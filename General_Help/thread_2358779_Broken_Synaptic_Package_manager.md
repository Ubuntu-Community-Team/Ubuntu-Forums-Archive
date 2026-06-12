---
title: "Broken Synaptic Package manager"
date: 2017-04-17
forum: General Help
---

### Post by zoe-scutterbug on 2017-04-17
Ooops I have broken my Synaptic package manager, when i press the icon, synaptic trys its best but it does not come up. Apt-get works fine.

From the output below I guess it is something to do with Bodhi desktop or Enlightenment, I was trying to find a desktop a bit like OpenGEU/Geubuntu which is what I used to run prior to a 7 year break on a mini mac. (I should say my attempts to install a workable Enlightenment/Bodhi Desktop failed)

```
$ gksudo synaptic
Traceback (most recent call last):
  File "/usr/bin/gksudo", line 5, in <module>
    import esudo.esudo as esudo
  File "/usr/lib/python2.7/dist-packages/esudo/esudo.py", line 14, in <module>
    from efl import ecore
  File "efl/ecore/efl.ecore.pyx", line 1, in init efl.ecore (efl/ecore/efl.ecore.c:39256)
ImportError: /usr/lib/python2.7/dist-packages/efl/eo.so: undefined symbol: eo_init
```


P.S. I am pretty much a eternal linux novice and I am guilty of, despite telling myself not to, added far too many repositories, desktops and packages...I am a package junky.

---

### Post by slickymaster on 2017-04-17
*Thread moved to **General Help**.*

---

### Post by vasa1 on 2017-04-17
> **zoe-scutterbug said:**
> ... I guess it is something to do with Bodhi desktop or Enlightenment, I was trying to find a desktop a bit like OpenGEU/Geubuntu which is what I used to run prior to a 7 year break on a mini mac. (I should say my attempts to install a workable Enlightenment/Bodhi Desktop failed)
...
Could you be a bit specific about what your distro actually is? And what is its version number?

Have you tried *sudo -H synaptic* instead?

---

### Post by zoe-scutterbug on 2017-04-17
*sudo -H synaptic* worked


Apologies ...I am on Ubuntu 16.04 LTS with a Cinnamon desktop, but I have added Ubuntu Studio, Mate and a couple of others too, apart from my failed attempt to get Bodhi.
* sudo -H synaptic worked* :)

however

```
/usr/bin/deborphan: The status file is in an improper state.
One or more packages are marked as half-installed, half-configured,
unpacked, triggers-awaited or triggers-pending. Exiting.
```

Its one broken package ..efl




```
dpkg: error processing archive /var/cache/apt/archives/efl_201701261.18.4bodhi1-1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/evas/filters/lua/color.lua', which is also in package libefl-data 1.19.0-0xenial3
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for libc-bin (2.23-0ubuntu7) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link

Errors were encountered while processing:
 /var/cache/apt/archives/efl_201701261.18.4bodhi1-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of terminology:
 terminology depends on efl; however:
  Package efl is not installed.

dpkg: error processing package terminology (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 terminology
```

Maybe i should just remove Bodhi?

Many thanks for your help, its very appreciated.
Zoe

---

### Post by vasa1 on 2017-04-17
What you should keep and what you should remove depends entirely upon you!

Having a variety of desktop environments on the same system *could* have consequences.

Please run
```
sudo apt-get update
```and then```
sudo apt-get upgrade
```and post the entire contents here. **Please use code tags for content you copy/paste from the terminal**!

---

### Post by zoe-scutterbug on 2017-04-17
Apologies for not using the code tags, just returning to linux.

```

zoe@zoe-ZBOX~$ sudo apt-get update
[sudo] password for zoe: 
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:2 http://ppa.launchpad.net/atareao/atareao/ubuntu xenial InRelease         
Hit:3 http://gb.archive.ubuntu.com/ubuntu xenial InRelease                     
Hit:4 http://ppa.launchpad.net/atareao/telegram/ubuntu xenial InRelease        
Ign:5 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:6 http://repo.steampowered.com/steam precise InRelease                     
Get:7 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Hit:8 http://ppa.launchpad.net/budgie-remix/ppa/ubuntu xenial InRelease        
Hit:9 http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu xenial InRelease     
Ign:10 http://dl.google.com/linux/earth/deb stable InRelease                   
Hit:11 http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial InRelease      
Hit:12 http://dl.google.com/linux/chrome/deb stable Release                    
Ign:13 http://repo.vivaldi.com/stable/deb stable InRelease                     
Hit:14 http://ppa.launchpad.net/gerardpuig/ppa/ubuntu xenial InRelease         
Hit:15 http://dl.google.com/linux/earth/deb stable Release                     
Hit:16 http://repo.vivaldi.com/stable/deb stable Release                       
Get:17 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB] 
Hit:18 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial InRelease        
Hit:19 http://ppa.launchpad.net/mati75/spacefm/ubuntu xenial InRelease         
Hit:20 http://ppa.launchpad.net/niko2040/e19/ubuntu xenial InRelease           
Hit:21 http://ppa.launchpad.net/noobslab/macbuntu/ubuntu xenial InRelease      
Hit:22 http://ppa.launchpad.net/noobslab/themes/ubuntu xenial InRelease        
Hit:23 http://ppa.launchpad.net/numix/ppa/ubuntu xenial InRelease              
Ign:24 http://packages.bodhilinux.com/bodhi xenial InRelease                   
Hit:25 http://ppa.launchpad.net/peterlevi/ppa/ubuntu xenial InRelease          
Hit:26 http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu xenial InRelease 
Hit:27 http://repository.spotify.com stable InRelease                          
Hit:28 http://ppa.launchpad.net/ross-kallisti/efl+e/ubuntu xenial InRelease    
Hit:29 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial InRelease
Hit:30 http://ppa.launchpad.net/stellarium/stellarium-releases/ubuntu xenial InRelease
Hit:31 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial InRelease    
Hit:32 http://packages.bodhilinux.com/bodhi xenial Release               
Hit:33 http://ppa.launchpad.net/thefanclub/ubuntu-after-install/ubuntu xenial InRelease
Hit:34 http://ppa.launchpad.net/webupd8team/atom/ubuntu xenial InRelease 
Hit:35 http://ppa.launchpad.net/webupd8team/brackets/ubuntu xenial InRelease
Hit:36 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease
Hit:37 http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu xenial InRelease
Ign:38 http://packages.bodhilinux.com/bodhi xenial Release.gpg
Get:39 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [54.2 kB]
Get:40 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [47.4 kB]
Get:41 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [32.2 kB]
Get:42 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [31.8 kB]
Get:44 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [288 kB]
Get:47 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [190 kB]
Get:48 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [160 kB]
Get:49 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [188 kB]
Get:50 http://gb.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,516 B]
Get:51 http://gb.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Hit:52 http://archive.canonical.com/ubuntu xenial InRelease                    
Hit:53 http://screenshots.getdeb.net wily-getdeb InRelease                     
Ign:54 https://dl.bintray.com/sbt/debian  InRelease
Get:55 https://dl.bintray.com/sbt/debian  Release [814 B]
Hit:55 https://dl.bintray.com/sbt/debian  Release
Fetched 1,304 kB in 5s (220 kB/s)
Reading package lists... Done
```

```

zoe@zoe-ZBOX:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

Yes I have grabbed to many repositories. I have removed the broken efl package as I did not know how to fix it.

(I have to be away from the keyboard for a couple of hours ...sorry for the delay in any replies)


Many thanks again for any help ...much appreciated.
Zoe

---

### Post by zoe-scutterbug on 2017-04-21
hi
 No biggie but is the anyway to restore synaptic so it works from an icon in the dock or menu, pref both.
Atm it only starts if I use the command [I]sudo -H synaptic

[/I]thanks in advance
Zoe

 (fyi I use Cairo and Gnome Pie)

---

### Post by vasa1 on 2017-04-21
> **zoe-scutterbug said:**
> hi
 No biggie but is the anyway to restore synaptic so it works from an icon in the dock or menu, pref both.
Atm it only starts if I use the command [I]sudo -H synaptic

[/I]thanks in advance
Zoe

 (fyi I use Cairo and Gnome Pie)In a terminal, try: ```
grep Exec= /usr/share/applications/*ynaptic*
```
and post the output here.

---

### Post by zoe-scutterbug on 2017-04-21
Thanks Vasa1..this is what appeared

```
zoe@zbox:~$ grep Exec= /usr/share/applications/*ynaptic*
Exec=synaptic-pkexec
zoe@zbox:~$ 

```

zoe

---

### Post by vasa1 on 2017-04-21
For me, I get```
grep Exec= /usr/share/applications/*ynaptic*
/usr/share/applications/synaptic.desktop:Exec=gksu synaptic

```
Notice the file name is provided. I don't know why your output doesn't have that.

So move to */usr/share/applications* and go through the desktop files to see how many synaptic.desktop files you have. At one time, I remember having two, one for GNOME and one for KDE.

If you have just the one, copy that file to your home folder as a backup and then run
[s]```
sudo -H gedit synaptic.deskop
```[/s]```
sudo -H gedit synaptic.desktop
```Be very careful at this stage since you'll be using elevated privileges.

Look for the line which has the Exec= line you found using the grep command.

Change it to this:
```
Exec=gksu synaptic
```Save the file and exit gedit. Close the terminal. Now try launching Synaptic from your launcher or by whatever other means you wish.

---

### Post by zoe-scutterbug on 2017-04-21
hi,

 I believe I followed the instructions (I always doubt myself).

 However after 
```
sudo -H gedit synaptic.deskop
```

I get a blank gedit page titled 'synaptic.desktop' /home/zoe

with no lines visible to edit.

---

### Post by howefield on 2017-04-21
> **zoe-scutterbug said:**
> I get a blank gedit page titled 'synaptic.desktop' /home/zoe

Try..

```
sudo -H gedit /usr/share/applications/synaptic.desktop
```

---

### Post by vasa1 on 2017-04-21
You have to be in /usr/share/applications. That's where the file is.

---

### Post by zoe-scutterbug on 2017-04-21
Lol  (apologies for being a dummy, which makes helping me tricky (I have no memory))  :)

Starting in the right place
```

zoe@zbox:/usr/share$ sudo -H gedit synaptic.deskop
[sudo] password for zoe: 
zoe@zbox:/usr/share$ sudo -H gedit /usr/share/applications/synaptic.deskop
zoe@zbox:/usr/share$ 
```

I still got a blank gedit page.

Zoe
Apologies if this is like extracting teeth

---

### Post by vasa1 on 2017-04-21
You have to be in /usr/share/**applications**. That's where the file is.

---

### Post by howefield on 2017-04-21
You simply made a typo... it is synaptic.desktop not synaptic.deskop

---

### Post by zoe-scutterbug on 2017-04-21
OK I am doubly embarrassed ... not spotting a spelling mistake and twice being in the wrong place.... LOL please forgive me:)

I got a proper gedit page up.
I changed the line.

```

[Desktop Entry]
Name=Synaptic Package Manager
GenericName=Package Manager
Comment=Install, remove and upgrade software packages
Exec=gksu synaptic
Icon=synaptic
Terminal=false
Type=Application
Categories=PackageManager;GTK;System;Settings;
X-Ubuntu-Gettext-Domain=synaptic
```

closed everything..tried the icon ...sadly nothing...rebooted...sadly nothing

---

### Post by howefield on 2017-04-21
> **zoe-scutterbug said:**
> OK I am doubly embarrassed ... not spotting a spelling mistake and twice being in the wrong place.... LOL please forgive me:)

Looking back in thread the typo wasn't made by you in the first place so don't worry about it :)

Tab autocomplete is worth getting used to, typing a few letters then pressing the tab key will complete the name for you, eg

typing

```
sudo -H gedit /u
```

then pressing the tab key will complete to..

```
sudo -H gedit /usr/
```

you can continue typing through the path, typing a few letters and hitting the tab key.. 'til you get to the file name, instead of typing synaptic.desktop just type syn and press the tab key.

There is a small detail to remember and that is it won't autocomplete if there is more than one possibility, eg in the above example it will likely stick on /usr/share/application and seemingly miss the "s" on the end.. press tab once more and you see the possibilities are

```
application-registry/  applications/ 
```

so you simply type the "s"

Hope that makes sense, it is more intuitive with a little practice than I made it look.

Back to your problem, I would suggest that there was nothing wrong with the .desktop file and I'd revert the change back to the original.

Can you confirm the desktop that you are trying to create the desktop launcher for ?

```
echo $XDG_CURRENT_DESKTOP
```
```
cat /etc/*-release
```

---

### Post by zoe-scutterbug on 2017-04-21
reverted as you suggested

```
zoe@zbox:/usr/share/applications$ echo $XDG_CURRENT_DESKTOP
X-Cinnamon
zoe@zbox:/usr/share/applications$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"
NAME="Ubuntu"
VERSION="16.04.2 LTS (Xenial Xerus)"

```


Not sure if this matters ...I don't use the cinnamon menu but Cairo (and Gnome-Pie)

---

### Post by howefield on 2017-04-21
Try loading Synaptic with the 

```
sudo -H synaptic
```

command that worked for you, synaptic should open and place an icon on the Cairo dock. Right click on the cairo Synaptic icon and select Synaptic Package Manager > Make it a Launcher.

[ATTACH=CONFIG]274696[/ATTACH]

---

### Post by zoe-scutterbug on 2017-04-21
I too tired tonight. But to be honest I do not know how to make a launcher to work, whether its for Cairo, cinnamon or Ubuntu. So I will try google it successfully tomorrow. The current icon in the dock and menu entry dont work.

Much appreciation for your help so far

Zoe

when I click on my Synaptic icon I don't get the option in the pop up to make it a launcher, but i can edit it.

---

### Post by howefield on 2017-04-21
> **zoe-scutterbug said:**
> I too tired tonight. But to be honest I do not know how to make a launcher to work, whether its for Cairo, cinnamon or Ubuntu. So I will try google it successfully tomorrow. The current icon in the dock and menu entry dont work.

Much appreciation for your help so far

Zoe

You're very welcome, try again tomorrow and remove any current synaptic icons in the Cairo dock then try to add again as I mentioned in post #20.

---

### Post by vasa1 on 2017-04-21
> **howefield said:**
> Looking back in thread the typo wasn't made by you in the first place so don't worry about it :)*Mea culpa* :(
> **howefield said:**
> 
...
Back to your problem, I would suggest that there was nothing wrong with the .desktop file and I'd revert the change back to the original.
...
I'm on the Openbox session of Lubuntu 16.04. I don't have any session manager running.

I've purged SPM, apt cleaned my /var/cache/apt/archives and reinstalled SPM.

If I double-click on the SPM icon in /usr/share/applications, nothing visible happens.
The Exec= line is synaptic-pkexec.
I run synaptic-pkexec in a terminal and see this:```
09:10 AM ~ $ synaptic-pkexec
==== AUTHENTICATING FOR com.ubuntu.pkexec.synaptic ===
Authentication is required to run the Synaptic Package Manager
Authenticating as: vasa1,,, (vasa1)
Password: 
polkit-agent-helper-1: error response to PolicyKit daemon: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: No session for cookie
==== AUTHENTICATION FAILED ===
Error executing command as another user: Not authorized

This incident has been reported.
09:10 AM ~ $ 

```But ```
gksu synaptic
``` works fine.

I don't know if gksu is installed by default across flavors. I think it and SPM are included in Lubuntu 16.04 by default. Could that explain why gksu doesn't work for zoe.

Another point, since SPM isn't a default package in Ubuntu, the Unity flavor, I'm guessing that the appropriate policy/configuration files for SPM will need to be written before synaptic-pkexec will work.

---

### Post by vasa1 on 2017-04-21
Some links that maybe relevant:
[https://ubuntuforums.org/showthread.php?t=2272231](https://ubuntuforums.org/showthread.php?t=2272231)
[https://askubuntu.com/questions/162011/pkexec-wont-launch-polkit-gui-in-lubuntu-lxde](https://askubuntu.com/questions/162011/pkexec-wont-launch-polkit-gui-in-lubuntu-lxde)

---

### Post by zoe-scutterbug on 2017-04-22
Hi

After using *sudo -H synaptic* to raise synaptic, I made the icon in the taskbar a launcher as in post 20 & 22
 but it fails to launch Synaptic with either* Exec=synaptic-pkexec* or *Exec=gksu synaptic  *versions of the file[I].

[/I]A silly error*[I]Exec=*[/I]*[I][I][I]Exec=*[/I]gksu synaptic[/I][/I] launched synaptic without root privileges

---

### Post by vasa1 on 2017-04-22
Do you have gksu installed? What does```
apt policy gksu
```show?

---

### Post by zoe-scutterbug on 2017-04-22
```
zoe@zbox:~$ apt policy gksu
gksu:
  Installed: 2.0.2-9ubuntu1
  Candidate: 2.0.2-9ubuntu1
  Version table:
 *** 2.0.2-9ubuntu1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by zoe-scutterbug on 2017-04-22
(I should say synaptic did work until I made several attempts to install the Bodhi desktop (8 years ago when I was on Linux last,  i ran OpenGeu/Geubuntu and I was trying to find something similar) but I failed because Efl had issues.)

---

### Post by zoe-scutterbug on 2017-04-22
Is the a solution in post 24? my brain is very teeny tiny this morning

---

### Post by vasa1 on 2017-04-22
I'm just speculating here, but it maybe that running Cinnamon may not allow for pkexec to work.

---

### Post by zoe-scutterbug on 2017-04-22
Reasonable to speculate :)

I tried launching synaptic under Ubuntu, Xfce, Budgie and Mate desktops all equally were unable to raise Synaptic. Ubuntu Studio (which failed too) seemed to look exactly like Xfce.

When ever I boot up. The is a pop up saying my system has a problem, would I like to report it. I am not sure what that problem is.

zoe

---

### Post by vasa1 on 2017-04-22
> **zoe-scutterbug said:**
> ...
When ever I boot up. The is a pop up saying my system has a problem, would I like to report it. I am not sure what that problem is.

zoe
The plot thickens! Some recent information maybe in /var/log/apport.log and in /var/log/apport.log.1. You could also poke around in /var/crash.

If you really need to use this computer, why don't you back up your data and do a clean install of the distro you like (and then try not to install sundry desktop environments that may complicate your life)?

---

### Post by zoe-scutterbug on 2017-04-22
In /var/log/apport.log

```
ERROR: apport (pid 11069) Sat Apr 22 11:24:30 2017: another apport instance is already running, aborting
ERROR: apport (pid 11053) Sat Apr 22 11:24:30 2017: another apport instance is already running, aborting
ERROR: apport (pid 11083) Sat Apr 22 11:24:31 2017: another apport instance is already running, aborting
ERROR: apport (pid 11068) Sat Apr 22 11:24:30 2017: called for pid 10862, signal 11, core limit 0
ERROR: apport (pid 11068) Sat Apr 22 11:24:30 2017: script: /usr/share/apport/apport-gtk, interpreted by /usr/bin/python3.5 (command line "/usr/bin/python3 /usr/share/apport/apport-gtk")
ERROR: apport (pid 11068) Sat Apr 22 11:24:30 2017: gdbus call error: Error connecting: Could not connect: Connection refused

ERROR: apport (pid 11068) Sat Apr 22 11:24:30 2017: debug: session gdbus call: 
ERROR: apport (pid 11068) Sat Apr 22 11:24:34 2017: wrote report /var/crash/_usr_share_apport_apport-gtk.1000.crash
```

 /var/log/apport.log.1 there is

```


the are 20 files in 
ERROR: apport (pid 21380) Wed Apr 19 16:20:27 2017: called for pid 21326, signal 6, core limit 0
ERROR: apport (pid 21380) Wed Apr 19 16:20:27 2017: executable: /usr/bin/webbrowser-app (command line "webbrowser-app")
ERROR: apport (pid 21380) Wed Apr 19 16:20:27 2017: debug: session gdbus call: (true,)

ERROR: apport (pid 21380) Wed Apr 19 16:20:43 2017: wrote report /var/crash/_usr_bin_webbrowser-app.1000.crash
```

 in /var/crash the are 20 files ... (the first nine are to do with Bodhi and efl, then a couple re the update manager, last three with cinnamon settings.)

I am very grateful for the kind and patient help you have given me. Its kinda part of why Linux is so good.

I think I might just have to give up trying to fix synaptic. Atm my computer works quite well without it. I always make the same mistake of setting out not to add stuff, but always end up breaking that rule. Plus I dont trust myself with a clean install. With synaptic working only via the terminal, that might slow me down. I can carry on using my computer, warts and all, as it is.

---

### Post by vasa1 on 2017-04-22
> **zoe-scutterbug said:**
> ... With synaptic working only via the terminal, that might slow me down. I can carry on using my computer, warts and all, as it is.
How often do you need synaptic in a day? What for?

---

### Post by zoe-scutterbug on 2017-04-22
Now my system is set up, very rarely. Not daily.... I can update and upgrade via the terminal etc

---

### Post by zoe-scutterbug on 2017-05-14
I fixed this issue by reinstalling the Policykit

---

