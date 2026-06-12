---
title: "Big Flash Problem"
date: 2008-04-21
forum: General Help
---

### Post by MosMusy on 2008-04-21
I installed the flash package from Synaptic Package manager and everything went smoothly. Then when I go to a website that has flash it says install missing plugin. Then when I press on install it says that I have it already and I need to restart Firefox. So I do that but it still says missing plugin.

---

### Post by ryanhaigh on 2008-04-21
You could try marking the package for re-installation in synaptic, ensuring that firefox is closed at the time.

---

### Post by banished_one on 2008-04-21
well first of all do a manual check, run this in your terminal

locate libflashplayer.so

---

### Post by MosMusy on 2008-04-21
I re-installed it with firefox closed and restarted firefox several times, but it still didn't work.

When I typed that into the terminal it just returned a blank line.

---

### Post by cdenley on 2008-04-21
Post the output for this command
```

sudo dpkg -l flashplugin-nonfree

```
Are you using 32-bit or 64-bit? Firefox 2 or 3? When you enter
```
about:plugins
```
in the url bar, does it list the flash plugin? Are you sure you close all instances of firefox when restarting it (including the little window with your downloads)? Did you try restarting your computer for good measure?

---

### Post by MosMusy on 2008-04-21
it says "type password:" at the terminal, but I can't type it!!!!!!!

---

### Post by cdenley on 2008-04-21
It won't print your password in the terminal, or any replacement characters such as *. Just type your password then press enter.

I think you can use this command, too, without entering your password for root privileges.
```

dpkg -l flashplugin-nonfree

```

---

### Post by MosMusy on 2008-04-21
> **cdenley said:**
> Post the output for this command
```

sudo dpkg -l flashplugin-nonfree

```
Are you using 32-bit or 64-bit? Firefox 2 or 3? When you enter
```
about:plugins
```
in the url bar, does it list the flash plugin? Are you sure you close all instances of firefox when restarting it (including the little window with your downloads)? Did you try restarting your computer for good measure?

It gives me this:
movses@movses-laptop:~$ sudo dpkg -l flashplugin-nonfree
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rc  flashplugin-no 9.0.48.0.2+rea Adobe Flash Player plugin installer

I'm sure I close all firefox windows, and yes I restarted, and the terminal does not recognize the line "about:plugins" so I don't know if I have 32-bit or 64-bit. I have firefox 2.

---

### Post by MosMusy on 2008-04-21
WHY CAN'T I INSTALL FLASH? IS IT THAT DIFFICULT? PLEASE SOME ONE TELL ME I HAVE BEEN WASTING HOURS TRYING MANY WAYS TO INSTALL THE STUPID PLUGIN. I AM REALLY QUESTIONING SWITCHING TO UBUNTU BECAUSE WITH WINDOWS IT JUST TAKES 2 MINUTES WHILE ON UBUNTU I HAVE BEEN WASTING HOURS:cry: WITH TRYING TO INSTALL A PLUGIN! PLEASE SOME ONE TELL ME HOW TO INSTALL IT!!!!!!!![-o<

---

### Post by kbless7 on 2008-04-21
What website is this that doesn't allow you to view the flash?

---

### Post by cdenley on 2008-04-21
What version of ubuntu are you running? The output you posted shows the flash plugin is not currently installed. I don't think flash 9.0.48 will install correctly since adobe replaced it on their server with the current version (9.0.124).

Assuming you are using gutsy:
-Open System>Administration>Synaptic Package Manager
-Settings>Repositories
-Select "Updates" tab
-Make sure "Recommended updates" is checked
-Click close
-Click "Reload" in the top left
-install flashplugin-nonfree (should now be 9.0.124)

---

### Post by cdenley on 2008-04-21
> 
I AM REALLY QUESTIONING SWITCHING TO UBUNTU BECAUSE WITH WINDOWS IT JUST TAKES 2 MINUTES WHILE ON UBUNTU I HAVE BEEN WASTING HOURS

Non-free software is annoying. Ubuntu isn't allowed to include the plugin in the repository, so they had to make a package which retrieves the plugin from adobe when installed. However, when adobe decides to replace the plugin with a newer version, the package breaks.

---

### Post by MosMusy on 2008-04-21
> **cdenley said:**
> What version of ubuntu are you running? The output you posted shows the flash plugin is not currently installed. I don't think flash 9.0.48 will install correctly since adobe replaced it on their server with the current version (9.0.124).

Assuming you are using gutsy:
-Open System>Administration>Synaptic Package Manager
-Settings>Repositories
-Select "Updates" tab
-Make sure "Recommended updates" is checked
-Click close
-Click "Reload" in the top left
-install flashplugin-nonfree (should now be 9.0.124)

no, I downloaded the most current version of flash

---

### Post by cdenley on 2008-04-21
> 
no, I downloaded the most current version of flash


Downloaded from where? If you are downloading it from the adobe website, then their installer probably isn't installing it to the right place. The preferred way to install anything in ubuntu is to use the package manager so it can be removed or upgraded easily. It also ensures compatibility and security. I can't help you with adobe's flash installer. If you want help installing it the correct way, post the output from these commands.

```
cat /etc/lsb-release
uname -rm
```

---

### Post by banished_one on 2008-04-21
dont get frustrated so quickly its taking this long because as i understand this is your first time using the terminal, once you get a hang of it everything will be much easier.

ill give an alternative way in case the others fail

go to [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) select tar.gz and dowload (tar.gz is something like rar or zip)

when the download is complete extract it by right click extract here. When you look inside the extracted folder there will be two files one of them is libflashplayer.so which is the flash plugin and the other file is the installer named flashplayer-installer (this just copies the .so file to the mozilla plugin folder, you can do it manually if you need to). double click this installer and select run i terminal, follow the instructions of the installer and you should be fine.

---

