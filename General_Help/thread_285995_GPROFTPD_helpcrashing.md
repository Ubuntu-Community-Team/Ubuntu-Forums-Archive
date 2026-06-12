---
title: "GPROFTPD help/crashing"
date: 2006-10-27
forum: General Help
---

### Post by malkaven on 2006-10-27
Hello all,  Im having issues w/ gproftpd.  I get an error when I enter "Sudo gproftpd"

> ** (gproftpd:8426): WARNING **: Couldn't find pixmap file: gproftpd.png

(gproftpd:8426): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Killed


However when I open the program w/o using sudo it runs fine.  I just cant modify anything because im not the root.  This error only happens when i try opening as root.  Any ideas?](*,)

---

### Post by malkaven on 2006-10-27
Just an update, I tried doing a clean reinstall and its still doing the same thing.

---

### Post by jbrickner on 2006-11-01
I am also experiencing the same problem.

---

### Post by bartek on 2006-11-02
Ditto here - precisely the same error.

Reinstalling / purging didn't solve it.

---

### Post by mrastas on 2006-11-06
Hi,

same error here also. 
Anyone found a solution yet?

I am running dapper, has somebody tested this in edgy?
And as i recall it stopped working after the latest proftpd update, about one month ago.

---

### Post by jbrickner on 2006-11-06
My GPROFTPD was running fine until I upgraded to EDGY.  No I get the error described above.  It also seemed to lockup my system.  The hard drive spins and spins and spins.  Not sure what is going on.  I have reloaded ProftpD and GProftpD with no luck.  ANy ideas... can't seem to find any solutions anywhere.

---

### Post by Kardelen on 2006-11-10
> **jbrickner said:**
> My GPROFTPD was running fine until I upgraded to EDGY.  No I get the error described above.  It also seemed to lockup my system.  The hard drive spins and spins and spins.  Not sure what is going on.  I have reloaded ProftpD and GProftpD with no luck.  ANy ideas... can't seem to find any solutions anywhere.

I have the same problem, moreover; I cannot install any packages now.. Here is the blah blah from terminal window:
```

sentinel@sentinel:~/easyubuntu$ sudo apt-get install fluxbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgsf-gnome-1-114
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  menu
Suggested packages:
  fluxconf fbpager fbdesk xfonts-artwiz
The following NEW packages will be installed:
  fluxbox menu
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1310kB of archives.
After unpacking 4575kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com edgy/universe menu 2.1.29 [389kB]
Get:2 http://archive.ubuntu.com edgy/universe fluxbox 0.9.15.1+1.0rc2-1 [922kB]
Fetched 1310kB in 3s (329kB/s)  
Selecting previously deselected package menu.
(Reading database ... 108438 files and directories currently installed.)
Unpacking menu (from .../archives/menu_2.1.29_i386.deb) ...
Selecting previously deselected package fluxbox.
Unpacking fluxbox (from .../fluxbox_0.9.15.1+1.0rc2-1_i386.deb) ...
Adding `diversion of /usr/bin/bsetroot to /usr/bin/bsetroot.blackbox by fluxbox'
Adding `diversion of /usr/share/man/man1/bsetroot.1.gz to /usr/share/man/man1/bsetroot.blackbox.1.gz by fluxbox'
Setting up proftpd (1.3.0-9) ...
Replacing config file /etc/proftpd/proftpd.conf with new version
 * Starting ftp server proftpd                                                                              - mod_dso/0.4: module 'mod_tls.c' already loaded
 - Fatal: LoadModule: error loading module 'mod_tls.c': File exists on line 16 of '/etc/proftpd/modules.conf'
                                                                                                    [fail]
invoke-rc.d: initscript proftpd, action "start" failed.
dpkg: error processing proftpd (--configure):
 subprocess post-installation script returned error exit status 1
Setting up menu (2.1.29) ...

Setting up fluxbox (0.9.15.1+1.0rc2-1) ...

Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Kardelen on 2006-11-10
I have uninstalled gproftpd and proftpd. This seems to have fixed package problems.

Does anyone know if there will be an update(or fix) soon?

---

### Post by jbrickner on 2006-11-13
I still get the error, but the gproftpd program now opens and works correctly.  My issue was that when I upgraded from Breezy to Edgy, it broke my swap file.  Everyone check your swap file.

---

### Post by Kardelen on 2006-11-16
I am new to linux so I must ask; how do I check swap file and fix it if it is broken?

---

### Post by ianni on 2006-11-27
> **malkaven said:**
> Hello all,  Im having issues w/ gproftpd.  I get an error when I enter "Sudo gproftpd"



However when I open the program w/o using sudo it runs fine.  I just cant modify anything because im not the root.  This error only happens when i try opening as root.  Any ideas?](*,)

hello man.for me also it was impossible to run gproftpd as a root.i just do this  sudo apt-get uprade gproftpd and then gksudo gproftpd and it s work

---

### Post by bartek on 2006-11-27
This does not work for me... I'm sure this has to do with the gproftpd.png file not being in the .deb itself - if whoever maintains it could possibly include it, that'd be good...

gproftpd crashes hard and I have to issue a killall to get back to normal...

---

### Post by superbeef on 2006-12-02
This program used to work for me, but now when I turn it on, it looks like this:

[IMG]http://pieinmyeye.cjb.net/images/groftpdbad.png[/IMG]

This happens when I open it through the desktop, type "sudo gproftpd" or just "gproftpd", and I also get the errors regarding the gproftpd.png file as well.

---

### Post by superbeef on 2006-12-04
I was able to run the server again by taking the configuration from the gproftpd, which I found in etc/proftpd.conf, and put that in etc/proftpd/proftpd.conf . Now I can run the server the way it was right before gproftpd stopped working, I just can't see it doing anything.

Hopefully that helps somebody else.

---

### Post by mrastas on 2006-12-05
I finaly made a bug report of this, and there seems to really be something weird with the package.

According to this it should be fixed in feisty gproftpd package.

[BUG report]("https://bugs.launchpad.net/distros/ubuntu/+source/gproftpd/+bug/74368")

Now how can i use this fix in dapper, or can i?

I allready tried manually moving the missing file, but that did not seem to work.

---

### Post by decoherence on 2006-12-14
> **mrastas said:**
> According to this it should be fixed in feisty gproftpd package.

[BUG report]("https://bugs.launchpad.net/distros/ubuntu/+source/gproftpd/+bug/74368")



Hi there! First of all, thanks for doing the bug report.

The fellow who was responding to you made it sound (unintentionally, I'm sure) that we should just wait for the Feisty package. I'm using Dapper because it's supposed to have "long term support."

Also, I'm not too familiar with LaunchPad, but the "Fix Released" in the status area is kind of offputting since those of us using the "Long Term Support" version don't have a fix.

Sorry if I just don't understand how launchpad works... are we expecting an update for dapper?

thanks again

---

### Post by mrastas on 2006-12-14
Well i am not exactly a pro either with launchpad or linux. But anyway that is what i am wondering too. 

Furthermore feisty is in development and edgy is the current, so atleast they should release the fix for edgy i think, but why not for dapper LTS also. Maybe there is some sort of checkup before ubuntu grew releases the fix to already finished versions like edgy and dapper. So still waiting...

---

### Post by sledhead45 on 2008-03-26
I'm still experiencing this issue. I'm running an up-to-date feisty system with proftpd 1.3.0 and gproftpd 8.2.8. I haven't used gproftpd in many months (maybe a year), but last I knew it worked. I'm getting the same exact error as the original post. Is there a simple fix for this? I'd really rather not reinstall proftpd since I have it configured exactly the way i want it. suggestions?

---

### Post by kackler on 2008-04-25
I snagged this from another post, but I was having the same problem today.

 Here is what I did.

$ hostname

remember (or better yet write down) whatever that returns

$ sudo gedit /etc/hosts

here you will see neart the top of the page:
127.0.0.1 localhost

Underneath that add this line:
127.0.0.1 <whatever hostname returned goes here>

Now save and exit and start proftpd. That should stop the error you were receiving (it did for me anyway).
Hope that helps and if there is a better solution or my solution causes any other problems please let me know.

Good Luck!

---

