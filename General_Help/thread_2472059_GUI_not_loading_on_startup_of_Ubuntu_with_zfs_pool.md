---
title: "GUI not loading on startup of Ubuntu with zfs pool"
date: 2022-02-16
forum: General Help
---

### Post by andrewcorser on 2022-02-16
(Please allow for my lack of Linux knowledge...)
When powered up, my desktop pc ('boite') loads Ububtu (20.04?) and its pool of 4 zfs NAS drives...however the screen display is blank but for a cursor, which blinks irregularly, and which is unresponsive to keyboard input.  I know Ubuntu has loaded as I can access boite over the network from a Windows 10 laptop (Z1)  using wsl and ssh-ing into boite, and files are still being rsync'ed from Z1 to the pool on boite (I think). 

I have managed (with a little difficulty) to boot from a usb stick, but don't know where to go next with that: I am nervous about re-installing Ubuntu due to the NAS drives (see background below).

Is there a way I can see a record of Ubuntu's loading so that I can identify when and what is stopping the graphics interface from working?

Many thanks.



Background: 
My (wonderful and linux-savy) son has set me up a (sort of server) pc running Ubuntu (20.something, I think).  It is on my home network, and is used as a media server and network attached backup storage (using a zfs pool of 4 drives), and a route to effect cloud backup (with Tresorit) - all part of my attempt to get out from under Google (gmail, drive, photos, maps etc).  I use Windows 10 on my main laptop (let's call it Z1, also on the home network) for most ordinary computing, but as the server pc (let's call it boite) is attached to the TV for display, I use that for streaming video content (Novara Media, BBC iPlayer etc but not the BFI coz they don't support linux...grrr) as well as for playing music.  I can do this directly through the keyboard and mouse attached to boite (but in an awkward place in my small living room), but prefer to do it using  Z1, connected to boite using VNC Viewer via ssh.

We had a small (family-related) problem when I upgraded Ubuntu and it messed up the operation of boite.  (After some persuasion) the boy re-set things up again so most of the previous functionality was again available.  I was left to work on some things, and decided to try and get a beginnings of linux familiarity in order to be able to maintain boite myself, so worked through William Shotts' Linux Command Line.  This gave me the confidence to try (but fail) to add the boite storage as a drive in W10 file management via ssh... I then tried (as boite does make a small amount of noise even when idle) to have boite go to sleep when not in use, and this may be the source of the current impasse - as I recall, I had boite going to sleep ok, but I couldn't wake it up using the VNC Viewer - I don't remember what I had specifically done just before the gui stopped loading.  The VNC Viewer way into boite now doesn't work, although, using wsl from the W10 command line, I can ssh into boite to give me a terminal on Z1.   

The motherboard of boite is an MSI MAG B460M MORTAR and it has not been straightforward changing the boot priority - I have really only managed it by trial and error.  The display card is an &#8203;MSI NVIDIA GEFORCE GT 710.  All of this was working fine previously.

---

### Post by MAFoElffen on 2022-02-16
At that blinking cursor... What happens if you press <Cntrl><Alt><F4> (together at the same time)? That should e the hotkeys to toggle to vtty4, to a command prompt where you can log into that Virtual TTY session...

---

### Post by andrewcorser on 2022-02-16
Thanks MAFoElffen!  That got me the login prompt, and I've logged in: progress!!

...only, sorry, I'm not sure what to do next...!

These are the messages I got when I logged in: [https://andrewcorser.com/NAS/screenshot.jpg](https://andrewcorser.com/NAS/screenshot.jpg)

---

### Post by andrewcorser on 2022-02-17
...a bit more on the log in: (and this was news to me...) when I log in to boite now on Z1 using the ssh, it gives me the same messages etc as I got using the Ctrl-Alt-F4 directly through the keyboard connected to boite.

My next step is how to find out why the gui is not loading...perhaps by setting up a log of the startup processes, and then restarting boite?

---

### Post by MAFoElffen on 2022-02-19
I'm here.

The good news is that you have (unknowingly) confirmed that the kernel is booting successfully, ZFS is starting and mounting successfully... That the graphics layer is not.

From here, you now know that if you rebooted, odds are that you should be able to at least boot back to this point. Because you are installed on ZFS, you have two options from here. (Option two is the easiest and the advantage of "having" ZFS and ZSysy.)

Option #1. Investigate what went wrong, and fix what is there... This could take some time and work by you, guided by me.

Option #2. Restore to an earlier point from a ZFS Snapshot on startup. When you installed ZFS, there was a system called ZSys that, by default has been taking system snapshots every time you did an update... This is turned on by defualt in Ubuntu when we are talking about ZFS. Next time you use apt, look at the  last message from apt fater it finishes, which says something along the line of ZSys adding the snapshot to Grub. The menu item will have dates, and says Restore to such-and-such a date.

Which option would you like to pursue? Option #1, Option #2? (Or what is hiding behind door #3? Just kidding.) Your choice.

---

### Post by andrewcorser on 2022-02-19
Thanks again, MAFoElffen - just learning the conventions of Ubuntu Forums!

From your options, I would prefer #1...although I feel maybe I should try to do #2 to learn what to do if something like this happens again...
...so I did sudo apt list (using ssh into boite on Z1) - couldn't see any messages about sfds/zsys from previous uses of apt - don't know if this helps with restoring a snapshot...
(selected output from sudo apt list:)
[IMG]https://andrewcorser.com/NAS/sudoaptlist.jpg[/IMG]

---

### Post by MAFoElffen on 2022-02-19
Okay... I'll go into Option #2, just as a note to others, and to you as a fail-back option if you decide to restore to later... That way you gain some confidence knowing that you know you can always use that to go back to.

On Option #2, you reboot (boot fresh) and (you didn't say if the system boots from BIOS or EFI) pressing either the spacebar (if booting BIOS) or <ESC> key (if booting UEFI) once the BIOS firmware boot messages end, and before the Linus System starts to boot... So that you get to the Grub2 Boot Menu. With ZFS installed on Ubuntu, the third Grub2 Boot menu will say: "Historyfor Ubuntu 20.04 LTS". Select that option. When that Menu displays, it will show Lines saying "Restore to <date> @ <time>. Select a date and time that you know was when the system was working okay. 

In the next menu, that appears, you will have 4 options:
[LIST]
[*]Revert system only 
[*]Revert system and user data 
[*]Revert system only (recovery mode) 
[*]Revert system and user data (recovery mode) 
[/LIST]

For you and your situation, I would choose the first menu item... It will take a while to restore those files and then it will boot to that previous state.

Okay... Now to describe what to do for Option #1...

If you take pictures of the output to the following, please post them as attachments to a post. It would be better to redirect output to a file, were you can transport to another computer if that file was on a USB Flash drive, that you can take to the computer you are posting from. To do that do this:
```

lsblk

```
In the output, look to see which device is your Flash drive... Then when you are doing the commands below, append the command with a space then redirect it to the device name, directory and filename, for an example, I will do a command to screen in the first command, then the same command redirecting it to a file on device '/dev/sdb1' so you can see how that is done:
```

sudo lshw -C video
sudo lshw -C video >> /dev/sdb1/output.txt

```
See how easy that is? Then you can open the file on the computer that you are posting from, and paste the output within CODE Tags, in a post.

Ready?

At the console prompt from the tty (after logging in):
```

sudo lshw -C video
dmesg | grep -i 'error\|warning'
[ -f /var/log/Xorg.0.log ] && echo "Xorg Log exists. Using XServer." || echo "Xorg Log does not exist. May be using Wayland."
sudo egrep -i 'xsession=' /var/lib/AccountsService/users/$USER
sudo egrep -i "wayland" /etc/gdm3/custom.conf

```

---

### Post by MAFoElffen on 2022-02-19
Dang. LOL. I forgot ask if the Black screen was before the Graphical login screen, or between that screen and the Desktop...

---

### Post by andrewcorser on 2022-02-20
GRRRR!!!  I just spent 2 hours writing a 'Quick Reply' and then it got lost **** **** ****

---

### Post by andrewcorser on 2022-02-20
[FONT=Times New Roman]OK.  Breathe deeply...start again.[/FONT]
 
 
 [FONT=Times New Roman]***Dang. LOL. I forgot ask if the Black screen was before the Graphical login screen, or between that screen and the Desktop... [/FONT] 
 
 
 [FONT=Times New Roman]Not sure quite what the question is ... but:[/FONT]
 
 
 [FONT=Times New Roman]On startup I get the following (timings approx)[/FONT]
 [FONT=Times New Roman]- Turn on; TV reports Wide...then 720p wide on black screen…[/FONT]
 [FONT=Times New Roman]- then after a bit there is a very brief (less than 1 second) splash screen with the boot options: ‘Press Del to enter BIOS setup, or F11 to run BOOT menu; press ctrl-F5 to to activate M-Flash for BIOS update.’; black screen[/FONT]
 [FONT=Times New Roman]- then splash screen for a few seconds; black screen[/FONT]
 [FONT=Times New Roman]- then splash screen with ubuntu and logo at bottom with timer spinning[/FONT]
 [FONT=Times New Roman]- black screen with irregularly flashing cursor[/FONT]
 
 
 [FONT=Times New Roman]Using Esc on startup:[/FONT]
 [FONT=Times New Roman]- grub> command line prompt under GNU GRUB version 2.04[/FONT]
 
 
 [FONT=Times New Roman]Using F11 (with usb boot stick plugged in) on startup gives a small garbled menu, which I can just about interpret to say:[/FONT]
 
 
 [FONT=Times New Roman]>Ubuntu on Seagate BarraCuda SSD [/FONT] 
 [FONT=Times New Roman]>Verbatim USB partition 1[/FONT]
 [FONT=Times New Roman]>Return to setup[/FONT]
 
 
 [FONT=Times New Roman]If I choose the USB that takes me to a boot menu:[/FONT]
 
 
 [FONT=Times New Roman]Ubuntu[/FONT]
 [FONT=Times New Roman]Ubuntu (safe graphics)[/FONT]
 [FONT=Times New Roman]OEM Install (for manufacturers)[/FONT]
 [FONT=Times New Roman]Boot from next volume[/FONT]
 [FONT=Times New Roman]UEFI Firmware Settings[/FONT]
 
 
 [FONT=Times New Roman]Choosing Ubuntu gets the machine to boot from the usb.[/FONT]
 
 
 [FONT=Times New Roman]Pressing Del on startup gets me into the so-called BIOS screen:[/FONT]
 [IMG]https://andrewcorser.com/NAS/BIOSscreen.jpg[/IMG] 

I will post this and then continue...

---

### Post by MAFoElffen on 2022-02-20
Your pain is real. I personally have done that too many times. 

If I know it is going to be a long post. I write it in a text editor, so I don't accidentally lose it. So I can later cut and paste it into a post. In fact, I have had this one temporary file called "response.txt" that is about 3 years old. (LMAO) 

The only thing temporary about it is the contents of it is ever changing.

So, as I read this, the freeze or lockup, where it has a black screen is between the Grub Boot Menu (the machine boots the kernel, activates ZFS) then freezes the graphics right before the Graphical Login, where it would have you choose a User, and enter your password, which for a default installation of Ubuntu, would be GDM3.

EDIT:
I just got a call from work, they asked me if I can come in early tonight. So I have about an hour before I have to leave.

---

### Post by andrewcorser on 2022-02-20
[SIZE=2] [FONT=Times New Roman, serif]So…[/FONT]
[/SIZE]
[SIZE=2] [/SIZE][SIZE=2][FONT=Times New Roman, serif]Option #2.  As mentioned above, Esc key on startup gets me to the grub> command line prompt.  I can’t see how to get to any menu from this.  The menus I can get to are the graphical ‘BIOS’ screen through the Del key on startup; (incidentally, that graphical BIOS screen doesn’t seem fully functional...or maybe I am expecting too much of it; anyway, e.g. if I move around the boot priority icons, I can’t get it to save the sequence, and it hangs.   Don’t know if this is symptomatic of a hardware problem – or of a lack of understanding by the user problem) …

[/FONT][/SIZE]

[SIZE=2] [/SIZE][SIZE=2][FONT=Times New Roman, serif]...and the boot menus through F11. 

So I can't find any opportunity to roll back to an earlier snapshot yet...

OK.  Now I will look at Option #1...
[/FONT] [/SIZE]

---

### Post by andrewcorser on 2022-02-20
Thanks MAFoElffen: using off-line text editor and 'Go Advanced' for everything (except this Quick Reply) now!!

---

### Post by MAFoElffen on 2022-02-20
Can you please post a picture of your system's Grub2 Boot menu?

EDIT: Oh Dang... To a commandline "Grub > _" Prompt?

Just in case it is taking too much input to cause that, at that point, [s]what happens if from that prompt, you enter[/s]
```

[s]exit[/s]    # Doing this at the Grub prompt, if it went there by mistake, will continue the boot process..

```
BRB. Gong to reboot and try to recreate that...

EDIT2:
Okay, at that prompt, try pressing the <Esc> key to backup and try to show the main Grub2 boot menu.

---

### Post by andrewcorser on 2022-02-20
***EDIT2:
Okay, at that prompt, try pressing the <Esc> key to backup and try to show the main Grub2 boot menu.

Pressing the <Esc> key at the grub> prompt returns a linefeed to another grub> prompt on the next line...

---

### Post by MAFoElffen on 2022-02-20
Okay... Let's get back to post #7... Normal boot until your system gets to the black screen (on graphics), then toggling over to another vtty...

Did you try those commands?

EDIT: Do not worry about rolling back snapshots yet. Since you can log into the console, there are still alternate ways from the commandline to rollback to a ZFS SnapShot, if need be.

---

### Post by andrewcorser on 2022-02-20
[FONT=Times New Roman, serif]***Okay... Let's get back to post #7... Normal boot until your system gets  to the black screen (on graphics), then toggling over to another vtty...

Did you try those commands?



Yes...Option #1.  I have managed to do the lsblk command to identify the usb stick: (presumably) the partition is sde1 and the disk is sde (see screenshot below)

so following your example for redirecting the output of lshw, I typed [FONT=Lucida Console, monospace][SIZE=2]sudo lshw -C video >> /dev/sde1/output.txt[/SIZE][/FONT][SIZE=3] ; 

the response was [/SIZE][FONT=Lucida Console, monospace][SIZE=2]-bash: /dev/sde1/output.txt: Not a directory[/SIZE][/FONT][SIZE=3]. 

[/SIZE][SIZE=3]
So I tried [/SIZE][FONT=Lucida Console, monospace][SIZE=2]sudo lshw -C video >> /dev/sde1/[/SIZE][/FONT][SIZE=3]; 

the response was [/SIZE][FONT=Lucida Console, monospace][SIZE=2]-bash: /dev/sde1/: [/SIZE][/FONT][FONT=Lucida Console, monospace][SIZE=2]Is[/SIZE][/FONT][FONT=Lucida Console, monospace][SIZE=2] a directory[/SIZE][/FONT][SIZE=3].[/SIZE][/FONT]

 [FONT=Times New Roman, serif][SIZE=3]

I have tried to interpret this without success!!!  Here is the screenshot:

[IMG]https://andrewcorser.com/NAS/lsblk.jpg[/IMG]

Something to do with mounting the usb drive?  (I don't really understand the 'mounting' thing in Linux: a long time Windows user, I'm afraid...)
[/SIZE][/FONT]

---

### Post by andrewcorser on 2022-02-20
BTW, thanks again for all of this help, MAFoElffen - it is really much appreciated!!

Andrew

---

### Post by MAFoElffen on 2022-02-20
I'll have to continue when I get back from work. Have to leave now...

Could you please try go back edit that last post and attach those photo's as attachments? Not all users have good graphics.

To guess, I would say that it might be a problem with an NVidia graphics driver, and for you to try to boot, with adding a 'nomodeset' boot parameter added to your Grub2 Menu boot line, but do you ever see that Menu on boot?

I can tell you how to 'force it' to show...

---

### Post by andrewcorser on 2022-02-20
All good.  I have to go to bed, anyway (11 pm in the UK...).  I will try and attach the jpg's.

---

### Post by andrewcorser on 2022-02-21
[FONT=Times New Roman, serif][SIZE=3]Good Morning MAFoElffen!

Boot update.

[/SIZE][/FONT]

 [FONT=Times New Roman, serif][SIZE=3]I looked up ‘[/SIZE][SIZE=3]G[/SIZE][SIZE=3]rub2 menu boot line’, and got ‘How to get the Grub menu at boot-[/SIZE][SIZE=3]t[/SIZE][SIZE=3]ime’.  

[/SIZE][SIZE=3]This led me into editing [/SIZE][SIZE=3]etc/default/grub (...I did save a backup…): I made 

GRUB_HIDDEN_TIMEOUT=0 into a comment by prefixing the line with #; 

and I changed [/SIZE][SIZE=3]GRUB_TIMEOUT_STYLE to =menu.[/SIZE][/FONT]

 [FONT=Times New Roman, serif][SIZE=3]
This got me the following menus (which don’t seem to be the Grub2 boot menus you were looking for in Post #7):

[ATTACH=CONFIG]290079[/ATTACH]



[PS I have tried attaching these jpg's, but couldn't get it to upload my attachments.  I have raised my difficulty in another part of the (Ubuntu Forums) forest]
[/SIZE][/FONT]

---

### Post by MAFoElffen on 2022-02-23
The permissions on the write, was because the USB thumb drive should have been mounted first...
```

sudo mkidr /media/flashdrive
sudo mount /dev/sde1 /media/flashdrive

#example to see if you can write to it ...
sudo lsblk [COLOR=#ff0000]>> /media/flashdrive/results.txt[/COLOR]
# etc...

# When through doing what you need to do, to close down the filesystem and such for it to be safely removed, 
# remember to unmount the drive before you pull it out.
sudo umount /media/thumbdrive

```

You say this is on ZFS right? I don't understand why the ZSys snapshot menu did not integrate into the Grub Boot Menu(???) What version of Ubuntu was this installed with and by what method? No matters.

What happens if you do(?)
```

zfs list
zpool list
mount | grep zfs
apt-policy zsys
zfs list -t snapshot
zfs get creation
zsysctl service dump

```
This output is important to you, as... the first two commands will show the ZFS filesystems and pools within the ZFS filesystem,as well as information about them. The third command will show you how those ZFS filesystems are mounted into the main structure of the filesystem... The fourth will show if ZSys is installed and what version of.
The 4th & 5th commands will show the snaphots and when they were created. The last will show us how ZSys views the world and when those were last accessed.

Then reboot your computer, in your Grub menu, at the first menu option, the the <E> key. Arrow down to the line that starts with the word 'linux'. Take a picture of that to post... Or you could try this first, before you did the above commands, to that is you get a Desktop Going, that you can cut and paste the output from a graphical terminal session to a browser. That would make this all a lot easier for you... 

Arrow right just after the word "splash", and add the work "nomodeset". Press <Cntrl><X> together and let it try to boot. If it does boot, select "Activities" > Start typing "Software & Updates". Select the "Software and Updates" Icon. In the "Additional Drivers" Tab... Try a different NVidia Graphics driver.

If that works,I feel there will be just a bit more to do... To see why and repair the Grub Menu, so that the ZSys snapshot menu is integrate back into your Grub Boot Menu as it should be...

And then... Please keep these commands somewhere 'safe' and handy for reference for later.. You will need them  for 'maintenance' later."ZFS-on-root" is stiil considered as  being a bit in the "Expermental" stage... although I've used ZFS since 2006... So what, 24 years? What isn't worked out yet for ZSys is the automated purging of snapshots as time goes on.

If you have done Ubuntu or Linux for a while... You probably know that if you used a separate  /boot partition, that after a few years it ran out of room from all the kernel boot images that were collected there. You used to have to manually purge the old ones to make room. Current, and there is an automated maintenance routine, that says, if you update a kernel, if you have more than 3 kernel versions, purge the older versions... 

ZSys makes a snapshot each time apt runs, and once a day. This is an incredibly powerful and useful tool, to be able to roll-back a problem if need be. But... There are no defaults set yet to purge any older snapshots yet. So by default it just collects. After a while the bpool snapshots will fill the boot pool's limited space, and you will have to tell to manually purge some of the older snapshots. How they will do this... They have a utility that will purge the last over 20 snapshots... 
```

zsysctl service gc -a

```
The 'gc' stands for garbage collection... But does nothing if you don't have this many. It's configuration options are 'set' at the time of compile. The Dev's say they have a plan to set a systemd timer to do this, which will be added later... I guess they have set that timer now. They were wary, because this affects "data" on production systems... They have not discussed how this affects Desktops... Because on "my long-range tests" on a Desktop... It takes a lot less than 20 kernel updates to fill the default bpool's /boot partition  size set in the Desktop installer... So the User is left to manually purge snapshots to free up size. Because at about 20% unused left in pool, ZSys will stop making snapshots and then (later) you will start getting update errors on kernel updates...'zysctl' now does have an external configuration overload file (/etc/zsys.conf), where Admins can set the options can be modified manually, such as for the limit of snapshots that it purges at. That file is not  exist there by default. Currently it takes about 18 updates for that to be full in a Desktop. It would be a good ide to create that file and set the number from 16-17 snapshots, instead of 20. 
 
So yes, before we are through fixing things,I'll share some those manual kinds of things with you so you are prepared for those when and what if's.

---

### Post by andrewcorser on 2022-02-24
(I am going to have a nervous breakdown soon...I don’t seem to be able to get past the first two lines of your instructions, MAFoElffen, before I encounter another example of my inadequacies in Linux…]

 
 
 These were your instructions:

 
 
 ‘[SIZE=3]The permissions on the write, was because the USB thumb drive should have been mounted first...[/SIZE]
 Code:
 sudo mkidr /media/flashdrive
sudo mount /dev/sde1 /media/flashdrive

#example to see if you can write to it ...
sudo lsblk [COLOR=#ff0000]>> /media/flashdrive/results.txt[/COLOR]
# etc...’ 



OK. But the response to     


 [FONT=Times New Roman][SIZE=3]    lsblk [/SIZE][COLOR=#ff0000][SIZE=3]>> /media/flashdrive/results.txt[/SIZE][/COLOR][/FONT]

 [COLOR=#000000][FONT=Times New Roman][SIZE=3]
was[/SIZE][/FONT][/COLOR]

 [FONT=Times New Roman][COLOR=#000000][SIZE=3]    
-[/SIZE][/COLOR][COLOR=#000000][SIZE=3]bash: /media/flashdrive/results.txt: Permission denied[/SIZE][/COLOR][/FONT] 

 
 
 So, I spent most of the day (in between hearing all about the start of World War III – it is 9.30 pm here now) trying to work our why permission was denied.

 I did chmod 777 on /media/, and on /media/flashdrive/, and on /media/flashdrive/results.txt (it took me some time to work all this out from my very low level understanding of linux that I explained at the beginning of this thread) such that they all have rwxrwxrwx (that seemed like the easiest way to do it for me).


 But as soon as I mount the directory onto the usb stick, the permissions go to rwxr-xr-x, which is presumably why I can’t write to the file.  And I have used both sudo, and going in as su (which made me very anxious, given my low level of linux knowledge) to try using chmod 777, without success.


 Help!!!  (And this is just to get a record of what is going wrong...we haven't really started to address that yet...)

 
**********************************************************************************************

I did start to have a look at what comes next.  First off, here is lsblk:

 
[IMG]https://andrewcorser.com/NAS/lsblk2.jpg[/IMG]

  
 
 So, at this point, zfs is not mounted (?) - because the pool is on sda, sdb, sdc and sdd.

 
 
 I just checked back to see that my files that were in the zfs pool (and that I had been able to see using the ssh into Boite, at the start of this thread) were still there...but no!  The directory that they were on is still there, but it is empty….
 ….now this could be because Ubuntu is loading slightly differently now, after all the things we have done in the last multiple days, and I hope it is…
 
 
 So, the return from  

     
zfs lis[FONT=Times New Roman][COLOR=#000000][SIZE=3]t [/SIZE][/COLOR][/FONT] 

 [FONT=Times New Roman][COLOR=#000000][SIZE=3]
is [/SIZE][/COLOR][/FONT] 

 [FONT=Times New Roman][COLOR=#000000][SIZE=3]    
no datasets available[/SIZE][/COLOR][/FONT]

 
 
 [FONT=Times New Roman][COLOR=#000000][SIZE=3]And, not surprisingly, the response to [/SIZE][/COLOR][/FONT] 

 [FONT=Times New Roman][COLOR=#000000][SIZE=3]    
zpool list[/SIZE][/COLOR][/FONT]

 [FONT=Times New Roman][COLOR=#000000][SIZE=3]
is[/SIZE][/COLOR][/FONT]

 [FONT=Times New Roman][COLOR=#000000][SIZE=3]    [/SIZE][/COLOR][COLOR=#000000][SIZE=3]
no pools available[/SIZE][/COLOR][/FONT]

---

### Post by TheFu on 2022-02-24
>  (Please allow for my lack of Linux knowledge...)

That statement has me saying "don't use ZFS!"
It isn't ready for you.  There will be issues.  As someone new to Linux, you should stay away from ZFS, BRTFS, and LVM ... for now.
Stick with straight ext4 file systems on partitions for at least the first 6 months as you learn more and more about Linux and storage management.

After 6 months of daily use, perhaps then you can add one of those advanced volume managers for a data disk, not the OS.

Of course, if you like to break things and that's how you learn and data loss isn't a problem for you and a non-working computer, go crazy. Do whatever you like.

I tried ZFS for my first 20.04 install as the OS file system.  Things were just wrong. The system was slow.  After 30 minutes, I flushed the system and reinstalled using LVM+ext4.  Aaaaah.  All was right in the world again.  I only have 25 yrs as a Unix/Linux admin, programmer and systems architect.  Yet, ZFS used for Linux storage on the OS scares me.

---

### Post by andrewcorser on 2022-02-24
[The  Fu]("https://ubuntuforums.org/member.php?u=1037685"), if you read the first post in this thread, you will see how I got to where I am...
...and to be fair, I am supremely confident that, even if the wonderful people on Ubuntu Forum can't help me, my son will eventually return to the family home and sort it all out for me!! It is, after all, his design, and he is not a newcomer to Linux...

...however, I would really like to be able to sort it out for myself, with appropriate help.

---

### Post by MAFoElffen on 2022-02-24
I can post the instructions to mount ZFS manually... But let's back up a bit.

I thought you said when you let the system boot on it's own, got to where it had a black screen, pressed <Cntrl><Alt><F4> to toggle over to tty4... Logged in... Thateverything was there and fine, except that the graphics were not working.

If it booted the core system, it had to have ZFS pools activated, or it would haver never found bpool, where the system's /boot is mounted. That is my logic on that.

But you also posted picture of your Grub2 Boot screen, where there is no trace of ZSys integration at all in that. Most times, when I see that, that is on machines where there are multiple installations of Ubuntu, and whatever was installed last, is the version of the Grub2 boot menu...

So if, you are boot as normal, successfully, and into tty4, and it says you have no ZFS or ZPools activated(?). It's either a miracle, or you booted different instance of Linux without ZFS.

Here is what I need you to do... Download the Ubuntu 20.04.3 iso. Create a USB LiveCD. Boot from it, and use Try. Open a browser to get back to here to read the instructions... open a terminal
```

sudo add-apt-repository ppa:yannubuntu/boot-repair-dev
sudo apt-get update
sudo apt install -y boot-info
boot-info

```
Let it run. Use Advanced and upload the results to a pastebin. Copy and paste the pastebin URL in a post so we can see what is going on and what it see's.

Yes, that is a DEV version of that, where I am contributing with how I do things, and we are getting that to work with ZFS and LUKS... Do not use any 'repair' from that, it's not ready yet...

---

### Post by andrewcorser on 2022-03-01
Hi MAFoElffen...
...did you get my message with boot-info url?

Andrew

---

### Post by #&amp;thj^% on 2022-03-01
> **andrewcorser said:**
> Hi MAFoElffen...
...did you get my message with boot-info url?

Andrew
To save you and MAFoElffen time, and to quote " Copy and paste the pastebin URL in a post so we can see what is going on and what it see's."
So when he returns he'll have that url here. You can edit your last post and include the url there.
Good Luck

---

### Post by andrewcorser on 2022-03-02
[1fallen]("https://ubuntuforums.org/member.php?u=2040855")
Not sure about putting boot-info on public post..?

---

### Post by #&amp;thj^% on 2022-03-02
> **andrewcorser said:**
> 
Not sure about putting boot-info on public post..?

Why??? you come for help but resist at every turn.
I wish you well and good luck.
A link to paste bin: [https://pastebin.ubuntu.com/](https://pastebin.ubuntu.com/)

---

### Post by andrewcorser on 2022-03-02
> **1fallen said:**
> Why??? you come for help but resist at every turn.
I wish you well and good luck.
A link to paste bin: [https://pastebin.ubuntu.com/](https://pastebin.ubuntu.com/)

I'm sorry that you see my caution as resistance: it is not that.  I am cautious because I do not know how the details from the boot-info might be used - clearly not by those trying to help, but by others who may have a different agenda.  I am new to this operating system, and if I do not understand something I think it is only sensible to maintain my security as well as I can: I have therefore sent the link to the person who has offered to help.

If you are implying that the Ubuntu community is not prepared to help people new to using Ubuntu, then perhaps I have chosen this os badly.  However, I do not believe that to be the case.

---

### Post by #&amp;thj^% on 2022-03-02
> **andrewcorser said:**
> 
If you are implying that the Ubuntu community is not prepared to help people new to using Ubuntu, then perhaps I have chosen this os badly.  However, I do not believe that to be the case.

You believe Right, we are here to help, also I understand your caution but we here can not help without the needed info.
If you sent MAFoElffen a link in a PM then you rob all here of aiding.
BTW privacy is a fairy tail now days, and there is the fact we have a very professional grade of staff members here that won't allow any form of misdeeds here.
And after you have found an answer to your problem (if any) you can re-edit your thread and simply remove the url>>>>easypeasy.

---

### Post by andrewcorser on 2022-03-02
OK, 1fallen, I will take you at your word (especially since you quote the Dalai Lama - your karma awaits you!)...

...here is the link: [https://paste.ubuntu.com/p/dYVrnsvM2B/](https://paste.ubuntu.com/p/dYVrnsvM2B/)

---

### Post by #&amp;thj^% on 2022-03-02
> **andrewcorser said:**
> OK, 1fallen, I will take you at your word **_(especially since you quote the Dalai Lama - your karma awaits you!)..._**


I can only hope and wait.:popcorn:
You now have a wider audience here. best wish's :)
EDIT: I never feel good when motivated by harm.

---

### Post by andrewcorser on 2022-03-22
I have found the command 

journalctl -b

which, I think, is a log of the startup process, which is what I asked for at the beginning of this thread.  As you will no doubt know, this is a very long file.

At line 2420, in yellow, it says 'fatal server error' on a line /usr/lib/gdm3/gdm-x-session[1077]:      which looks like the display system..?

I will post an image directly of the start of the journal, and the lines later on where I think the display fails (see link, below rant)...
[I]
[[[...well, I would post the image if Ubuntu Forums wouldn't, yet again, give me a null return, tell me I don't have the permissions to do what I am trying to do, and then log me out without having uploaded my image, nor saved my changes in the 'advanced' editor...OK.  100 Kb only...!!!]]]

...[https://andrewcorser.com/NAS/journalctl-b.jpg](https://andrewcorser.com/NAS/journalctl-b.jpg)


ACTUALLY, I THINK IT IS TIME TO BREAK THIS OFF INTO A [NEW POST]("https://ubuntuforums.org/showthread.php?t=2473062&p=14087020#post14087020")...
[/I]

---

