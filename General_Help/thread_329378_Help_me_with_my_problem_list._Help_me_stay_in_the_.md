---
title: "Help me with my problem list. Help me stay in the linux world!"
date: 2007-01-01
forum: General Help
---

### Post by DrSasaroli68 on 2007-01-01
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) 

I am using ubuntu for nearly three months and i have put quite a good effort in learning thing and trying to fix problems and bugs which just keep popping up.
I was quite an ubuntu enthusiast (i conviced 3 mates to install it and use it!) but what happened last night was the last drop. Unless things start to get fixed i will be "upgrading" to vista shortly. I want a useable PC and as it seems i cannot get it with ubuntu.

This is a list with the problems which i am currently facing. If the most important issues are solved i will be more than pleased to continue my linux experience. If not i will probably say goodbuy to linux.
Hoping that the community is the stong part of UBUNTU i am asking for your help, because my courage and TIME is running really low.....

I have a Fujitsu Lifebook P7010 (ultraportable) and it has kubuntu edgy 6.10 on it. And here are my troubles

Lets start
1)WRONG RESOLUTION AFTER SUSPEND HYBERNATE. After either Hibernate or standby the screen resolution which normaly is  1280x768 changes to 1280x1024?? something really ugly and un-usable.I have to reboot, or kill X in order to get it back to normal which really means that i do not have the functionality of either suspend or hibernate something which is killing me. (P.S. i used 915resolution to get the resolution correct in the first place)

2)No matter what i do, i cannot change the power saving timer on the monitor.It just goes back at 5hrs!!!! 

3)NOT READING ALL THE FILES IN NTFS. Now this really pissed me off!! I have an NTFS partition with a MUSIK folder in it. Now the folder contains under MS 3172 files and consumes 11,4 GB.All of which are playable. Linux on the other hand sees that only 2430 files exist at 9GB of space.
IS THERE AN EXPLANATION ABOUT THIS?? Under linux only around half of the files under each folder is readable-seeable. WHY?? 

4)The FnF3 mute button pops up as it should, a window which say mute on-off. My problem is that as far as i can tell, it mutes the MasterChanel , which is not used and has no affect in the P7010, while it should mute headphones-or PCM channels to actyally MUTE the sound.
HOW can i fix this around?In linux the myth is that you can change everything. HOW can i make FNf3 mute everything and not just the unused Master chanell??\

5)each time i want to run vmware server after a restart i have to reconfigure it. Something time-consuming and nerve cracking. Any fixes???

6)Knights chess program crashes in EVERY game. Any syggestions? other progs?

7)How can i find out the temperature of my machine and most important wheather the fan is working correctly or not?

8)I also have a problem with amarok and greek ID3 tags,but i think i can live with that, though a fix would be great :mrgreen: 
 
9)Suggest a torrent program.

The list was way bigger but i fixed some things. 1-2-3-7 are absolutely must for me. With the other problems i can live with. Excuse me for me tone, but problems just KEEP POPING up with a rate which i have no time to get them fixed.

Any help will be depply appriciated. Thanx in andvance fellow ubuntu users.
I will be closely monitoring the thread, and i will try to provide with any information needed. Thanx again and a happy new year.

---

### Post by adaptr on 2007-01-01
> **DrSasaroli68 said:**
> I am using ubuntu for nearly three months and i have put quite a good effort in learning thing and trying to fix problems and bugs which just keep popping up.
That is good.

>  I was quite an ubuntu enthusiast (i conviced 3 mates to install it and use it!) but what happened last night was the last drop. Unless things start to get fixed i will be "upgrading" to vista shortly. I want a useable PC and as it seems i cannot get it with ubuntu.Most people can, but it takes different amounts of perseverance and expertise in different circumstances.

>  This is a list with the problems which i am currently facing. If the most important issues are solved i will be more than pleased to continue my linux experience. If not i will probably say goodbuy to linux.That, of course, is entirely up to you.

> Hoping that the community is the stong part of UBUNTU i am asking for your help, because my courage and TIME is running really low.....This, however, is probably the worst attitude you can take.
We do not exist to make your Ubuntu work.
Either you want it, or you don't - no harm done, it's your PC.

But let's have a look.

> I have a Fujitsu Lifebook P7010 (ultraportable) and it has kubuntu edgy 6.10 on it. And here are my troublesSigh.. laptops... not one for the easy road, are you ?

> 1)WRONG RESOLUTION AFTER SUSPEND HYBERNATE. After either Hibernate or standby the screen resolution which normaly is  1280x768 changes to 1280x1024?? something really ugly and un-usable.I have to reboot, or kill X in order to get it back to normal which really means that i do not have the functionality of either suspend or hibernate something which is killing me. (P.S. i used 915resolution to get the resolution correct in the first place)Well, A) hibernate is seriously broken in many laptops, and
B) this is more a problem with specific hardware combinations than with Ubuntu in general.
You may need some very funky kernel settings to get *your* laptop working with hibernation and or suspend-to-disk.
There are support groups for just these kinds of things.

> 2)No matter what i do, i cannot change the power saving timer on the monitor.It just goes back at 5hrs!!!!Again, this is very hardware-specific.
Have you tried googling for your laptop model and a question related to this issue ?

>  3)NOT READING ALL THE FILES IN NTFS. Now this really pissed me off!! I have an NTFS partition with a MUSIK folder in it. Now the folder contains under MS 3172 files and consumes 11,4 GB.All of which are playable. Linux on the other hand sees that only 2430 files exist at 9GB of space.
IS THERE AN EXPLANATION ABOUT THIS??There certainly is.
NTFS is a proprietary, closed-source filesystem, for which Microsoft **does not publish the specifications**.
The fact that there is **any** NTFS support in Linux _at all_ is a credit to the unrelenting devotion of many volunteers.

> 4)The FnF3 mute button pops up as it should, a window which say mute on-off. My problem is that as far as i can tell, it mutes the MasterChanel , which is not used and has no affect in the P7010, while it should mute headphones-or PCM channels to actyally MUTE the sound.
HOW can i fix this around?In linux the myth is that you can change everything. HOW can i make FNf3 mute everything and not just the unused Master chanell??\See response to #2, above.
Google.

>  5)each time i want to run vmware server after a restart i have to reconfigure it. Something time-consuming and nerve cracking. Any fixes???Don't use vmware ?
Seriously, if using closed-source programs is really that much of an issue then you're hopelessly tied to Windows in any case.

> 6)Knights chess program crashes in EVERY game. Any syggestions? other progs?Erm.. hundreds ? **Thousands **?

>  7)How can i find out the temperature of my machine and most important wheather the fan is working correctly or not?If your laptop hardware is not insanely stupid, there are software packages that can tell you all this and more.

> 8)I also have a problem with amarok and greek ID3 tags,but i think i can live with that, though a fix would be great :mrgreen: Fix your fonts, or use the right settings (ever heard of Unicode?).

>  9)Suggest a torrent program.No.
There are literally dozens to choose from, and not knowing what your problem is with any of them, I see no issue here.

>  The list was way bigger but i fixed some things. 1-2-3-7 are absolutely must for me. With the other problems i can live with. Excuse me for me tone, but problems just KEEP POPING up with a rate which i have no time to get them fixed.Then you have 2 options:
1. MAKE time, or:
2. PAY for Windows software and - ahem - support.
**Microsoft support !**
Whahey - I'm sorry, just couldn't resist it - WHAHAHAHAHAHA

As you may have noticed - no, I do not excuse your tone.
Either moderate it or live with the consequences.

---

### Post by kd7swh on 2007-01-01
> 1)WRONG RESOLUTION AFTER SUSPEND HYBERNATE. After either Hibernate or standby the screen resolution which normaly is 1280x768 changes to 1280x1024?? something really ugly and un-usable.I have to reboot, or kill X in order to get it back to normal which really means that i do not have the functionality of either suspend or hibernate something which is killing me. (P.S. i used 915resolution to get the resolution correct in the first place)

This is most likely a problem with your x.conf file. It normally contains screen resolutions after changing it with  915resolution it may not have made it into x.conf (in /etc/X11 I think)

> 2)No matter what i do, i cannot change the power saving timer on the monitor.It just goes back at 5hrs!!!! 

I think this would be a bios problem and not a linux thing.

> 3)NOT READING ALL THE FILES IN NTFS. Now this really pissed me off!! I have an NTFS partition with a MUSIK folder in it. Now the folder contains under MS 3172 files and consumes 11,4 GB.All of which are playable. Linux on the other hand sees that only 2430 files exist at 9GB of space.
IS THERE AN EXPLANATION ABOUT THIS?? Under linux only around half of the files under each folder is readable-seeable. WHY??


I am not sure on this one. I know that NTFS support doesn't come standard with most distros. I think there is a project by the name of ntfs-3g or something like that. This project adds additional NTFS support.

> 4)The FnF3 mute button pops up as it should, a window which say mute on-off. My problem is that as far as i can tell, it mutes the MasterChanel , which is not used and has no affect in the P7010, while it should mute headphones-or PCM channels to actyally MUTE the sound.
HOW can i fix this around?In linux the myth is that you can change everything. HOW can i make FNf3 mute everything and not just the unused Master chanell??\

No idea.

> 5)each time i want to run vmware server after a restart i have to reconfigure it. Something time-consuming and nerve cracking. Any fixes???

This is strange, I have used VMware workstation before and the configuration stuck on that. Maybe the config. file isn't being written to file? Make sure that you have proper permissions.

> 6)Knights chess program crashes in EVERY game. Any syggestions? other progs?

gtkboard or gnome-chess will work.

> 7)How can i find out the temperature of my machine and most important wheather the fan is working correctly or not?

I am sure there are a number of programs for doing this. You may try something like "sensord"

```
I also have a problem with amarok and greek ID3 tags,but i think i can live with that, though a fix would be great 
```

sorry don't know

> 9)Suggest a torrent program.

I use azureus [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)
but ktorrent works too :)

---

### Post by kd7swh on 2007-01-01
adaptr: you bring up some valid points about every users choice of operating system. However, I don't think that your comments are very productive or helpful. One of the sticky posts in this forum asks us not to tell people to google things. If someone is asking for help we have a choice to provide it or not. If we choose to be cynical and withdrawn it detracts from the true spirit of Ubuntu and I would hope that you could find better things to do.

---

### Post by phossal on 2007-01-01
Don't miss xboard for chess, which will download with the unbeatable gnuchess engine if you use:
```

sudo apt-get install xboard

```

Look up xboard on the net, and download the pdf guide for it. It's ultra-configurable, and connects to the free chess servers, like freechess.org (where *masters* play), amazingly well.

---

### Post by WiseElben on 2007-01-01
> 1)WRONG RESOLUTION AFTER SUSPEND HYBERNATE. After either Hibernate or standby the screen resolution which normaly is 1280x768 changes to 1280x1024?? something really ugly and un-usable.I have to reboot, or kill X in order to get it back to normal which really means that i do not have the functionality of either suspend or hibernate something which is killing me. (P.S. i used 915resolution to get the resolution correct in the first place)

You can try editing your xorg.conf file. 

```

#backup your xorg.conf first with this:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

#now to edit:
sudo gedit /etc/X11/xorg.conf

```

Go to the Screen section and add in the resolution you use. under "Modes." You can try taking out the 1280x1024 one so it won't choose it.

---

### Post by usy on 2007-01-01
i am not an expert with linux or ubuntu but i was just wondering if u hav tried ubuntu (gnome version).i use a laptop (althought dell but still a laptop :) ) and i dont hav ny of these pbs.if u havnt then perhaps u shud try gnome.how come u realized these pbs after 3 months or hav u been living with them? :D

---

### Post by escape on 2007-01-01
> **DrSasaroli68 said:**
> ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) 


Lets start
1)WRONG RESOLUTION AFTER SUSPEND HYBERNATE. After either Hibernate or standby the screen resolution which normaly is  1280x768 changes to 1280x1024?? something really ugly and un-usable.I have to reboot, or kill X in order to get it back to normal which really means that i do not have the functionality of either suspend or hibernate something which is killing me. (P.S. i used 915resolution to get the resolution correct in the first place)

Change every instance of 1280x1024 to 1280x768 in /etc/X11/xorg.conf. Do this with 
>sudo nano /etc/X11/xorg.conf
and hit Ctrl+W to search for 1024
> 
2)No matter what i do, i cannot change the power saving timer on the monitor.It just goes back at 5hrs!!!! 

Don't know. How are you trying to change it to begin with? I'm sure it can be fixed.

> 
3)NOT READING ALL THE FILES IN NTFS. Now this really pissed me off!! I have an NTFS partition with a MUSIK folder in it. Now the folder contains under MS 3172 files and consumes 11,4 GB.All of which are playable. Linux on the other hand sees that only 2430 files exist at 9GB of space.
IS THERE AN EXPLANATION ABOUT THIS?? Under linux only around half of the files under each folder is readable-seeable. WHY?? 

The native NTFS stuff isn't that great. Do this: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)
It's a better NTFS driver. I have yet to have problems with it, although I haven't experimented with folders that large as I keep my music on my ubuntu partition.

> 
4)The FnF3 mute button pops up as it should, a window which say mute on-off. My problem is that as far as i can tell, it mutes the MasterChanel , which is not used and has no affect in the P7010, while it should mute headphones-or PCM channels to actyally MUTE the sound.
HOW can i fix this around?In linux the myth is that you can change everything. HOW can i make FNf3 mute everything and not just the unused Master chanell??\

Sorry but I can only give a half-assed answer for this, as I don't know too much here. Hopefully this is a start. The first two do not permit use of the Fn button to mute your machine but may help.
If you have GNOME (not KDE, which I know nothing about):
Easier solution: go to your main menu on the panel -> preferences -> keyboard shortucts. You can map mute here to something (but not an Fn based shortcut). 
Harder solution: Open gconf-editor (using alt+f2 or from a terminal), go to apps/metacity/keybinding_commands. You want "run_command_1" to somehow mute the machine. I'm 100% sure there's a command line way to mute your computer the way you want, I just don't know how. But you would put this command here. Then in /metacity/apps/global keybindings you would put the keyboard shortcut. I tried <Fn> as a modifier but it didn't seem to do anything. 

Alternate solution for beryl: If you are using beryl go to beryl-settings-manager (thru alt+f2 or a terminal) and under the tabs in general options you can make non-Fn shortcuts as well. 
> 
5)each time i want to run vmware server after a restart i have to reconfigure it. Something time-consuming and nerve cracking. Any fixes???
Also don't know but I'm sure there's a way to save settings. Have you searched the forums? Look for a howto.

> 
6)Knights chess program crashes in EVERY game. Any syggestions? other progs?
First try
>sudo apt-get update
>sudo dpkg --purge knights
>sudo apt-get install knights
If it still fails try a much older/stabler version. If you do >man knights you can probably get a URL for the program and find your way to older/more stable  or newer/more stable versions there. Try running knights from a terminal as well to see how it crashes.

7)How can i find out the temperature of my machine and most important wheather the fan is working correctly or not?
Temp should be under /proc/acpi/thermal_zone/THM0/temperature and /proc/acpi/thermal_zone/THM0/state. 
If it's not then maybe try getting lm_sensors or look for a howto for your laptop. I'm on a thinkpad. If that location does work then this might help.  The fan info is also buried in /proc/acpi.  You may want to try just poking around in /proc/acpi/, this is where you'll find what you're looking for.
> 
8)I also have a problem with amarok and greek ID3 tags,but i think i can live with that, though a fix would be great :mrgreen: 
 Derno there.
> 
9)Suggest a torrent program.

If you have java working, just try Azureus. If Azureus is broken, as it is on some, then check out the fix here [http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus](http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus)
Otherwise I recommend uTorrent through wine if you have time, as well as just bittorrent, the builtin super lightweight client. You might also like Apollon (P2P program):
[http://ubuntuforums.org/showthread.php?t=59857&highlight=howto+apollon](http://ubuntuforums.org/showthread.php?t=59857&highlight=howto+apollon)

---

### Post by DrSasaroli68 on 2007-01-01
Thanks to all the great people who used some of their time to help me!!!!
I Did not put this post to start a flame war, so i will not answear to irony.

**I repeat once more that i am but a simple fellow- not a programer or even power user- who stumbled upon ubuntu and got really motivated by all the wonderful declarations and thoughts  which are the "spirit" of ubuntu. I gave an enormous amount of time but i am frustrated, and i cannot spend 5 hours each day searching-trying-modifying just to have a usable computer.
So if ubuntu is really linux for human beeings i ask for your help.(and i really thank all the wonderfull people who already tried to help me!!)
If i cannot USE my computer, i will be FORCED to go back to the well known M$, in order to just do my job.And this will not be a free but a FORCED choice**


To the point:
**general note i am runing KDE**(and in the laptop in question 6.10 edgy)

1)FIXED!!!! YES YES YES a really big thanks to everyone! After toying around with xorg.conf and a few tries it worked!!! PS the suspend-hibernate work ONLY from the klaptop menu and not the KDE native suspend-hibernate which after wake up scramble the screen(things are double as if you are drunk and there is a really bizare black fill everywhere) leaving the only altenative of reboot in order to get things back to normal.
So to sum up if it works one way it is fine with me. 

2)i am quite sure that this is a kubuntu bug. I go to the K-System Settings-Monitor&Display-Power Saving i aquire root access and i change the screen poweroff value from its default 5hours to three minutes.I then press apply or ok.(done both)It works fine for each session but after a reboot, it is back to  5 hours. I really doubth that this is a bios bug a hardware problem.
Any fixes or workarounds?

3)NTFS support: I want to keep it as simple as possibly and i do not need write support.
I just followed the instructions on ubuntuguide for ntfs read only support.
I have to add that at my deskotop i do not have the same problem( kubuntu 6.06 there not edgy the only diference) while the mysik collection over there is much bigger and theoreticly i did the exectly same things.
From what i can get there is a problem with some of the files but i cannot understand why those files in particular. Could it be their name, or a special character in their name?I just can not see them....

5)In order to reconfigure Vmware i have to do each time sudo /usr/bin/vmware-config.pl
so i think that it has all the permisions it needs to save the F*** settings. **Is there a way i can run/load this script aytomaticly at each boot? **(without the need to press all those enter of course!!!!)


AND A NEW PROBLEM: each time KDE starts a dialog saying "Could not find mime type
application/octet-stream" pops up 4!!!! times and it keeps poping up each time i try to access lets say the cdrom or the HD. Really annoying (though i think that it is my fault).
Any ideas what it means- what can be done about it?


I didnot have the time to check-try anything else, but i will so shortly, and reply.
Thanks once more for your time and patience.

---

### Post by DrSasaroli68 on 2007-01-02
HELL BROKE LOOSE!!!!

Updates:
1)Screen resolution:though yesterday everything seemed ok (i also rebooted many times), this morning the sh** just hit the fan once more. Ubuntu could not start X due to the fact that it could not find a usable resolution in it. I had to use the xorg.conf.backup, and then it booted with the well known wrong resolution-after wake up-problem. After a lot of trial an error it SEEMS to be working fine, but i am really curious how long will it last, since everything seemed ok yesterday, but obviously this was not the case

3)Ntfs read. Ok Now this is the most frustrating part.I said to my sefl ok since it doesny work on ntfs, though on my desktop it works fine, lets go into the trouble to use FAT32. I reformated the ntfs partiotion to FAT32 and recopied all the music in it. AFTER ALL THIS TROUBLE i simply cannot mount the FAT32 partition (using the ubuntuguide instructions to the letter).
I can perfectly well mount an NTFS partition but it will not show all the files in  it.(the previous state of the problem.
WHAT IS HAPENING?HELP! I am completely lost.

This is my fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda3
UUID=2e514abe-45a0-49a8-a30d-ad2447e435b0 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda5
UUID=4a110479-573a-4e2a-abcb-d26fdabf9fb2 none swap sw 0 0
/dev/hdc /media/cdrom0 auto user,atime,auto,rw,dev,exec,suid 0 0
/dev/hda1 /media/hda1win ntfs ro,umask=022 0 0
/dev/hda2 /media/BackupFAT32 vfat iocharset-utf8,umask-000 0 0
/dev/hda3 <mount\040point> auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0

and after sudo mount – a i get :
mount: No medium found
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and after dmesg i get “FAT: Unrecognized mount option "iocharset-utf8" or missing value”
among other incomprehensible stuff.


Ps i also tried /dev/hda2 /media/BackupFAT32 vfat umask-0000 0 0 on fstab with the same results.

**UPDATE*** After another hour the line “/dev/hda2 /media/BackupFAT32 vfat auto,user,rw,umask=0 0 0” actually mounts the partion.  But have my troubles come to an end??? NOOOO!!!!**

It reads all the files but it shows ??????? instead of all the greek characters. At least all files are accesible.
The really strange part is that i have no problem reading everything (including greek characters from my usb HD  (also FAT32).

SO PLEASE PEOPLE, Help me on this one...................
[B]
Why can i read everything from the usb but not from th hdd???
Am i mounting correctly the HD?[/B]
I try, i try, i try but i fail...HELP.



APlication/ocet/stream: FIXED! deleting the file in question somewhere in the kde folders worked for my.It is an old and well known bug as it seems.

Vmware Server: In case anyone finds the same problem maybe deleting the not configured file in will help. For the time beeing it seems to be working for me.


Nearly 10 hours of forum searching-google searching triyng and modifiing and i have not gone a really long way solving anything.And it is really frustrating that after all this trouble i cannot access properly my music.FUBAR. Linux for human beeings???????????? Yeah.....

---

### Post by escape on 2007-01-02
It sounds like Linux probably isn't for you. I'm curious as to why you didn't just try NTFS-3G. Also sorry about your screen resolution. Instead of directly modifying the xorg.conf file, maybe it would be better to run >sudo dpkg-reconfigure xserver-xorg

---

### Post by itsmonktastic on 2007-01-02
I'm sorry to hear about your pain with kubuntu.  I only installed ubuntu myself about 3 months ago for the first time, on a laptop too, but i have not had this number of problems (although I believe my standby and hibernate may be broken) everything else has convinced me to stay with GNU/Linux in the future.

As I pointed out, I am still relatively new to these matters (this is my first forum post actually) but I can suggest, if you have methods of temporary backup (a network card, a cable, and a friend will do :) ) then you could reformat your NTFS partition full of music (I'm hoping they're not stored in the same partition as your important windows files) reformat it in ext3, as it is **possible to read and write to the ext geometry in windows** using something called Ext2FSD 

[http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)

That's the link to the project :) good luck!

---

### Post by ethan961 on 2007-01-03
Sorry-duplicate post-see below (Mods, please delete this message as I do not know how to...)

---

### Post by ethan961 on 2007-01-03
I highly recommend you remove Kubuntu and install Ubuntu. It all works out of the box most of the time. When I installed Kubuntu I was always getting crash reports, programs barely run, and the whole thing slowed down. I also noticed you said you were simple user, for which I recommend Gnome/Ubuntu as Gnome is simply... simpler. I have a 7 year old laptop for which everything worked out of the box (with Ubuntu). If you do wipe kubuntu and install Ubuntu, PLEASE do not do anything to make NTFS work or anything to access your music. **It will work automatically.**\\:D/
Sorry to see you in so much pain. I am lucky to get by so easily.
Hope I can help,
Ethan

---

### Post by tlacuache on 2007-01-16
> **DrSasaroli68 said:**
> 
5)each time i want to run vmware server after a restart i have to reconfigure it. Something time-consuming and nerve cracking. Any fixes???


I don't know if this thread is still alive, but I did have a similar problem running vmware workstation. It turns out that for some reason vmware was thinking it needed to be reconfigured, but it really didn't. It knows by checking for the existence of a not_configured file.

Finally what I did was place this in my /etc/rc.local file (anywhere before the exit 0 line), which deletes that file if it exists upon startup:

```
# remove a spuriously generated not_configured file for vmware
if [ -f /etc/vmware/not_configured ]; then
    rm /etc/vmware/not_configured
fi

```

After that I had no problems.

---

