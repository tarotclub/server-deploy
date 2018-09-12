# server-deploy
Deploy TarotClub server easily


# Ubuntu server setup

(Ubuntu 18.04)

## Install packages

```
apt-get install nginx git build-essential curl nodejs npm qt5base qt5-qmake
```

## Install CouchDb


Compile and install CouchDb 2.x from the official package.

```
echo "deb https://apache.bintray.com/couchdb-deb bionic main" | tee -a /etc/apt/sources.list
curl -L https://couchdb.apache.org/repo/bintray-pubkey.asc | apt-key add -
apt install couchdb
```


## Install Node.js dependencies

Run 'npm install' at the directory root /opt/www/tarotclub/tarotclub/www

## Run Web app as a systemd service

Copy 'server-deploy/tarotclubweb.service' (as root) to /etc/systemd/system/tarotclubweb.service

```
Enable it: # systemctl enable tarotclubweb
Start it: # systemctl start tarotclubweb
See status: # systemctl status tarotclubweb
See logs: # journalctl -u tarotclubweb
```

Try killing the node process by its pid and see if it starts back up!

## SSL configuration

Copy past the following additionnal intermediate certificates at the send of your .cert file:

https://www.gandi.net/static/CAs/GandiStandardSSLCA2.pem

Then configure Nginx SSl parameters accordingly.

## Password configuration

Create a text file containg the mail server password: /opt/mailpassword.txt.

Create a text file containg the couchdb admin password: /opt/couchdbpassword.txt.

# Configure IRC bots

wget ftp://ftp.eggheads.org/pub/eggdrop/source/1.6/eggdrop1.6.18.tar.gz

Code:
tar zxvf eggdrop1.6.18.tar.gz 
cd eggdrop1.6.18 
./configure 
make config 
make 
make install DEST=~/location_to_run_eggdrop_from

Utiliser le fichier de configuration simple.conf.

# Configure Web site

FIXME

# Configure Game server

FIXME
