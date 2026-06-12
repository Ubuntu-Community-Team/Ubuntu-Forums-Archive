---
title: "Neutrino or Gnomad2 Working?"
date: 2004-10-30
forum: General Help
---

### Post by natefish on 2004-10-30
Has anyone successfully installed Neutrino or Gnomad2 and been able to use with Dell Jukebox or other Nomad/Zen MP3 Player?

I have been able to install both successfully yet neither is able to find my Dell Jukebox. The system recognizes the Jukebox on start up and it exists unders devices, yet neither software program seems to find it. 

Anyone have some insight? Maybe a tutorial on what they did to get things working?

---

### Post by natefish on 2004-11-07
So a little more information in case anyone has experience with this. It seems that I am able to work with Gnomad if I launch it as root from the terminal. So it seems that it is a permissions error thing. 

The Dell Jukebox is shown under devices. 

Does anyone have any insight into where the permissions could be adjusted so I can run Gnomad as a normal user? 

I tried editing the etc/hotplug/usb/  usermap file but it didn't seem to help.. the file is below...

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

#!/bin/sh
# Lifts a plugged in nomad jukebox to user space and
# optionally runs a client program.
# Written by Linus Walleij 2004, based on the "usbcam"
# script by Nalin Dahyabhai.
DEVICEOWNER=CONSOLE
DEVICEPERMS=666
PROGRAM="cd ~; gnomad2 --display=localhost:0"

# Special quirk for SuSE systems using "resmgr"
# (see [http://rechner.lst.de/~okir/resmgr/](http://rechner.lst.de/~okir/resmgr/))
if [ -f /sbin/resmgr ]
then
    /sbin/resmgr "${ACTION}" "${DEVICE}" desktop usb
    exit 0
fi

# This is for most other distributions
if [ "${ACTION}" = "add" ] && [ -f "${DEVICE}" ]
then
    # New code, using lock files instead of copying /dev/console permissions
    # This also works with non-gdm logins (e.g. on a virtual terminal)
    # Idea and code from Nalin Dahyabhai <nalin@redhat.com>
    if [ "x$DEVICEOWNER" = "xCONSOLE" ]
    then
	if [ -f /var/run/console.lock ]
	then
	    DEVICEOWNER=`cat /var/run/console.lock`
	elif [ -f /var/lock/console.lock ]
	then
	    DEVICEOWNER=`cat /var/lock/console.lock`
	else
	    DEVICEOWNER=
	fi
    fi
    if [ -n "$DEVICEOWNER" ]
    then
        chmod 666 "${DEVICE}"
        chown "${DEVICEOWNER}" "${DEVICE}"
        chmod "${DEVICEPERMS}" "${DEVICE}"
	# Then run an optional program - this does not work yet.
	# su "${CONSOLEOWNER}" -c "${PROGRAM}"
    fi
fi

---

### Post by natefish on 2004-11-10
I was able to get this running by changing the file to the following...
#!/bin/sh 
chmod 666 "${DEVICE}"

---

### Post by wayover13 on 2004-11-24
Thanks for this info.  I, too, am trying to get gnomad2 so I can access my Jukebox from Linux.  Though it will be helpful to know that I'll need to chmod the binary--chowning it is another alternative I suppose--what I'd really like to know is how you installed gnomad2?  Did you compile from source, or maybe apt-get it?  I see it's in the Debian repositories, so I know I could get it that way.  But I'm concerned I might break something in Gnome by using a foreign repository like that  Searched for gnomad at [www.apt-get.org](www.apt-get.org) but didn't find any repositores there--not surprising since it's in the main repositories.  Further info on how you installed this will be appreciated.

James

---

### Post by wayover13 on 2004-11-24
Ok, I've read this more carefully and I see you're not chmod'ing a binary.  The chmod is done by a script, and involves a device rather than a binary.  Clear enough.  But what's not clear is the script: did you insert this in the /etc/hotplug/usb/usermap file you show here?  If so, where?  Your description could be read as saying that you replaced this file with the little two-line bash script you give, but I doubt that's what you mean.  So, did you put ```

#!/bin/sh
chmod 666 "${DEVICE}"
```
where previously there was only ```
 chmod 666 "${DEVICE}"
``` in the file whose contents you've posted?
So that the stanza ```

 if [ -n "$DEVICEOWNER" ]
then
chmod 666 "${DEVICE}"
chown "${DEVICEOWNER}" "${DEVICE}"
chmod "${DEVICEPERMS}" "${DEVICE}"
# Then run an optional program - this does not work yet.
# su "${CONSOLEOWNER}" -c "${PROGRAM}"
fi
fi
```
reads ```

 if [ -n "$DEVICEOWNER" ]
then
#!/bin/sh
chmod 666 "${DEVICE}"
chown "${DEVICEOWNER}" "${DEVICE}"
chmod "${DEVICEPERMS}" "${DEVICE}"
# Then run an optional program - this does not work yet.
# su "${CONSOLEOWNER}" -c "${PROGRAM}"
fi
fi
```
instead?  In other words, you only inserted the line ```
#!/bin/sh
``` into that file?  clarification is needed.

Btw, I did not resolve installing this on Ubuntu yet.  I'd still like to know how you did it.  I.e., whether by adding a non-Ubuntu repository and apt-get(ting) it or by compiling it yourself?  I don't want to go breaking my system or anything.

Further input appreciated.

James

---

### Post by inha on 2004-11-29
Why exactly are there no packages for gnomad in the repositories?

---

### Post by randy on 2004-11-30
In order to get my Nomad  Zen Extra working I had to compile both libnjb and gnomad2 from source.  I also had to change some permissions somewhere, I can't remember exactly where though.  (I did it two days after the first pre release).

---

### Post by wayover13 on 2004-12-20
I got this working, and it is really pretty simple. First. note that gnomad2 is in the Debian repositories.  So there's already a Debian-packaged, Ubuntu-compatible package for gnomad2.  The main problem here is that the Ubuntu people, for whatever reason, decided not to include this package in the Ubuntu repository--only they could tell you why.

There are really only three steps to getting gnomad2 installed and working on your Ubuntu system: 1) install 2 libraries on which gnomad2 depends (Use Synaptic for this); 2) find and download the .deb package for gnomad2; and 3) use the dpkg command to install the downloaded package.

The only dependencies my system showed for this package were liblinc and libnjb--liblinc1 and libnjb0.  If those aren't already installed, install them using Synaptic. Since I've installed quite a few things to my system, I can't guarantee that your only missing dependencies will be liblinc and libnjb like it was on mine.  But let's assume your system will be the same as mine for all intents and purposes.  If it's not, and you have other lacking dependencies, we'll see later how you might fix that.

So, having installed liblinc and libnjb, you can now download the .deb file for gnomad2. I found it at [http://kharkoma.homelinux.com/index.php?zone=downs](http://kharkoma.homelinux.com/index.php?zone=downs) but there are likely other places it can be found and downloaded from.  Do a web search to locate an alternate if the above link doesn't work or get you what you want.*

Once you've downloaded that Debian package to your system, open a terminal, cd to the directory where the downloaded package resides and issue ```
sudo dpkg -i name-of-gnomad2-pkg.deb
```. dpkg is the commandline version of the Debian package installation program, and the -i switch is for "install." After this, the gnomad2 package is installed on your system.

To start it, open a terminal and issue the command ```
gnomad2
```.  It should start up: mine fired right up after this.  If you still lack any dependencies, you will see error output in the terminal indicating what dependencies were not found. If you get this sort of message, you'll have to try and resolve those dependencies manually--hopefully using Synatpic to find missing packages. You're on your own in doing that: since it wasn't necessary for me I can't describe exactly what you'll need to do. Anyway, after getting the program working I made a launcher for it in the Gnome panel using the standard method.

I've just browsed my Nomad player and transferred some music. Seems to work fine.

James

* Later edit: looking over that kharkoma site, I see that he offers downloads for libnjb packages, too. I advise NOT using those, but using the ones you can get from Ubuntu repositories using Synaptic. You may foul up Synaptic by trying to use his libnjb packages with dpkg.

PS I should also mention that using the simplified method I've described here, I didn't have to do any sort of fiddling with permissions--like 2 other posters using other methods said they had to here. It worked for my system's user "right out of the box."

---

### Post by natefish on 2004-12-26
Sorry I just checked this, I removed the old file and replaced with the short two line file. There is probably a better way but it worked for me.

---

### Post by Ste on 2004-12-26
[QUOTE=natefish]Sorry I just checked this, I removed the old file and replaced with the short two line file. There is probably a better way but it worked for me.[/QUOTE]
 Which file did you edit, was it /etc/hotplug/usb/usermap ?

---

### Post by wayover13 on 2004-12-27
[QUOTE=Ste]Which file did you edit, was it /etc/hotplug/usb/usermap ?[/QUOTE]

Use my method and you won't need to edit any files like that. Save yourself some headaches and do this the simple way: compiling from source is definitely not required to get this program installed and working. If you save yourself some trouble by not compiling from source, you'll also save yourself the trouble of editing those config files. Like I said, with no editing of any config files, gnomad worked for my user "right out of the box" when I installed using the Debian package method I've described above.

James

---

### Post by Ste on 2004-12-27
[QUOTE=wayover13]Use my method and you won't need to edit any files like that. Save yourself some headaches and do this the simple way: compiling from source is definitely not required to get this program installed and working. If you save yourself some trouble by not compiling from source, you'll also save yourself the trouble of editing those config files. Like I said, with no editing of any config files, gnomad worked for my user "right out of the box" when I installed using the Debian package method I've described above.

James[/QUOTE]
 I have it working but I need to sudo each time to gain access to the mp3 player.
Using the method you described above gives a link to an older version of gnomad2.
I'm running 2.5.0 at the moment. Wondering if I should compile 2.6.1. As I don't see a .deb anywhere for it.

---

### Post by wayover13 on 2004-12-29
[QUOTE=Ste]I have it working but I need to sudo each time to gain access to the mp3 player.
Using the method you described above gives a link to an older version of gnomad2.
I'm running 2.5.0 at the moment. Wondering if I should compile 2.6.1. As I don't see a .deb anywhere for it.[/QUOTE]

Is there something keeping you from searching the web for other package sources? Try [http://ftp.us.debian.org/debian/pool/main/g/gnomad2/gnomad2_2.5.0-2_i386.deb](http://ftp.us.debian.org/debian/pool/main/g/gnomad2/gnomad2_2.5.0-2_i386.deb) . In general, [http://www.debian.org/distrib/packages#search_packages](http://www.debian.org/distrib/packages#search_packages) is the place to search for official Debian packages. Select "unstable" for more bleeding-edge packages.

James

---

### Post by wayover13 on 2004-12-29
The problem with this program is permissions on certain binaries connected with usb management. I just installed this newer version from the Debian package I gave a link for above and when trying to run the program as user I get 

```
usb_set_configuration: Operation not permitted
```

The user is not permitted to run this binary. An interim solution is to make a launcher for the program and use gksudo: that way it is run by the superuser and permissions on that binary aren't a problem. It's worth mentioning that the older version I gave a link for previously didn't have this permissions problem. It worked fine invoking it as the regular user.

James

PS The newer package requires an additional library, too--libid3tag0. That can be found searching Debian packages from the link I provided above.

---

### Post by wayover13 on 2004-12-29
You might find information at this link helpful: [http://www.linuxquestions.org/questions/showthread.php?postid=1097795](http://www.linuxquestions.org/questions/showthread.php?postid=1097795) . I was able to use this information to resolve the binary permissions problem. I actually had the source for gnomad2 on my system, having downloaded and unpacked it earlier in preparation for compiling it on my system, so I was able to get the nomad.usermap and nomadjukebox files from there. This said, there's nothing keeping you from copying and pasting the content the poster at the link given has inserted into his post into files you create on your machine. You then name those files appropriately (nomad.usermap and nomadjukebox) and move them into the directory the poster specifies and change their permissions accordingly: nomad.usermap needs to be 644 and belong to root. The poster says chmod +x nomadjukebox (as root) in his post but I needed to set permissions to 755 in addition to making root the owner for that file.

James

---

### Post by coldsalmon on 2005-04-11
I can't tell if you guys are having the same problem that I am or not.  I can start the program fine, but I always get an error saying "No jukeboxes found on USB bus."  Is this what you guys are dealing with?

Thanks

--C

---

### Post by weblars on 2005-04-11
Hi coldsalmon!

Before I upgraded to Hoary I got the same error all the time. Now Gnomad works just fine for me. I'm using the Creative Zen Touch.

Just install libnjb0 and gnomad2 via Synaptic. Then connect your jukebox via USB and run gnomad2.

If this doesn't work you can give the new libnjb-2.0 a try. Look at libnjb.sourceforge.net and compile it from source.

Lars

---

### Post by coldsalmon on 2005-04-11
Hi,

It's working now.  I guess I had to use kynaptic rather than the CLI apt-get.

--C

---

### Post by xalphas on 2005-04-25
Thereis no way. I had Creative Zen Xtra working many times in fedora and warty 4.10. But in Hoary i got playlist scanned but no more transferring files or play from playlist. 

I am using the gnomad2 2.5 and libnjb 1.1.2 from universe repository. I would be glad if anyone helps me.

Thx.

---

### Post by vassie on 2005-05-19
> I am using the gnomad2 2.5 and libnjb 1.1.2 from universe repository. I would be glad if anyone helps me.

So would I [http://www.ubuntuforums.org/showthread.php?p=179156#post179156](http://www.ubuntuforums.org/showthread.php?p=179156#post179156)

Ben

---

### Post by cdub on 2005-05-20
[QUOTE=natefish]Has anyone successfully installed Neutrino or Gnomad2 and been able to use with Dell Jukebox or other Nomad/Zen MP3 Player?

I have been able to install both successfully yet neither is able to find my Dell Jukebox. The system recognizes the Jukebox on start up and it exists unders devices, yet neither software program seems to find it. 

Anyone have some insight? Maybe a tutorial on what they did to get things working?[/QUOTE]

I finally got gnomad2 working with my Dell DJ 20 (without sudo).  Essentially, I tried everything suggested in this thread, but to no avail... until now (don't get me wrong... I appreciate everyone's postings... I learned quite a bit).  Previously, the closest I came was a successful connection and then the app would hang while "scanning for songs."

Anyway, long story short... I decided to sync my Treo and call it a night when I stumbled upon *my* issues with gnomad2.  For me, the culprit turned out to be gpilot.  I use that little gnome gilot taskbar applet, so I right-clicked it, selected pause daemon, and proceeded to successfully connect gnomad2 to my Dell DJ!  Apparently, the daemon was interferring in some way (for me, at least).

BTW, I'd be happy to submit my configuration and everything that I tried/did in regards to gnomad2 and libnjb... just let me know.  I did not do so in this post because everything that I tried is already in this thread,

Hopefully, this will save at least one person a boatload of valuable time! :)

~cdub

---

### Post by vassie on 2005-05-24
Hello
I am trying to install gnomad2.6.3-1 on Hoary, however it depends on libnjb4, which in turn depends on a newer version of libc6 that is currently install
Can anyone please help me get the latest gnomad2 working, beacuse without it, I cannot get rid of Windows
Thanks
Ben

---

### Post by cdub on 2005-05-24
[QUOTE=vassie]Hello
I am trying to install gnomad2.6.3-1 on Hoary, however it depends on libnjb4, which in turn depends on a newer version of libc6 that is currently install
Can anyone please help me get the latest gnomad2 working, beacuse without it, I cannot get rid of Windows
Thanks
Ben[/QUOTE]

Here's the gnomad2 snippet from a ubuntu setup script that I have... maybe it will help.  Let me know if you run into any problems obtaining required packages and I can send you my sources.list file.

#!/bin/bash
#gnomad2
#---------------------------
sudo apt-get install libusb-dev libid3tag0-dev
wget "http://easynews.dl.sourceforge.net/sourceforge/libnjb/libnjb-2.1.1.tar.gz"
tar xvfz libnjb-2.1.1.tar.gz
cd libnjb-2.1.1
./configure
make
sudo make install
sudo cp nomadjukebox /etc/hotplug/usb/nomadjukebox
sudo chmod 755 /etc/hotplug/usb/nomadjukebox
sudo cp nomad.usermap /etc/hotplug/usb/nomad.usermap
sudo ldconfig
cd ..
rm -Rf libnjb-2.1.1
sudo /etc/init.d/hotplug restart
wget "http://easynews.dl.sourceforge.net/sourceforge/gnomad2/gnomad2-2.6.3.tar.gz"
tar xvfz gnomad2-2.6.3.tar.gz
cd gnomad2-2.6.3
./configure
make
sudo make install
cd ..
rm -Rf gnomad2-2.6.3
sudo gedit /etc/hotplug/usb/nomadjukebox
#change DEVICEPERMS=0600 --> DEVICEPERMS=0666
#ensure gpilotd is paused (gnome gpilot applet)
#connect Dell DJ, cross fingers, and launch gnomad2 :-)
#---------------------------

~cdub

---

### Post by vassie on 2005-05-25
Thank you, I will give it a try :)

*EDIT: It worked a treat, thank you so much :):):)

*EDIT 2: I had to run this command at the end ```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib
```

*EDIT 3: Arrrrrggghhhhh!, firstly, the above command only works for my username, gnomad2 fails to run under sudo, and secondly, I have to run it everytime I login, I rebooted and got the following error ```
gnomad2: error while loading shared libraries: libnjb.so.4: cannot open shared object file: No such file or directory
``` 

Ben

---

### Post by cdub on 2005-05-25
[QUOTE=vassie]
*EDIT 3: Arrrrrggghhhhh!, firstly, the above command only works for my username, gnomad2 fails to run under sudo, and secondly, I have to run it everytime I login, I rebooted and got the following error ```
gnomad2: error while loading shared libraries: libnjb.so.4: cannot open shared object file: No such file or directory
``` 

Ben[/QUOTE]

You had the right approach, but what you did was a temp fix.  BTW, I should've included that in my script snippet... sorry about that.  Try this and let me know how you makeout...

sudo echo /usr/local/lib >> /etc/ld.so.conf
sudo ldconfig

~cdub

---

### Post by vassie on 2005-05-25
I gave in, sorry, I installed it from....

deb [http://debian.balt.net/debian/](http://debian.balt.net/debian/) unstable main contrib non-free
deb [http://debian.balt.net/debian-non-US/](http://debian.balt.net/debian-non-US/) unstable/non-US main contrib non-free
deb [http://debian.balt.net/debian/](http://debian.balt.net/debian/) ../project/experimental main contrib non-free

It also installs libnjb4 and upgrades libc6, I know upgrading libc6 is risky, but it worked for me

Ben

---

### Post by xs38 on 2005-07-31
[QUOTE=cdub]Here's the gnomad2 snippet from a ubuntu setup script that I have... maybe it will help.  Let me know if you run into any problems obtaining required packages and I can send you my sources.list file.

#!/bin/bash
#gnomad2
#---------------------------
sudo apt-get install libusb-dev libid3tag0-dev
wget "http://easynews.dl.sourceforge.net/sourceforge/libnjb/libnjb-2.1.1.tar.gz"
tar xvfz libnjb-2.1.1.tar.gz
cd libnjb-2.1.1
./configure
make
sudo make install
sudo cp nomadjukebox /etc/hotplug/usb/nomadjukebox
sudo chmod 755 /etc/hotplug/usb/nomadjukebox
sudo cp nomad.usermap /etc/hotplug/usb/nomad.usermap
sudo ldconfig
cd ..
rm -Rf libnjb-2.1.1
sudo /etc/init.d/hotplug restart
wget "http://easynews.dl.sourceforge.net/sourceforge/gnomad2/gnomad2-2.6.3.tar.gz"
tar xvfz gnomad2-2.6.3.tar.gz
cd gnomad2-2.6.3
./configure
make
sudo make install
cd ..
rm -Rf gnomad2-2.6.3
sudo gedit /etc/hotplug/usb/nomadjukebox
#change DEVICEPERMS=0600 --> DEVICEPERMS=0666
#ensure gpilotd is paused (gnome gpilot applet)
#connect Dell DJ, cross fingers, and launch gnomad2 :-)
#---------------------------

~cdub[/QUOTE]

Thanks for this, Now my Creative Zen micro works perfectly (better than under W$)
You're great !!!

Xavier.

---

### Post by cdub on 2005-07-31
[QUOTE=xs38]Thanks for this, Now my Creative Zen micro works perfectly (better than under W$)
You're great !!!

Xavier.[/QUOTE]


No prob... glad it worked out for you!

~cdub

---

### Post by bam on 2005-09-15
[QUOTE=cdub]No prob... glad it worked out for you!

~cdub[/QUOTE]
 seems to be stopping and giving me a nice error...

---

### Post by ThirdWorld on 2005-11-30
I just bougth a Zen micro from walmart and was not working. There was an USB error. 
This is the most retarded bug i have ever seen, this time shame on you linux developers. i just went to my menu and edit it, i change the comand line to start the ganomad application and add sudo. Its working ok now, but I really think this type of bugs should be fixed if linux developers want more people to try and switch to the linux platform. you buy a mp3 player and end up with a permisions issues? WTH??? sorry im a little bit mad about this. :confused: 

well its fixed...:rolleyes:

---

### Post by rrsstio5276 on 2007-05-15
> **Ste said:**
> Which file did you edit, was it /etc/hotplug/usb/usermap ?


[Bankruptcy Tsunami memory pollution American Idol](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/index.php)

---

