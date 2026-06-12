---
title: "installing programs"
date: 2006-07-02
forum: General Help
---

### Post by jiaz1 on 2006-07-02
i'm want to install:

1) openoffice 2.0.3
2) azureus betas
3) bon echo 
4) vlc .8.5

but i don't know how to do so via text commands.

i wouldn't mind learning. does any know of a good tutorial site?

OR

are there any reliable repositories.
i have subscribed to a unviversal repository but still can't find even openoffice 2.0.3 or vlc .8.5--only find OO 2.0.2 and vlc .8.4

---

### Post by aysiu on 2006-07-02
Generally, if you want the absolute latest versions of software, you're going to have to learn to compile from source (yes, that requires text commands).

Ubuntu--at release time--freezes package versions except for security updates. Six months later, you get whatever's the latest at that time. Six months still later, you'll get whatever's latest at *that* time.

In other words, Dapper has whatever was the latest version as of the end of May. Edgy will have whatever's the latest version as of October. Whatever's after Edgy will have the latest version as of April.

I don't know about the other stuff, but this script will install Bon Echo for you if you aren't using AMD64 or PowerPC Ubuntu.

Open your favorite text editor. Paste in this code: ```
#!/bin/bash
echo "Updating repositories list
"
sudo apt-get update
echo "
Making sure libstdc++5 and the old Firefox are installed
"
sudo apt-get -y install firefox libstdc++5
echo "
Backing up old Firefox preferences
"
cp -R ~/.mozilla ~/.mozilla_backup
echo "
Changing to home directory
"
cd
echo "
Downloading Firefox from the Mozilla site
"
wget -c ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/bonecho/alpha3/linux-i686/en-US/bonecho-alpha3.tar.gz
echo "
Unzipping the .tar.gz file
"
sudo tar -C /opt -x -z -v -f bonecho-alpha3.tar.gz
echo "
Removing the unzipped .tar.gz
"
rm bonecho-alpha3.tar.gz
echo "
Linking plugins
"
cd /opt/firefox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
echo "
Linking launcher to new Firefox
"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
echo "
The new Firefox is installed."
``` Save it as *bonecho.sh*
```
chmod +x bonecho.sh
./bonecho.sh
``` I'm just curious--what features are there in OpenOffice 2.0.3 that aren't in 2.0.2? Are these features really important to you?

---

