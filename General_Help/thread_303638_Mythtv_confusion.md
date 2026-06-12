---
title: "Mythtv confusion"
date: 2006-11-20
forum: General Help
---

### Post by LilRayRay on 2006-11-20
Hi all, I just installed mythtv (to run my ATI HDTV card), and I am very confused on how to set it up.  I run "mythtv-setup and it asks me my language then it goes onto the database page.  My first question is, how do I set up my mysql password and also, why does this program need a database to view tv?  Any help on getting this to work is greatly appreciated.

---

### Post by reclusivemonkey on 2006-11-20
> **LilRayRay said:**
> Hi all, I just installed mythtv (to run my ATI HDTV card), and I am very confused on how to set it up.  I run "mythtv-setup and it asks me my language then it goes onto the database page.  My first question is, how do I set up my mysql password

Have you searched the forums for MythTV HOWTOs? I'm pretty sure you will find your answers there. I run my MythTV setup on Slackware, and I am not sure the setup will be the same. The MythTV forums/wiki will certainly have the answer. You don't *need* to set up a root password for mythtv, but depending on your existing security its a good idea.

[EDIT]Actually, the mysql setup is right here in the MythTV documentation;

[http://www.mythtv.org/docs/mythtv-HOWTO-6.html](http://www.mythtv.org/docs/mythtv-HOWTO-6.html)

> **LilRayRay said:**
> and also, why does this program need a database to view tv?  Any help on getting this to work is greatly appreciated.

MythTV does *far* more than let you view tv. The database is for channels, configuration settings, schedules, recording information, video information, music information, etc. If you just want to view tv, I suggest TVTime;

[http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/)

---

### Post by LilRayRay on 2006-11-21
Im very confused here, so please bare my ignorance.  Many of the commands in the guides do not seem to work. I think I am flying blind here, so maybe one could point me in the right direction.  

When I run myth-setup, It asks me my language then it goes to a page that asks for some information (see image below) after this there is an optional LAN setting, then when I click finished, I see this in the comman prompt

```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2006-11-21 09:15:23.872 DBPassword is not set in mysql.txt
2006-11-21 09:15:23.885 New DB connection, total: 1
2006-11-21 09:15:23.893 Unable to connect to database!
2006-11-21 09:15:23.898 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

Total desktop width=1280, height=1024, numscreens=1
2006-11-21 09:15:23.900 Unable to connect to database!
2006-11-21 09:15:23.900 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:23.900 Database not open while trying to load setting: XineramaScreen
2006-11-21 09:15:23.900 Unable to connect to database!
2006-11-21 09:15:23.901 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:23.901 Database not open while trying to load setting: RunFrontendInWindow
2006-11-21 09:15:23.901 Using screen 0, 1280x1024 at 0,0
2006-11-21 09:15:23.901 Unable to connect to database!
2006-11-21 09:15:23.901 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:23.901 Database not open while trying to load setting: Style
2006-11-21 09:15:23.902 Unable to connect to database!
2006-11-21 09:15:23.902 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:23.902 Database not open while trying to load setting: Theme
2006-11-21 09:15:23.902 Switching to square mode (blue)
2006-11-21 09:15:23.903 Unable to connect to database!
2006-11-21 09:15:23.903 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:23.903 Database not open while trying to load setting: GuiOffsetX
2006-11-21 09:15:23.903 Unable to connect to database!
2006-11-21 09:15:23.903 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:23.903 Database not open while trying to load setting: GuiOffsetY
2006-11-21 09:15:23.904 Unable to connect to database!
2006-11-21 09:15:23.904 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:23.904 Database not open while trying to load setting: GuiResolution
2006-11-21 09:15:23.904 Unable to connect to database!
2006-11-21 09:15:23.904 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:23.905 Database not open while trying to load setting: GuiWidth2006-11-21 09:15:23.905 Unable to connect to database!
2006-11-21 09:15:23.905 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:23.905 Database not open while trying to load setting: GuiHeight
2006-11-21 09:15:23.906 Unable to connect to database!
2006-11-21 09:15:23.906 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:23.906 Database not open while trying to load setting: MenuTheme
2006-11-21 09:15:23.907 Unable to connect to database!
2006-11-21 09:15:23.907 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:23.907 Database not open while trying to load setting: QtFontBig
2006-11-21 09:15:23.907 Unable to connect to database!
2006-11-21 09:15:23.907 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:23.907 Database not open while trying to load setting: QtFontMedium
2006-11-21 09:15:23.908 Unable to connect to database!
2006-11-21 09:15:23.913 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:23.913 Database not open while trying to load setting: QtFontSmall
2006-11-21 09:15:23.917 Unable to connect to database!
2006-11-21 09:15:23.933 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:23.933 Database not open while trying to load setting: HideMouseCursor
2006-11-21 09:15:23.961 Unable to connect to database!
2006-11-21 09:15:23.961 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:23.962 Database not open while trying to load setting: RunFrontendInWindow
2006-11-21 09:15:24.335 Unable to connect to database!
2006-11-21 09:15:24.335 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.335 Unable to connect to database!
2006-11-21 09:15:24.336 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.336 Unable to connect to database!
2006-11-21 09:15:24.336 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.337 Unable to connect to database!
2006-11-21 09:15:24.337 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.337 Unable to connect to database!
2006-11-21 09:15:24.337 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.338 Unable to connect to database!
2006-11-21 09:15:24.338 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.338 Unable to connect to database!
2006-11-21 09:15:24.338 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.339 Unable to connect to database!
2006-11-21 09:15:24.339 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.339 Unable to connect to database!
2006-11-21 09:15:24.340 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.340 Unable to connect to database!
2006-11-21 09:15:24.340 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.341 Unable to connect to database!
2006-11-21 09:15:24.341 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.341 Unable to connect to database!
2006-11-21 09:15:24.341 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.342 Unable to connect to database!
2006-11-21 09:15:24.342 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.342 Unable to connect to database!
2006-11-21 09:15:24.342 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.343 Unable to connect to database!
2006-11-21 09:15:24.343 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.343 Unable to connect to database!
2006-11-21 09:15:24.343 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.344 Unable to connect to database!
2006-11-21 09:15:24.348 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.349 Unable to connect to database!
2006-11-21 09:15:24.349 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.349 Unable to connect to database!
2006-11-21 09:15:24.350 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.350 Unable to connect to database!
2006-11-21 09:15:24.350 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.350 Unable to connect to database!
2006-11-21 09:15:24.351 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.351 Unable to connect to database!
2006-11-21 09:15:24.351 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.352 Unable to connect to database!
2006-11-21 09:15:24.352 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.352 Unable to connect to database!
2006-11-21 09:15:24.352 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:24.352 Database not open while trying to load setting: Languagemythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2006-11-21 09:15:24.362 Joystick disabled.
2006-11-21 09:15:25.914 Unable to connect to database!
2006-11-21 09:15:25.914 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:25.915 Database not open while trying to save setting: Language2006-11-21 09:15:25.915 Unable to connect to database!
2006-11-21 09:15:25.915 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:25.915 Database not open while trying to load setting: Language2006-11-21 09:15:25.916 Unable to connect to database!
2006-11-21 09:15:25.916 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:25.917 Database not open while trying to save setting: Language2006-11-21 09:15:25.917 Unable to connect to database!
2006-11-21 09:15:25.917 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:28.405 Unable to connect to database!
2006-11-21 09:15:28.405 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'andy'@'localhost' (using password: NO)

2006-11-21 09:15:28.405 Failed to init MythContext, exiting.
```

I have tryed a couple of the guides, including the mythtv guides, and I really havent gotten anywhere. 

> 
If you just want to view tv, I suggest TVTime;

[http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/)

I have tv time, and although video works, there is no audio.  Also, it doesn't seem to have HD support.

Anyway thanks for the help.  Please excuse any ignorance, Im still quite new to linux, and my tv card it the last peice of hardware I have yet to get to work on linux.

---

### Post by reclusivemonkey on 2006-11-21
> **LilRayRay said:**
> Im very confused here, so please bare my ignorance.  Many of the commands in the guides do not seem to work. I think I am flying blind here, so maybe one could point me in the right direction.  


1. Make sure you have a correctly setup and working mysql database. As I mentioned before I use Slackware for my MythTV box, so I can't help you here.

2. Make sure you have a mythconverge database in mysql.

3. Make sure you have created permissions to the myconverge database for the default user. I don't think you should change the defaults here; stick with mythtv as the user and mythtv as the password. You can try it as you have it set up with andy, but you don't have a password entered in the setup screen you included in your post.

With regard to TVTime, do you have the TV out wired to your soundcard Line-In?

---

### Post by LilRayRay on 2006-11-21
Ahh, that has to be the problem.  The HDTV wonder does both video and audio through the PCI slot.  There is no line out on the card.

---

### Post by reclusivemonkey on 2006-11-21
> **LilRayRay said:**
> Ahh, that has to be the problem.  The HDTV wonder does both video and audio through the PCI slot.  There is no line out on the card.

Ah, not sure how the sound will work then. If you don't mind using a KDE app, I hear Kaffeine is a good app for TV Cards and will do recording if you want a simpler setup.

---

### Post by LilRayRay on 2006-11-21
Ive tryed kaffeine and it doesnt seem to have support for my card.  Anyway, I tried starting mythtv-setup as superuser and, it didnt ask for any database info but rather went right on to setting up the hardware.  The new problem is that when I try to run the actuall tv view is gives me an error saying that it could not connect to the backend server and reccomended that I check my IP settings.  I think I might as well just pop in my happauge card and settle for non-HD tv.

---

### Post by reclusivemonkey on 2006-11-21
> **LilRayRay said:**
> Anyway, I tried starting mythtv-setup as superuser and, it didnt ask for any database info but rather went right on to setting up the hardware.

It doesn't ask for database information. You need to set up the database yourself by reading the documentation. You also shouldn't set up mythtv as the superuser. There is no need and it could cause problems later on. MythTV isn't just a "click and install" application. You *really* need to read the documentation carefully or it won't work as it should. It took me months to get it running the first time, weeks on the second upgrade and this latest update (0.20) I managed to get it going in a couple of days.

> **LilRayRay said:**
> The new problem is that when I try to run the actuall tv view is gives me an error saying that it could not connect to the backend server and reccomended that I check my IP settings.  I think I might as well just pop in my happauge card and settle for non-HD tv.

If you haven't set up the database and mysql permissions correctly it won't work. You also need to start mythbackend. Did you do this?

Again, you really need to read the MythTV documentation carefully and follow all the steps.

---

### Post by superm1 on 2006-11-21
Lilrayray,

there are some oddities that you will have to understand about how things are supposed to work that are detailed in the ubuntu mythtv guide ([http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV))

Particularly,

1) mythtv-setup needs to be ran as superuser. 
2) mythbackend needs to be started as the mythtv user (sudo /etc/init.d/mythtv-backend start)
3) the recordings directory that you choose (default /var/lib/mythtv) needs to have write permissions for the mythtv user or group
4) You either need to add your user to the mythtv group, start mythfrontend as the mythtv user, or copy the /etc/mythtv/mysql.txt to ~/.mythtv

---

### Post by mtron on 2006-11-22
i don't want to confure you even more, but try to get the official release 0.20 from the mythtv homepage and compile it yourself. The debian (or ubuntu?) guys patch it quite heavy, so it's really hard to debug. The documentation for the source build is very good, and when you follow it, i had it up & running in 1/2 an hour (without the time for compiling ;))

---

### Post by reclusivemonkey on 2006-11-22
> **mtron said:**
> i don't want to confure you even more, but try to get the official release 0.20 from the mythtv homepage and compile it yourself. The debian (or ubuntu?) guys patch it quite heavy, so it's really hard to debug. The documentation for the source build is very good, and when you follow it, i had it up & running in 1/2 an hour (without the time for compiling ;))

And the new OpenGL rendering looks fantastic. Very slick...

MythTV can be a pain to get up and running, but once you do, its rock solid and you will get many, many more hours of enjoyment out than you put in. My schedule :D 

[http://reclusivemonkey.homelinux.org:6544/](http://reclusivemonkey.homelinux.org:6544/)

---

### Post by PilotJLR on 2006-11-25
I have the same setup as you. The nay-sayers will tell you the ATI HDTV Wonder won't work in linux, but they are sorely mistaken.

1. consider uninstalling mythtv, as troubleshooting it may be more effort than it's worth.
2. Use the ubuntu repo's (waste of time compiling this yourself)
3. Install mythtv EXACTLY as shown here:
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
4. Upload new firmware to your ATI HDTV Wonder as shown here:
[http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder](http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder)

Let me know if you have an issue with that last step, as it's not tailored specifically for Ubuntu. But I assure you it will work (and is required), as I too have an ATI HDTV Wonder used by MythTV.

Good luck!

---

### Post by FryerFox on 2006-11-25
I had read up a lot on MythTV before I bought a TV card yesterday (Hauppage PVR USB2), and had seen many places complaining of how hard it was to get it working properly.

It took a couple of hours to compile the drivers, pull the firmware off the Windows CD supplied for the card, and set up the server, but I finally got it working. Given that I am fairly well versed in Linux (but had no clue as to how TV Cards worked in general) I want to say that it really is near to impossible for a newbie to get it going unless they follow a guide verbatim.

If you're not new to Linux, then I suggest trying to go into phpmyadmin and remove the two entries for the mythtv user. Add them back with access to everything (at least for the myth database) using the same password that you plugged into mythtv-setup.

This is a step I had to take myself, and I'm not really sure why. Also, could some of your troubles be due to not setting up a mythtv user?

I didn't follow a single guide on how to set up MythTV, but [https://help.ubuntu.com/community/MythTV_Edgy](https://help.ubuntu.com/community/MythTV_Edgy) was very helpfull.

---

### Post by msuemnig on 2006-12-02
Very beginner questions to follow, pls forgive.

I tried to use the mythTV instruction guide here: [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

I got as far as trying to install the dvb tools

typing: 
sudo apt-get install dvb-utils dvbstream

gets me:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dvb-utils

and typing: 
sudo apt-get install gxine mplayer
gets me:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libdvdread3 (>= 0.9.6) but it is not installable
           Depends: libggi2 (>= 1:2.2.1) but it is not installable
E: Broken packages

when I run lshw, I see the hdtv wonder (I know I bought a non-linux friendly card, but I'm stuck with it), under multimedia...let me know if I should post that...

I'm really at a loss as to where to go from here.

Thank you very much for your help in advance!!

---

### Post by superm1 on 2006-12-02
Sounds like you dont have either universe or multiverse added to your repository lists.  IMO, you won't need those dvb utillities necessarily.  Myth does all the tuning for the card.

---

### Post by msuemnig on 2006-12-03
SuperM,

thanx a lot for the response!! :)  I really appreciate the help.  I added the universe and downloaded the programs.  When I try to run the next step (info included below), the card doesn't run....it doesn't show up when I run lshw under PCI slots....so, I think I don't have the card installed correctly.  I found an install guide at [http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder](http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder)
The first step is to chmod +x on a folder called documentation, which doesn't exist, so I don't know what to do.  

The guide is written for people who don't suck at linux.  I don't fall into that category...yet!  Can anyone add some more explicit details to it pls?

root@mythTV:/home/msuemnig# mkdir /root/.tzap
root@mythTV:/home/msuemnig# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill > /root/.tzap/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 754166670 0 3 9 1 0 0 0
WARNING: frontend type (ATSC) is not compatible with requested tuning type (OFDM)
ERROR: initial tuning failed
dumping lists (0 services)
Done.

---

### Post by burek on 2006-12-03
I got this :
```

dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.20-0.2ubuntu2); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-database
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@tower05:/home/winwood# dpkg-reconfigure --force mythtv-database
Failed to connect to database: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database

 
```

I did apt-get install mythtv

then:
 
i ran mythtv as root
```
  12-03 18:28:36.803 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-12-03 18:28:46.242 Unable to connect to database!
2006-12-03 18:28:46.242 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-12-03 18:28:46.299 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-12-03 18:28:46.355 Failed to init MythContext, exiting.
```

then error ; i understand anythg how it works 

Help
  
I found this [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)
by chance
  
but still undersntacn anthyghg for the moment
i have no phpamdin when i go in firefox and type localhost 

> MythTV uses MySQL extensively, so we have to get this set up before anything else. Fire up Firefox and in the address bar, type "localhost". Click the "phpmyadmin" directory. Type in "root" in the login form, and no password. Look down the resulting page for a "Change password" link, and click it; type in what you want your MySQL password to be. Note that this is *not* your root password, or your primary sudo account password. This one is separate, so make it whatever you want it to be. But remember it; we will need it late

---

### Post by superm1 on 2006-12-03
Two things:

_As for your HDTV Tuner firmware:_

The script that they are calling for is attached to this post.  

1) Save the script in your home directory.
2) Extract the script
```
gunzip get_dvb_firmware.gz
```3) Make the script executable.
```
chmod +x get_dvb_firmware
```4) Run the script
```
 ./get_dvb_firmware nxt2004
```
5) Copy the firmware to your /lib/firmware directory
```
sudo cp dvb-fe-nxt2004.fw /lib/firmware
```
6) Load the module
```
sudo modprobe cx88-dvb
```
7) Continue mythtv setup as described below:

_About setting up mythtv:_

That howto is dated and doesn't reflect the way things work in Edgy.

You need to install mysql-server prior to mythtv.  It is ***not*** a dependency because you can have the mysql server located elsewhere on the network, not necessarily on the same machine that mythtv-database is even installed!

Following the updated howto for edgy is preferable: [http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)

---

