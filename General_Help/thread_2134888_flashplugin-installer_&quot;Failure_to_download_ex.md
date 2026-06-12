---
title: "flashplugin-installer &quot;Failure to download extra data files&quot;"
date: 2013-04-12
forum: General Help
---

### Post by Ol'manScratch on 2013-04-12
I did an auto-update last night that it said came with a Flash player in the 26 item content. This morning shortly after I logged into Firefox and started viewing a slideshow this notice popped up:

"Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

flashplugin-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection."

I've never seen this notice at any other Flash upgrade, so I'd like to know a: what it is, and b: should I follow the instructions?
I'm using Firefox 20.0 Mozilla Firefox for Ububtu cannonical running under  Ubuntu 12.04

If this was supposed to be posted in a different forum, please excuse the error.
Thanks

---

### Post by Impavidus on 2013-04-12
Flashplugin-installer doesn't contain the flash player itself, but downloads it on installation. It seems that, when installing the packages, your computer was unable to reach the server from where it wants to download the plugin. If your system wants to try again later, just let it do so.

---

### Post by ankita indeed on 2013-04-13
This exact problem is repeatedly happening to my system as well.I am using ubuntu 12.04 and I am unable to watch videos on youtube because the youtube site says I need to upgrade my flash player version.In the updaate information dialog box which says failure to download extra data files, after I let the system run the action the terminal window popsup and after asking authentication displays this message in the terminal

flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.280.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.280.orig.tar.gz)

then the terminal closes on its own and the problem continues to reccur

---

### Post by Impavidus on 2013-04-13
Have you tried pinging the server? The server may be down. It works for me (updated the flash player two days ago), but based on my location I may be redirected to a different IP.

In the meantime, many youtube videos don't need flash anymore. If you disable flash many will still play.

---

### Post by jyris on 2013-05-23
Are behind a proxy by any change? If you are the command bellow should succesfully install flashplugin for you:

sudo http_proxy=http://<proxy-server-name>:<proxy-port> apt-get --reinstall install flashplugin-installer

However, even after a succesful install the "Failure to download extra data files"-error keeps coming once per day and I have no idea how to stop that. 

Does anybody have any idea how to tell update-manager that the package has already been succesfully installed and it can stop bugging the user? I am considering of disabling the whole update-manager for this.

---

### Post by jyris on 2013-05-23
Commenting my self :)... the error can be stopped by:
sudo rm -f /var/lib/update-notifier/package-data-downloads/flashplugin-installer.failed

---

### Post by arch0njw on 2014-03-17
OMG, I'm really hoping this works for me.  I ended up setting up a second account that can connect without the proxy, and then I install flashplugin-installer with a connection that does not require me to use a proxy.
1) What a pain.
2) Why can't the installer get fixed?

---

### Post by arch0njw on 2014-03-19
Rats.  That didn't do it for me.  :(

[http://ubuntuforums.org/showthread.php?t=2211669](http://ubuntuforums.org/showthread.php?t=2211669)

---

### Post by wgarcia on 2014-03-19
I intervened in an error report ([https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/1037662](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/1037662)) which hasn't been closed yet, but somebody (don't remember who) told me that actually flashplugin-installer is not needed any more. So one can safely:

sudo apt-get remove flashplugin-installer

sudo apt-get install adobe-flashplugin

from a terminal. I did this some months ago and never had a problem with this again. In the error report some say that it is still needed, but as I said, I never got bothered by this since I issued the above-mentioned commands.

---

### Post by arch0njw on 2014-03-19
Well, hey... I'll give that a try and see what happens!  Thanks!!

---

### Post by sukup-jaroslav on 2014-03-21
I had also this problem. 
I fixed it by manual install using that annoying dialog. But I had to setup proxy in the ubuntu system and applying it in the whole system. 
Apt-get install worked for me, because I had manual proxy setup only for apt (in /etc/apt/), but this proxy setup didnt work for specific install of flashplugin-installer.
Thanx [COLOR=#DD4814][COLOR=#000000][jyris]("http://ubuntuforums.org/member.php?u=1821691") [SIZE=2]for idea.[/SIZE][/COLOR][/COLOR]

---

### Post by Pablo_Halpern on 2014-05-06
> **wgarcia said:**
> I intervened in an error report ([https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/1037662](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/1037662)) which hasn't been closed yet, but somebody (don't remember who) told me that actually flashplugin-installer is not needed any more. So one can safely:

sudo apt-get remove flashplugin-installer

sudo apt-get install adobe-flashplugin

from a terminal. I did this some months ago and never had a problem with this again. In the error report some say that it is still needed, but as I said, I never got bothered by this since I issued the above-mentioned commands.

Didn't work for me:

```
~ $ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'adobe-flashplugin' has no installation candidate
~ $ 

```

---

### Post by Impavidus on 2014-05-06
For adobe-flashplugin you have to enable the partner repositories.

---

### Post by juanch02 on 2015-03-27
Worked like a charm, thanks for [**[COLOR=#000000]jyris[/COLOR]**]("http://ubuntuforums.org/member.php?u=1821691") tips when behind a proxy; ;) (this is usefull even when proxy has been set via network manager)

---

