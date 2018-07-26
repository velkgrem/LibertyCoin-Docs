# LibertyCoin-Docs
## Service Node Install
### 1. Get a VPS server from a provider like DigitalOcean, Vultr, Amazon AWS, Linode, etc…

### 2. Enable the communication ports for Liberty

```
ufw allow 41412/tcp
ufw status
```

### 3. Install the Liberty CLI wallet. Always download the latest release available
Download and install the Liberty Coin wallet files using the following command:

```
curl https://s3.amazonaws.com/liberty-builds/4.0.4.1/v4.0.4.1-linux-x64.tar.gz | tar xvz
```

### 4. Cleanup the install, removing the QT Wallet
Next we're going to remove the qt-wallet, which we don't need it in order to run a servicenode.

`rm liberty-qt`

### 5. Configure the Masternode

`mkdir -p ~/.libertycore`

`cd ~/.libertycore`

`nano liberty.conf`

```
rpcuser=abunchofrandomtext
rpcpassword=morerandomstuff.justlettersandnumbers
rpcallowip=127.0.0.1
servicenode=1
servicenodeaddr=YOUR_PUBLIC_IP:41412
servicenodeprivkey=YOUR_SERVICENODE_PRIVATE_KEY
```
when done press `ctrl+o` then enter to confirm that the file name is **liberty.conf** then `ctrl+x` to exit that mode.

### 6. Startting the Masternode

`cd`

`./libertyd -daemon`

Make sure you are in the same directory as **libertyd**

`crontab -e`

Down arrow to the first empty line where there are no # marks.

`@reboot /root/libertyd`

This will start the daemon when your VPS reboots. Then do the whole `ctrl+o` `enter` `ctrl+x` sequence.
