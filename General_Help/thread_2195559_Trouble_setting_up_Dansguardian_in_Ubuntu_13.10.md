---
title: "Trouble setting up Dansguardian in Ubuntu 13.10"
date: 2013-12-24
forum: General Help
---

### Post by jhilp on 2013-12-24
I'm having issues setting up Dansguardian on my computer with Ubuntu 13.10. I'm trying to follow the steps in the Ubuntu Community Documentation for Dansguardian: [https://help.ubuntu.com/community/DansGuardian](https://help.ubuntu.com/community/DansGuardian)


I installed the programs it specified via terminal command with no errors. Then I downloaded the blacklists from [http://urlblacklist.com/?sec=download](http://urlblacklist.com/?sec=download) and extracted the files. 


The next step is to run: tar -xzf bigblacklist.tar.gz


I tried running that command, but get this response:


john-hill@johnhill-desktop:~$ tar -xzf bigblacklist.tar.gz
tar (child): bigblacklist.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
john-hill@johnhill-desktop:~$ 


Any ideas? Or is there a better way to set up the blacklists? Any help is appreciated.

---

### Post by bashiergui on 2013-12-25
You have to be in the folder the tar ball is in. If it's in the download folder then do
```
cd ~/Downloads
``` then run your command.

A helpful trick to know whether you're in the right directory is to type the first few letters of the file you're looking for then press tab a few times. If you see the name of the file you're looking for appear then you're in the right directory.

---

### Post by jaimerosario on 2013-12-27
```

cd /etc/dansguardian/lists
wget -c -q -Y on "http://urlblacklist.com/cgi-bin/commercialdownload.pl?type=download&file=bigblacklist" -O blacklists.tgz
tar xfz blacklists.tgz
find /etc/dansguardian/lists/blacklists -name "domains" -execdir cp {} {}.processed \;
find /etc/dansguardian/lists/blacklists -name "urls" -execdir cp {} {}.processed \;
chown -R root:root /etc/dansguardian/lists/blacklists
#
/etc/init.d/dansguardian stop && /etc/init.d/dansguardian start &> /dev/null

```

Part of a script I have to install and configure Dansguardian. You can try it.

---

### Post by bashiergui on 2013-12-27
In the script above you would be in /etc/dansguardian/lists 
However in your first post you are in your home directory.
I can't tell what went wrong with what you've posted.

---

