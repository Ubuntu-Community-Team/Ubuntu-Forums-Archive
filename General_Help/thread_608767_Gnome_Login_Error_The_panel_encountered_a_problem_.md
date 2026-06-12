---
title: "Gnome Login Error The panel encountered a problem while loading &quot;OAFIID ..."
date: 2007-11-10
forum: General Help
---

### Post by ideasman42 on 2007-11-10
Hi, were running a small studio with ubuntu gutsy workstations and every now and then users get this error in 5 separate error dialogs.

The panel encountered a problem while loading "OAFIID:Deskbar_Applet".
The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".
The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".
The panel encountered a problem while loading "OAFIID:GNOME_MultiLoadApplet".
The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet"

Nautilus also fails to startup.

These are normal gutsy installs with NIS/NFS logins enabled, however I dont think NIS is causing the problem since their home directories still function as expected.

The odd thing is its happened on 3 workstations, and the users are not tinkering with the systems (installing junk or changing their configuration greatly) - I have searched for this error before but others have got it as result of an upgrade, where as this is a fresh install.

I worked around the problem by logging off. killall gconfd-2, and removing gconf-username and mapping-username, orbit-username files from the temp dir. Then the problem went away.

Here is the details for the system setups we had.

[http://wiki.blender.org/index.php/User:Ideasman42#Peach_System_Setup](http://wiki.blender.org/index.php/User:Ideasman42#Peach_System_Setup)

Wondering if there is a more straightforward solution for this.

Thanks...

---

### Post by gtr225 on 2007-11-11
I have the same problem. It doesn't happen on every login, but when it does I have to Ctrl+Alt+Backspace and try logging in again.

---

### Post by ideasman42 on 2007-11-13
> **gtr225 said:**
> I have the same problem. It doesn't happen on every login, but when it does I have to Ctrl+Alt+Backspace and try logging in again.

yeah, I tried this too. but it didnt work for me. rebooting worked, but then it happened again next they logged out.

I suspect orbit or gconfd is crashing/closing somehow, and leaving temp files that prevent restarting normally. since removing files in the /tmp dir fixed the problem.

Still this is really bad if others have it. perhaps its a known problem?

---

### Post by gtr225 on 2007-11-13
I think it may be a common problem. However it took a while for me to find this thread so perhaps others may have trouble finding resources on this problem. I hope it can be resolved soon, it is incredibly annoying. It got so bad for me just now that I had to reboot because when I would try logging in after Ctrl+Alt+Backspace, I would see my wallpaper and nothing else, no panels. When I rebooted from the login screen, it then went to a generic login screen (not sure if it's related) from where I had to tell it to reboot again.

---

### Post by erginemr on 2007-11-13
+1

I am also suffering from the same problem with the following error message:
The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".

and when that happens, I lose all theming settings, icons, orange (human) colors and such and fall back to a default Gnome theme, which is pretty annoying. Funny thing is that, it happens from time to time, that is, is not some consistent error, you sometimes have it, sometimes not. 

As ideasman42 suggested above:
"... I worked around the problem by logging off. killall gconfd-2, and removing gconf-username and mapping-username, orbit-username files from the temp dir. Then the problem went away...."

it may have something to do with the locked files in the temp folder that decide to remain locked by themselves.

Possibly a bug, which I hope will be addressed by the developers very soon.

---

### Post by gtr225 on 2007-11-13
Is what you suggested a perminent fix for the problem?

---

### Post by erginemr on 2007-11-14
> **gtr225 said:**
> Is what you suggested a perminent fix for the problem?

I hope so. What I am trying to say is, the problem is not permanent, so the source of the problem should not be either. If there were some missing files or erroneous settings in config files, the problem would be permanent.

The only explanation I can put forward regarding this enigma is temporary lock files. Perhaps, the problem occurs after some lock files remain as residual, and is gone when they are gone (or released) too. Then again, I am not sure yet...

---

### Post by gtr225 on 2007-11-14
I'll try this later today and see if it resolves the issue.

---

### Post by ubuntu1sttimer on 2007-11-14
Same "OAFIID:GNOME Fast User Switch Applet" message here also.

---

### Post by superid on 2007-11-16
Same error here, I'm running Ubuntu Gutsy (7.10) 64-bit.

I encountered the problem when switching between users. The user being switched to had already previously logged in.

---

### Post by gtr225 on 2007-11-16
> **erginemr said:**
> I hope so. What I am trying to say is, the problem is not permanent, so the source of the problem should not be either. If there were some missing files or erroneous settings in config files, the problem would be permanent.

The only explanation I can put forward regarding this enigma is temporary lock files. Perhaps, the problem occurs after some lock files remain as residual, and is gone when they are gone (or released) too. Then again, I am not sure yet...
I tried it and it seemed to do the trick for now. The problem has yet to reappear.

---

### Post by erginemr on 2007-11-16
> **gtr225 said:**
> I tried it and it seemed to do the trick for now. The problem has yet to reappear.

So far so good. Mine is also working for now. Let's wait and see...

---

### Post by gtr225 on 2007-11-16
Any word on exactly what is causing this problem and what packages are related to it?

---

### Post by erginemr on 2007-11-17
Nope. But the error started after I installed IceWM desktop to try it. Thinking that IceWM might have caused this behavor, I have deleted it. But the error message kept appearing for a few more sessions and then washed away by itself.:confused:

---

### Post by ideasman42 on 2007-11-17
I should have mentioned, in my case they are 64bit systems also. has anyone had this happen with a clean 32bit install?

---

### Post by gtr225 on 2007-11-17
> **ideasman42 said:**
> I should have mentioned, in my case they are 64bit systems also. has anyone had this happen with a clean 32bit install?
I'm running a clean 32-bit install.

---

### Post by gtr225 on 2007-11-18
Ok the problem occured again. Followed the steps and I could login again, however after logging out the problem would occur again and about two more times after.

---

### Post by erginemr on 2007-11-18
> **gtr225 said:**
> Ok the problem occured again. Followed the steps and I could login again, however after logging out the problem would occur again and about two more times after.

Darn! Are you using any other desktop alongside with Gnome, such as Fluxbox, IceWM, Enlightenment, etc?

---

### Post by ideasman42 on 2007-11-21
Seems like we should do a bug report, this keeps happening every so often for people here. I just remove their temp files and kill gconfd-2.

This could also happen because of Pressing Ctrl+Alt+Backspace (I do it sometimes when nothing important is running) - it would make sense that if some apps run in gnome dont die correctly.

---

### Post by gtr225 on 2007-11-24
> **erginemr said:**
> Darn! Are you using any other desktop alongside with Gnome, such as Fluxbox, IceWM, Enlightenment, etc?I'm just using plain old GNOME.

---

### Post by gtr225 on 2007-11-24
> **ideasman42 said:**
> Seems like we should do a bug report, this keeps happening every so often for people here. I just remove their temp files and kill gconfd-2.

This could also happen because of Pressing Ctrl+Alt+Backspace (I do it sometimes when nothing important is running) - it would make sense that if some apps run in gnome dont die correctly.I would like to file a bug report but I'm not sure which program this would fall under. Has anyone found any existing bug reports related to this?

---

### Post by gtr225 on 2007-11-24
Ok I posted a bug report for this issue here [https://bugs.launchpad.net/ubuntu/+bug/164804](https://bugs.launchpad.net/ubuntu/+bug/164804) I used the first post in this thread to sum up what's happening when a user suffering from this problem attempts to login.

---

### Post by erginemr on 2007-11-24
> **gtr225 said:**
> Ok I posted a bug report for this issue here [https://bugs.launchpad.net/ubuntu/+bug/164804](https://bugs.launchpad.net/ubuntu/+bug/164804) I used the first post in this thread to sum up what's happening when a user suffering from this problem attempts to login.

Thank you very much. Let's cross the fingers and hope that it will be addressed soon.

---

### Post by gtr225 on 2007-11-24
Yea I would also encourage everyone in this thread to subscribe to the bug report to keep track of its status and perhaps add some input if possible.

---

### Post by mdhmdh31 on 2007-11-24
I have the same problem starting from an install of Kubuntu Gutsy-64 and then installing gnome.

---

### Post by gtr225 on 2007-11-24
Does anyone have any idea what package is causing this error? It would be helpful if I could find that out so I can add it to the bug report.

---

### Post by Ripfox on 2007-11-27
This is happening to me as well, randomly on an apple g3 laptop with Gutsy.

---

### Post by Ripfox on 2007-12-01
Anyone figure this out?

---

### Post by erginemr on 2007-12-01
> **gtr225 said:**
> Does anyone have any idea what package is causing this error? It would be helpful if I could find that out so I can add it to the bug report.

Well, it did happen again. This time, when I have tried adding a gnome splash screen to my session, almost the same as you have explained in your bug report. 

Did anyone notice that Gnome splash screens (the one that shows up after the login prompt) have been omitted from Gutsy? I first thought maybe I have erased it unintentionally, by the Gutsy Live CD does not have them either. The only one that exists is the default Gnome splash screen but it was disabled from within Gconf settings. Whatever, to get them back, I have collected the splash screens from the older Feisty Live CD and this problem re-occurred when I tried to implement them to my Gutsy system, 

Maybe the developers knew that something wrong would happen when you enable it and have removed the splash screen altogether... :confused:

---

### Post by Leo the Lion on 2007-12-14
The exact same thing is happening to my system (I'm running Ubuntu 7.10). On top of that, if I try clicking on the Screen Saver under System>Preferences, the system reboots. 

Any ideas on this yet?

---

### Post by mlissner on 2007-12-14
> **Leo the Lion said:**
> The exact same thing is happening to my system (I'm running Ubuntu 7.10). On top of that, if I try clicking on the Screen Saver under System>Preferences, the system reboots. 

Any ideas on this yet?

I posted my solution to this here:[http://ubuntuforums.org/showpost.php?p=3907202&postcount=6](http://ubuntuforums.org/showpost.php?p=3907202&postcount=6)

Worked for me. 

Regarding the screensaver problem, I think your computer is probably not restarting entirely. I am theorizing that X is crashing. 

Were I you, I'd try something like this ```
gnome-screensaver-preferences &> outputFile.txt
```

That will create an outputFile with the error messages that happen when you run the grnome-screensaver-preferences dialog. That could help you figure out the real problem. Once you've got that, you can start a new thread to that topic.

---

### Post by Leo the Lion on 2007-12-16
> **mlissner said:**
> I posted my solution to this here:[http://ubuntuforums.org/showpost.php?p=3907202&postcount=6](http://ubuntuforums.org/showpost.php?p=3907202&postcount=6)

Worked for me. 

Regarding the screensaver problem, I think your computer is probably not restarting entirely. I am theorizing that X is crashing. 

Were I you, I'd try something like this ```
gnome-screensaver-preferences &> outputFile.txt
```

That will create an outputFile with the error messages that happen when you run the grnome-screensaver-preferences dialog. That could help you figure out the real problem. Once you've got that, you can start a new thread to that topic.

Thanks for the help. I tried the screensaver code, but the same thing happened, the system restarted as soon as I hit enter after the code.
Any ideas?
Thanks again.

---

### Post by mlissner on 2007-12-16
OK. Now do this: ```
more ~/outputFile.txt
``` and let us know what is output. If we're lucky, we might have some error messages in there.

---

### Post by Leo the Lion on 2007-12-23
> **mlissner said:**
> OK. Now do this: ```
more ~/outputFile.txt
``` and let us know what is output. If we're lucky, we might have some error messages in there.

Ok, this is what I got after running the code:

```
** (gnome-screensaver-preferences:6131): DEBUG: Found best visual for GL: 0x2c
gnome-screensaver-preferences: Fatal IO error 104 (Connection reset by peer) on 
X server :1.0.
```

Oh, and thanks for the help.

---

### Post by mlissner on 2007-12-23
Hmmm...that doesn't mean anything to me, but you should try googling some of the words in there and see what you learn. Try google.com/linux.

---

### Post by Leo the Lion on 2007-12-24
For those with the error message "OAFIID....", here's what I did:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

This installs any gnome apps that might have gotten screwed up during the installation of other software.

---

### Post by pxrox on 2008-01-13
I have the same problem (2.6.22-14-386 kernel). The reinstallation of gdm, etc as mentioned above did NOT solve the problem.

---

### Post by mlissner on 2008-01-13
Did you try following the steps in my link above? Those might work for you, since they are a little more extreme than what I've seen elsewhere.

---

### Post by pxrox on 2008-01-13
Yes, I did follow your instructions:

```
aptitude search applet | more
aptitude reinstall [any applet preceded by a v or an i in previous step]
```

Some applets got installed OK, but then lots of python errors on, e.g., deskbar-applet !

I just posted separately regarding this python error, [http://ubuntuforums.org/showthread.php?p=4131366](http://ubuntuforums.org/showthread.php?p=4131366) , which is really vexing me (worked hard to get python2.5 uninstalled/reinstalled, and yet still I get these python errors w/

```
 sudo apt-get purge deskbar-applet
```

(see [http://ubuntuforums.org/showthread.php?p=4131366](http://ubuntuforums.org/showthread.php?p=4131366) )

I thought I was fixing something little, and it seems to have turned into something big....:(

---

### Post by mlissner on 2008-01-13
Well, I'm betting the python problem will need to be solved before we can return to this. Try this link, and see if you find anything interesting:
[http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&q=%22Could+not+find+platform+independent+libraries+%3Cprefix%3E%22&btnG=Search](http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&q=%22Could+not+find+platform+independent+libraries+%3Cprefix%3E%22&btnG=Search)

I started reading them, but I think you might have better success.

---

### Post by pxrox on 2008-01-14
Yeah, I had looked at a bunch of these. Seems to be idiosyncratic to each person's trouble, but the common thread may be a messed up python installation. My guess (only that) is that once you have one or more pythons correctly installed (e.g. ubuntu's default 2.4 & 2.5), adding in another one (as I did, 2.3, to run some legacy python code) can completely screw up all the python libraries/includes, unless you know exactly what you are doing (and automatic configure/make scripts seem to assume that they are the only python on your system...).

---

### Post by gilf on 2008-01-16
I'm adding information here in case it may help in determining the cause of the problem:

This morning one of our Samba networked Ubuntu computers had the error message:

> 
"Error: The panel encountered a problem while loading "OAFIID: Gnome_fastuserswitchapplet". Do you want to delete the applet from your configuration?"

The workstation is a plain vanilla Ubuntu 7.10 i386 install which has been working for about a month. No updates have been applied yet. It is networked with Samba. Two users are installed on this workstation.

One major network change was instituted last night -- we went from DHCP to static IPs. Systems were tested last night and the network was functional. This is a home network with a dialup connection, and we turn the network (workstations router and modem) off when not in use.

A nautilus bookmark exists on the problem workstation for a Samba shared file folder on another workstation.

When the workstation was started this morning, the routers and modem were turned off, as was the computer with the shared Samba file.

The error message appeared twice after two hard reboots. It appeared about a minute after the desktop was up.

A third attempt at booting was succesful and did not show the error message -- the router, modem, and shared folder workstation had been started BEFORE the reboot.

I'm wondering whether this problem is related to STATIC configured networks which are unresponsive, or unconnected.

I notice some additional evidence here (static IP, network non-functional, same error message):

[http://ubuntuforums.org/showthread.php?t=632755](http://ubuntuforums.org/showthread.php?t=632755)


EDIT: the workstation does not have an additional python version installation.

---

### Post by pxrox on 2008-01-16
My laptop is hard-wired into a Verizon-supplied FIOS wireless router (sorry, at work now, and cannot get router manufacturer/model number; let me know if important).

I have no idea whether my laptop gets a static or dynamic IP address from the router (how do I check this?).

That said, the router & my laptop connection to it has not changed since I first loaded up ubuntu (clean install, Dec. 2007).

---

### Post by gilf on 2008-01-16
One other possibly relevant piece of the puzzle:

When shutting down the problem computer last night there was a warning message that 2 users would be disconnected.

From some prior posts, and from the bug report, it appears  that one fix for the repeated error message is to remove specific user files from the temp folder which seem to have been left over. 

That might agree with the user disconnection warning message above.

In our case the disconnected users would have been Samba users linking to shared files on the problem workststion.

---

### Post by pxrox on 2008-01-16
Just updated to Hardy's developing kernel - 2.6.24 ( [http://ubuntuforums.org/showthread.php?t=646755&highlight=kernel+update](http://ubuntuforums.org/showthread.php?t=646755&highlight=kernel+update) , followed by Envy to reinstall my nvidia driver) - in effort to fix this problem (it did, at least for the last two reboots!), and also fix troubles I have with delays during typing (still vexing me). Upgrading kernel as suggested here ( [https://bugs.launchpad.net/ubuntu/+bug/39315](https://bugs.launchpad.net/ubuntu/+bug/39315) ) didn't fix that bug for me.

---

### Post by s4n8eep on 2008-01-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/164804](https://bugs.launchpad.net/ubuntu/+bug/164804) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This problem was solved for me after I did what is mentioned in the solution provided by

"mlissner"  here :

[http://ubuntuforums.org/showpost.php...02&postcount=6](http://ubuntuforums.org/showpost.php...02&postcount=6)

later i had to install "gnome-applets" though, since it  had become 'c' for some reason.

---

### Post by raydar on 2008-01-24
I just had this happen on a clean Gutsy install, with only 1 user logged in--specifically, the message was:

The Panel encountered a problem while loading "OAFIID:Deskbar_Applet".
Do you want to delete the applet from your configuration?

This happened a couple of boots in a row, with the panel at the top displayed but unresponsive (menus wouldn't open, etc.)  The second time, I chose "yes" to delete it from my configuration, and after that the problem didn't recur.

One potentially interesting circumstance is that this error followed some kind of disk corruption, where I had to manually run fsck (and basically hold down the "Y" key 'cause I forgot to add the "fix everything" switch when I typed the command).  I have no clue what caused the corruption.

Another conceivably relevant factor--since there's been some mention here of temp files and users logging on and off--is that this is a 1999 computer that doesn't meet the "year 2000 cutoff" and doesn't shut down properly (regarding which I just now found the thread [http://ubuntuforums.org/showthread.php?t=629939](http://ubuntuforums.org/showthread.php?t=629939) ).  The shutting-down progress bar does shrink all the way to the end, so I doubt this is the cause of some temp files' not being deleted, but I thought I'd mention it anyway.

---

### Post by gilf on 2008-01-24
I had the problem return, and then there was a crippling slowdown of the machine -- booting took forever, same error message returned, plus new ones about services unable to configure, took forever to navigate, eror messages eventually would appear blank.

Tried to go to Synaptic, but root password no longer worked.

Then:

1.) Booted into Recovery Mode
2 ) apt-get remove gnome-applets
3.) apt-get install gnome-applets
4.) apt-get install ubuntu-desktop
5.) Restart computer

The computer booted up normally, with no error messages. Speed was normal. Root password works again.

Phew.

---

### Post by ManOnOneWheel on 2008-01-26
I just got this very same error as well under very pecular circumstances. I am a college student hard wired into the schools DHCP network jack. I was browsing along and my web pages stopped loading, I lost connection to the LAN and everything started running really slow al within like 30 seconds.

After a few reboots the error popped up on my screen. 

I checked the jack in windows, no connection there. I tried the jack with my lapto, no connection.

I called up the IT people and apparently my network jack was turned off because of an Acceptable Use Policy violation(yikes!) but it seems to me the disabling of my network jack is what caused the error, and I also wonder if the error could have caused my AUP violation. The IT guy said I would have to talk to the network people

Unfortunatly they turned it off at 5:00 on a Friday so I was not able to speak to anyone about this.
Quite convient.

I have been messing around on the Samba network lately. Just browsing around and seeing what kind of stuff is hooked up. In hindsight this was probably a bad idea, but I was just curious.

The above steps did not fix my problem, but I am ready for a fresh install anyway.

Oh, and this is on 64-bit Gutsy.

Just one more report to the cause.

---

### Post by salviablue on 2008-03-01
Hi, I am having those same infernal errors appearing, fortunately for me (sort of) they only occur after I log out and back in again or if I soft reset X (ctrl + alt + del). I get about 7 of these. Unfortunately for me it has happened a few time when my windows-philes friends have been around to witness the `superiority` of a linux desktop system, becoming quite embarassing!!
  I am running Gutsy (7.10) on the generic kernel (32 bit) on an Advent 7201 laptop.

---

### Post by linucksrox on 2008-04-17
I had the same problem just recently, after a clean install of Ubuntu Studio 7.10.  I installed the ATI fglrx driver, compiz stuff, and then xserver-xgl (which installed libglitz1 and libglitz1-glx1).  After installing xserver-xgl with that libglitz stuff, my desktop looked different, and compiz didn't work properly, so I uninstalled (using synaptic) xserver-xgl.  That's when I started getting this error.  So I figured, Synaptic to uninstall libglitz1 and libglitz1-glx1, restarted, and problem solved.  So it's worth a shot, quick and easy.  Start up Synaptic and see if libglitz1 is installed and maybe uninstall it... just a suggestion.

---

### Post by Dilberito on 2008-05-22
> **Leo the Lion said:**
> For those with the error message "OAFIID....", here's what I did:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

This installs any gnome apps that might have gotten screwed up during the installation of other software.

This worked for me, at least it seems that way for now.

---

### Post by mr91nk on 2008-05-31
> **Dilberito said:**
> This worked for me, at least it seems that way for now.This made the trick for me as well. I was running some uninstalls (Ekiga, Evolution among a few other applications) and at some point it seems gnome-panel was also uninstalled (either by mistake by me, or as a consequence by smth else). It was after re-installing gnome-panel that those errors appeared. Still really don't know why, but I'm happy my machine is running smoothly again, so thanks to Dilberito! :)

---

### Post by HRshovinstuff on 2008-06-06
Just wanted to post about my experience with this same problem.  I'm using Ubuntu 8.04 AMD64

I was getting the same error involving applets crashing.  My fix was simple.  Get to a terminal, recovery mode, ctrl+alt+F1, etc.

sudo apt-get remove gnome-applets
sudo apt-get install gnome-applets

restart your computer


P.S.   My problems began when I fell asleep watching a flash format movie full screen with VLC.  I woke up - my monitors were in standby mode.  I moved the mouse and yet they would not wake up.  So I pressed the restart button on my tower.  When I logged back in the applets would not start.

---

### Post by Walter Melon on 2008-07-10
> **gilf said:**
> I had the problem return, and then there was a crippling slowdown of the machine -- booting took forever, same error message returned, plus new ones about services unable to configure, took forever to navigate, eror messages eventually would appear blank.

Tried to go to Synaptic, but root password no longer worked.

Then:

1.) Booted into Recovery Mode
2 ) apt-get remove gnome-applets
3.) apt-get install gnome-applets
4.) apt-get install ubuntu-desktop
5.) Restart computer

The computer booted up normally, with no error messages. Speed was normal. Root password works again.

Phew.
I had the same problem, I deleted Evolution because I didn't use it and after I shut it down all the errors with the applets popped up.  Long story short, Your way worked perfectly. :) Thanks

---

### Post by mysterymann78 on 2008-07-14
I uninstalled Samba and all works well now. Scared to reinstall now but never had to use it anyway so no great loss.

---

