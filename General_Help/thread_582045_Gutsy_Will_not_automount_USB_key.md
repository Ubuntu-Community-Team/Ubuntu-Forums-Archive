---
title: "Gutsy: Will not automount USB key"
date: 2007-10-19
forum: General Help
---

### Post by geehumshriber on 2007-10-19
In 7.10, when ever we plug in a USB key, it won't auto mount. It auto mounts my DVD drive as though it were a USB drive, and you can take out and put in CD's without problems, but it won't work for USB drives. The only time that it works is when I boot with a USB key already plugged in.

Thanks!

G

---

### Post by Dow Franklin Dudley on 2007-10-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had a similar problem with my usb key and an  external disk drive. I found a solution at the very end of the thread posted by Dan Lenski here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025)

"Go into gconf-editor and navigate to /system/storage/default_options/vfat/mount_options, and then remove the "usefree" option from the list. Exit gconf-editor, and try hotplugging your drive again. It works :-)"

I tried it and, indeed, it worked.

Hope this helps; good luck.

---

### Post by amr2205 on 2007-10-20
> **Dow Franklin Dudley said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had a similar problem with my usb key and an  external disk drive. I found a solution at the very end of the thread posted by Dan Lenski here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025)

"Go into gconf-editor and navigate to /system/storage/default_options/vfat/mount_options, and then remove the "usefree" option from the list. Exit gconf-editor, and try hotplugging your drive again. It works :-)"

I tried it and, indeed, it worked.

Hope this helps; good luck.

Ohhh! it works for me too! Thanks!
:popcorn:

---

### Post by Tanker Bob on 2007-10-27
What's the equivalent process to fix this in Kubuntu? gconf only applies to the gnome desktop.

---

### Post by LoCusF on 2007-10-28
> What's the equivalent process to fix this in Kubuntu? gconf only applies to the gnome desktop.

Hey,

It can be done via Dolphin file browser, just replug the usb-key and it will be displayed in Dolphin. Now go to "Storage Media" in Bookmarks and right-click the usb-key icon -> Properties -> Mount automatically.

Cheers,
LoCusF

---

### Post by Tanker Bob on 2007-10-28
Thank you for your reply. I did this, but it forgets after the next reboot. I have to use Dolphin to mount USB removable media after every reboot.

---

### Post by cwalte on 2007-10-29
It didn't work for me! Is there a specific version of Gnome(*12, 14 or 16) that should be used. Nothing happens and yes I've rebooted...

---

### Post by jarvis13 on 2007-10-30
Nothing will automount for me via USB: USB Keys, iPod etc.
Have been dealing with this issue since the week Gutsy came out. Worked in Feisty. Works in OpenSuSE....
HP dv6110us

---

### Post by Tanker Bob on 2007-10-30
I have a more detailed post on my experimentation with this [here](http://ubuntuforums.org/showthread.php?p=3660810), which includes dmesg outputs after connecting devices that automount and those that do not automount. It may help to see if others are getting the same outputs.

---

### Post by chejrw on 2007-10-30
I removed the 'usefree' option, but my USB drives still do not automount.  Any furthur suggestions are appreciated.

---

### Post by agent-s on 2007-10-30
i looked in dolphin and nothing shows up in storage media..???

---

### Post by Tanker Bob on 2007-10-30
> **agent-s said:**
> i looked in dolphin and nothing shows up in storage media..???
There was a solution suggested in the thread that I linked above. I haven't tried it yet.

---

### Post by KevLeviathan on 2007-10-31
This worked.... kind of.
First I removed "usefree". It did nothing.
So I rebooted and my usb devices still wouldn't hot plug. So I put "usefree" back in, and rebooted once more.
Now my devices all work fine! So it seems that you need to remove it, reboot, put it back and reboot again.
Strange but... worked for me.

---

### Post by 4Jazz on 2007-11-01
Only my 2nd post, how do get into gconfig-editor I haven't located it yet

---

### Post by mikeize on 2007-11-01
applications>accessories>terminal

type:  gconf-editor


-mike

---

### Post by G4HZA on 2007-11-03
None of the solutions have not worked for me so I've given up and I'm going back to Feisty.  I cannot do without downloading from my camera and gps any longer.  It would be ok if I could manually mount but even that does not work.
It is a shame that this bug has been allowed to continue for so long as it must be affecting a lot of people and I cannot understand why it has not been properly resolved long before now with a clear concise description of how to get it working.
Roger

---

### Post by fausto1980 on 2007-11-04
The Dan Lenski solution worked for me by removing the USB usefree option.  Now it works great!  Thank You! :)

---

### Post by Tanker Bob on 2007-11-04
Anybody know where that option would be in KDE?

---

### Post by aristotlewilde on 2007-11-07
I am having a similar issue.  Everything mounts for me, but I cannot write to or delete files from my USB key.  It says I do not have permission.  Anyone know how to fix this aspect?

---

### Post by TheBigBentley on 2007-11-08
I used a program called pysdm to mount my usb drives. It also fixed the problem I had with mounting my second internal HD. Simply selected the drive in the program and used the option "default". Then clicked mount. Worked great and now all my drives work fine.
heres the link
[http://sourceforge.net/project/shownotes.php?release_id=416726&group_id=142700](http://sourceforge.net/project/shownotes.php?release_id=416726&group_id=142700)

---

### Post by Endolith on 2007-11-09
What does "usefree" mean?  Since some people report success with it turned on and some with it turned off, is this just affecting something else indirectly?

---

### Post by eumetaxas on 2007-11-10
None of the recommended solutions worked for me.
I t seems that there's a** wider problem with usb devices from 7.04 and then. **Everything was ok in 6.10. In 7.04 there was a problem with unmounting usb hard disks (there's a big thread on this) and i personally i still have this problem, and now with usb sticks. i do not mind mount or mount manually  - through terminal- this is not the point. Something that used to work fine  does not anymore.
**I'm not quitting ubuntu** & linux in general anymore  - but some others might.
Hope there'll be a solution soon.

---

### Post by Endolith on 2007-11-10
> **eumetaxas said:**
> I t seems that there's a[B] wider problem with usb devices from 7.06 and then.

My problems have been happening since the upgrade to Feisty, too, before which everything auto-mounted fine.  Do yours involve only FAT partitions?

> i do not mind mount or mount manually  - through terminal- this is not the point. Something that used to work fine  does not anymore.

Exactly.

---

### Post by eumetaxas on 2007-11-11
with feisty the problem was unmounting external hard disk - both ntfs & fat. Now includes mounting the external drive,  usb sticks & my card reader

---

### Post by njwiley on 2007-11-13
For those who happen to be running VMware, I found that my virtual machine was grabbing the USB drive and preventing my host (Ubuntu) from automounting.  Simply uncheck the USB drive in VMware Console (VM>Removable Devices>USB Devices).  Something to check if you're having trouble with USB automount.

---

### Post by fjgaude on 2007-11-13
> **njwiley said:**
> For those who happen to be running VMware, I found that my virtual machine was grabbing the USB drive and preventing my host (Ubuntu) from automounting.  Simply uncheck the USB drive in VMware Console (VM>Removable Devices>USB Devices).  Something to check if you're having trouble with USB automount.

Thanks for the info... so much to learn these days, what with virtualization.

---

### Post by Tanker Bob on 2007-11-13
> **njwiley said:**
> For those who happen to be running VMware, I found that my virtual machine was grabbing the USB drive and preventing my host (Ubuntu) from automounting.  Simply uncheck the USB drive in VMware Console (VM>Removable Devices>USB Devices).  Something to check if you're having trouble with USB automount.
I'm having the opposite problem. My Dell PPC PDA is no longer picked up in my virtual machine. It worked fine in Feisty. This will be a deal killer if I can't get gutsy to offer it up to my virtual machine. lsusb shows it in the list, just like all the stuff that doesn't mount or automount.

---

### Post by eumetaxas on 2007-11-14
Do people with did clean install of ubuntu gutsy having the same problems? and if not is there a way to reinstall this modules without formatting?

---

### Post by Tanker Bob on 2007-11-14
I did two clean installs. I also later reinstalled the hal and mounting modules, but it made no difference.

---

### Post by eumetaxas on 2007-11-15
I do not how, by i fixed my automount issue! Playing around i tried to install the newer version of gnome-mount(0.7), i had installed 0.6. 
The ./configure from the source files asked to install various packages(libraries) during configuration. I had almost all of them installed but not the -dev part of them. step by step i installed them. The ./configure finally ended successfully. The "make" command ended with erros and i gave up. But after that the automounting of my usb sticks was working again!! So i guess some libraries are missing because i only installed some files. Hope the ubuntu experts find out a more proper solution!

---

### Post by Jeff_From_VA on 2007-11-15
> **eumetaxas said:**
> I do not how, by i fixed my automount issue! Playing around i tried to install the newer version of gnome-mount(0.7), i had installed 0.6. 
The ./configure from the source files asked to install various packages(libraries) during configuration. I had almost all of them installed but not the -dev part of them. step by step i installed them. The ./configure finally ended successfully. The "make" command ended with erros and i gave up. But after that the automounting of my usb sticks was working again!! So i guess some libraries are missing because i only installed some files. Hope the ubuntu experts find out a more proper solution!

Could you list what all you installed - I just noticed my USB is no longer automounting.... 

 I am starting to regret the "upgrade" to gutsy - Feisty was working well, should have left well enough alone....

---

### Post by Tanker Bob on 2007-11-15
Ditto. My feisty worked great but gutsy has been a hassle since day one. If I cannot get my PPC PDA to be passed to my WinXP virtual machine like feisty did, I'll have to go back to feisty.

---

### Post by eumetaxas on 2007-11-16
1. I found the source files of gnome-mount 0.7 while surfing around. i guess this is easy to do. the ./configure command said that various files where missing. then through synaptic found them and installed. i cannot recall all of them but i remember gconf-2.0, eel and some others. Sorry i cannot remember more. If you tell me a way to find the history i'll post back.
2. my windows pda was working fine with synce & multisync

---

### Post by Endolith on 2007-11-16
I tried reinstalling, completely removing and reinstalling, and dpkg reconfiguring gnome-mount and gnome-volume-manager, but my partitions still don't automount.

---

### Post by eumetaxas on 2007-11-16
which gnome-mount? i had 0.6 in the repositories not 0.7 that i tried to install

---

### Post by Tanker Bob on 2007-11-17
Well, I found that pmount and its support library were not installed. I installed these in Kubuntu, restarted the system, and now my PDA is recognized again in the virtual machine. USB flash sticks are still non-starters for autoloading. The hal bug in launchpad [here](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/102097) is marked confirmed, but the importance is undetermined and it is unassigned. I take that to mean that it is being ignored.

---

### Post by flick on 2007-11-22
What worked for me :

sudo apt-get install usbmount

a reboot

Logged back in, stuck my usb drive in, icons appeared on the desktop, copied and moved files around just like it's supposed to work.

Only tested in GNOME so far.

---

### Post by Bargio on 2007-11-22
> **flick said:**
> What worked for me :

sudo apt-get install usbmount

a reboot

Logged back in, stuck my usb drive in, icons appeared on the desktop, copied and moved files around just like it's supposed to work.

Only tested in GNOME so far.

It seems that usbmount doesn't display an icon when plugging in an usb-pen:
[I]"USBmount is intended as a lightweight solution which is independent of
a desktop environment. [U]Users which would like an icon to appear when an
USB device is plugged in should use the pmount and hal packages
instead.[/U]"
[/I]

removing usbmount solved my problem :)

---

### Post by flick on 2007-11-22
@ Bargio :

Ah, the joys of linux. What works perfectly on one machine for one person botches things for someone else on a different machine. At least with Linux there are options, and forums full of ( possible ) solutions. Sorry my suggestion didn't work for you, but happy you found a solution.

---

### Post by Tanker Bob on 2007-11-22
I had tried that before as well and found the same thing as Bargio. Plus usbmount made phantom mount points in Krusader which made it difficult to tell which were phantoms after a while and which were new devices plugged in. Unfortunately for me, uninstalling usbmount simply put me back where I was before, i.e., no automounting.

---

### Post by Bargio on 2007-11-25
> **flick said:**
> @ Bargio :

Ah, the joys of linux. What works perfectly on one machine for one person botches things for someone else on a different machine. At least with Linux there are options, and forums full of ( possible ) solutions. Sorry my suggestion didn't work for you, but happy you found a solution.

Forget what i've said...it doesn't work anymore :(
i really don't know what to do...surely it must be something with hal...
i'll try to sudo-apt get usbmount again :)

---

### Post by Tanker Bob on 2007-11-25
> **Bargio said:**
> Forget what i've said...it doesn't work anymore :(
i really don't know what to do...surely it must be something with hal...
I just knew that was coming...

---

### Post by SeanONe on 2007-11-25
Man does this suck. I could just about deal with having to power cycle my external USB drive every reboot. Now a USB stick of a clients has been killed by this ******** and there are no drive icons of any kind on my desktop. Plugged in someones iPod the other day and no amarok. I just figured out how to get kontact to work again.

Why isn't there some kind of chkusb utility seeing as this is such a common and showstopping BUG. If this wasn't open source someone would be getting fired. Once I get my machine half working again its off to openSolaris for me.

---

### Post by SeanONe on 2007-11-25
Also I don't type stars this fucknut bullitin board is censoring me, what a ******* joke.

---

### Post by watway on 2007-11-30
Many Thanks, I have looked for an answer for this for a week or so. My problem was auto mounting a camera. I think it works for all usb drives.

---

### Post by Endolith on 2007-11-30
> **watway said:**
> Many Thanks, I have looked for an answer for this for a week or so. My problem was auto mounting a camera. I think it works for all usb drives.

Thanks for what?  Did you figure out a way to get it working?

---

### Post by brymux on 2007-12-01
> **Dow Franklin Dudley said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had a similar problem with my usb key and an  external disk drive. I found a solution at the very end of the thread posted by Dan Lenski here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025)

"Go into gconf-editor and navigate to /system/storage/default_options/vfat/mount_options, and then remove the "usefree" option from the list. Exit gconf-editor, and try hotplugging your drive again. It works :-)"

I tried it and, indeed, it worked.

Hope this helps; good luck.
I have had this same problem in both fiesty and now gutsy this didn't work for me whats odd is my wireless usb mouse works and so does my usb to keyboard and mouse adapter but not my hard drive.I have to fdisc to find its designation(it changes each time) then manualy mount it everytime the drive pwoers down or the computer resets.Is there an easy fix to make it hot plug?I use it to transfer files between my differant computers and OS's?

---

### Post by TheMouse on 2007-12-03
Cool. Now my flash drive works, so I don't have to lug my laptop to campus to get files for my classes. I'll have to wait til I get home to make sure that the workaround didn't do something weird for my printer and mouse, but so far, so good.

Thanks all.

---

### Post by natuk on 2007-12-03
Tried everything. No luck I am afraid. My memory stick works occasionally (1 in 10) but I can't figure out when. Also it only works with one usb port and not the rest. I suppose we just keep trying.

---

### Post by erix12 on 2007-12-08
I'm having the same problem. When I plug the USB pendrive the following appears in the system log:
```
[  401.932000] FAT: Unrecognized mount option "usefree" or missing value
```

I went to gconf-editor and removed the troublesome option from VFAT storage settings. Restarted everything possible but I still got the same error message into the logs.

Then I started to search for the "usefree" text in the config files and I found that HAL appends that string when VFAT volume is attached. I found that option in 
```
/usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi
```

In the above file I removed the line:
```
<append key="volume.mount.valid_options" type="strlist">usefree</append>
```
and restarted hald. After this change there is no more that "usefree" error but still can't mount. I just get a general error that "Cannot mount volume" and that there is some problem with mount options. Th system log doesn't have any related error message that could give some clue.

Any idea what I could check still? What can be that problematic mount option?

As for the record I'm using Ubuntu 7.10 (Gutsy) with 2.6.20-15-generic kernel, from Feisty, because my laptop wouldn't boot with the kernel from Gutsy.

Edit: OK, I figured out that removing that "usefree" from valid_options causing that error. But from where the gnome-mount takes that "usefree" option if it is removed from gconf?

Edit2: My bad, I did not realize that gconf is per user, so I removed the "usefree" form root by starting gconf-editor as root :) 
So, If someone has the same problem start gconf-editor as normal user and change the VFAT settings there and not as root!

---

### Post by jbeiter on 2007-12-08
My Neuros and kid's MP3 players did fine with 7.04. Upgraded to 7.10 and it auto-mounted an MP3 Player (Sandisk) the *first* time only. Now, nothing with automount. Tried rebooting and the suggestion listed in here with gconf.

Something is seriously FUBAR with USB and this version of Ubuntu.

I keep getting this error in /var/log/messages:
Dec  8 07:40:07 glyph kernel: [ 1211.033265] usb 5-8: new high speed USB device using ehci_hcd and address 7
Dec  8 07:40:08 glyph kernel: [ 1212.016214] usb 5-8: new high speed USB device using ehci_hcd and address 8
Dec  8 07:40:08 glyph kernel: [ 1212.535654] usb 5-8: new high speed USB device using ehci_hcd and address 9

and this in dmesg:
[ 1211.904482] hub 5-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[ 1212.016214] usb 5-8: new high speed USB device using ehci_hcd and address 8
[ 1212.423762] usb 5-8: device not accepting address 8, error -71
[ 1212.535654] usb 5-8: new high speed USB device using ehci_hcd and address 9
[ 1212.943202] usb 5-8: device not accepting address 9, error -71

---

### Post by swejuggalo on 2007-12-09
I use PYSDM (found within the repos, Synaptic). Load with sudo pysdm. Let it configure your drive. Use options "users,noauto". Apply. All your plugin usb units will work the next time you plug it in. At least all mine did. Phone, sd-card reader and stuff..

---

### Post by Tanker Bob on 2007-12-09
> **swejuggalo said:**
> I use PYSDM (found within the repos, Synaptic). Load with sudo pysdm. Let it configure your drive. Use options "users,noauto". Apply. All your plugin usb units will work the next time you plug it in. At least all mine did. Phone, sd-card reader and stuff..
I just installed PYSDM, let it configure the USB hard drive, rebooted, and now it seems like other USB stuff loads as well. I've had stuff work once before, so this isn't a definitive fix for me yet. But, it looks good so far. Thanks for the suggestion!

---

### Post by johnnywellas on 2007-12-13
I did the gconf-editor usefree thing (removed usefree, reboot, added usefree, reboot) and it works! Not a very good standard solution, though.

---

### Post by seppav on 2007-12-18
I was getting the message box complaining about mounting parameters when inserting an USB key. None of the above worked in my case.

My problem was that my laptop doesn't have an optical drive, but still there is a row in /etc/fstab telling to mount /dev/sdb as the cd-rom drive, meaning iso9660 filesystem. In my laptop /dev/sdb is usually the USB key. The problem was solved by simply commenting away the row in fstab.

---

### Post by Tanker Bob on 2007-12-18
> **Tanker Bob said:**
> I just installed PYSDM, let it configure the USB hard drive, rebooted, and now it seems like other USB stuff loads as well. I've had stuff work once before, so this isn't a definitive fix for me yet. But, it looks good so far. Thanks for the suggestion!

This didn't work for USB sticks at all nor for other devices in the long term.

---

### Post by lfcipriani on 2007-12-19
Hi, I really try all the workarounds cited in this Topic and I didn't get any successful results. Anymore suggestion? I'm really tired to search a solution for this.

---

### Post by A$h X on 2007-12-19
pysdm sorts out most mount problems. Goto to system > administration > synaptic package manager
then type "pysdm" into the search box. Install it, then goto system > administration > storage device manager. Click on SDA in the left-hand window then your USB drive should appear. Click on the assistant button, and you can change the options from there.

---

### Post by Chal on 2007-12-20
ok by now i fixed this prob for me in kubuntu gutsy

it tried everything buuuuuuuuuuut at the end editing my fstab works (for me)

open fstab

sudo kwrite /etc/fstab

this are the lines of my fstab before editing:

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=3ac5b2fc-17fa-4cbb-8b31-2a5d2191f39f / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=841068f9-540d-4379-8fce-003a47fd3412 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/sdb1 /media/sdb1 ntfs-3g defaults,locale=de_DE.UTF-8 0 0
/dev/sda1 /media/sda1 vfat rw,user,fmask=0111,dmask=0000 0 0

then i just removed a few lines and now i have only:

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=3ac5b2fc-17fa-4cbb-8b31-2a5d2191f39f / ext3 defaults,errors=remount-ro 0 1

and now everything works fine for me

---

### Post by dvo on 2007-12-26
Under KDE, just found the following solution.

When you plug in a USB device, an icon for it should appear on your desktop.
Click on it and the device will be mounted and also listed in /media.
For automatic mounting, right-click on the icon, 
select Properties -> Mounting -> "Mount automatically"
You may also adapt the name of the Mountpoint.

---

### Post by Muttley99 on 2007-12-28
> **Chal said:**
> ok by now i fixed this prob for me in kubuntu gutsy

it tried everything buuuuuuuuuuut at the end editing my fstab works (for me)

open fstab

sudo kwrite /etc/fstab

this are the lines of my fstab before editing:

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=3ac5b2fc-17fa-4cbb-8b31-2a5d2191f39f / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=841068f9-540d-4379-8fce-003a47fd3412 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/sdb1 /media/sdb1 ntfs-3g defaults,locale=de_DE.UTF-8 0 0
/dev/sda1 /media/sda1 vfat rw,user,fmask=0111,dmask=0000 0 0

then i just removed a few lines and now i have only:

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=3ac5b2fc-17fa-4cbb-8b31-2a5d2191f39f / ext3 defaults,errors=remount-ro 0 1

and now everything works fine for me

Yeah! this worked for me but for different reasons. I have the Asus EEE PC running Gutsy. I changed SDC to vfat from udf,iso9660 and now it solved my USB mount problems (EEE PC doesn't have a CDROM)

---

### Post by red_chameleon on 2008-01-18
It's not a perfect fix, but here's what worked for me:

"sudo mkdir /media/usb"
"sudo gedit /etc/fstab"

At the bottom of the file, I added the line:

"/dev/sdb1  /media/usb  vfat  noauto,users,rw,umask=0  0  0"

<Note: /dev/sdb1 is generally where my key shows up on my computer. It might be different for yours.>

This won't immideatly automount the key to your desktop, but it'll at least show up in Places-->Computer, and if you click on it, it automatically mounts then.

Goodluck.

---

### Post by cytg on 2008-01-18
haha .. i have this issue as well but only of some of my usb ports .. the others it works fine... friggin weird! .. i suppose there's two seperate usb channels/hardware and only one set gets identified ... wtf do i know :)

---

### Post by Gary Stout on 2008-01-18
I had the same problem and I used Muttley99's suggestion, but instead of removing all that he did, I only removed the line the had /sdb1 and the problem was solved. 
It drove me crazy for a while on this one too. I could manually mount the flash drive, but it was a pain having to do this each time I wanted to use it.

Gary

---

### Post by chumpjaw on 2008-01-26
All I did to get it working was reformatted my drive with Windows (getting rid of any software on it) and once I did that, Ubuntu 7.10 recognized it.  I was then able to swap files and all with Ubuntu....  I'm sure there is a way to do this from the command line in Ubuntu, but after messing with it for quite some time and being a noob...bla, bla, bla . . . I just wanted to share my 'success' with hopes of helping.

---

### Post by vrix on 2008-01-28
Also experienced this problem, and what I did was re-install **libhal-storage1** and **libhal1** using synaptic, then reboot and it worked.

I would like to note, eumetaxas was right about gnome-mount although I did not upgrade to 0.7 as he suggested.

Hope this helps.

---

### Post by lukem on 2008-02-23
Did a fresh install of Gutsy and everything was good except my external Segate vfat HD.  It would not auto mount when plugged in (usb).  It always worked fine on Dapper.  I can mount it manually from command line but it won't let me write files to it.  I installed pysdm and changed a few settings for the drive and rebooted.  Now when I plug the drive in it auto mounts but it does not put an icon on the desktop or open a nautilus window.  I just have to go to /media to open it but this is so much better than having to manually mount it and then not being able to write to it that I'm satisfied.  All my other usb devices (thumb drives, cameras, ipod) have auto mounted fine since installing Gutsy, but I back up on this Seagate and use it on windoze (it never quit working on windoze) for work so it is a relief to get it working again.  Thanks to all who contributed to this thread.

still having fun

---

### Post by ian65000 on 2008-03-17
> **cytg said:**
> haha .. i have this issue as well but only of some of my usb ports .. the others it works fine... friggin weird! .. i suppose there's two seperate usb channels/hardware and only one set gets identified ... wtf do i know :)

by george, i think he's got it! i've got 4 on the back, 4 on the front; ones on the back work, ones on the front don't. after faffing around with different settings and reinstalling things, i "solved" the problem with a 1m usb extension cable i found lying around.

---

### Post by Tanker Bob on 2008-03-17
> **ian65000 said:**
> by george, i think he's got it! i've got 4 on the back, 4 on the front; ones on the back work, ones on the front don't. after faffing around with different settings and reinstalling things, i "solved" the problem with a 1m usb extension cable i found lying around.
No so much here. All my ports on the back and front seem to work immediately after a restart with everything connected at that time, but not later if I disconnect something or plug anything in later, it's hit or miss (mostly miss) if they will be mounted or remounted.

---

### Post by paulkingnz on 2008-03-23
Hi, I had this problem on a toshiba tecra laptop but not on my desktop. I solved it with the following. I used wajig to reinstall libhal-storage1 and libhal1 like this for the noobs:

wajig reinstall libhal libhal-storage1

and now everything is working. My kernel detail from uname -a are:

2.6.24-12-generic if that helps anyone with troubleshooting. good luck.

---

### Post by brunodbo on 2008-05-29
I had a similar problem with my iPod Classic.

After I tinkered a little bit with the mount options it wouldn't automount anymore :'(

I went into gconf-editor > system > storage and found my iPod there. Removed all the mount options, disconnected my iPod, plugged it in again, and it magically automounted.

Thanks for the fix, back to tinkering :)

---

### Post by Yappy on 2008-05-30
> **chejrw said:**
> I removed the 'usefree' option, but my USB drives still do not automount.  Any furthur suggestions are appreciated.

I have a different set of problem. My USB storage come with slots for CF, SD card etc.

The drives for the cards are missing although they show up in Windows.

How to mount the various drives?

Thanks

---

### Post by rraiman on 2008-06-08
I just now reinstalled libhal-storage1 and libhal1.
Kubuntu 7.10 clean install.
It worked!  But why?

> **vrix said:**
> Also experienced this problem, and what I did was re-install **libhal-storage1** and **libhal1** using synaptic, then reboot and it worked.

I would like to note, eumetaxas was right about gnome-mount although I did not upgrade to 0.7 as he suggested.

Hope this helps.

---

### Post by gtdaqua on 2008-07-09
This is still a an issuse in Hardy. From today, USB drives wont mount automatically and have to manually mount them via command line. Is this a bug?

---

### Post by Tanker Bob on 2008-07-09
Don't know. It seems to be better in Kubuntu 8.04.1. Everything that I've tried so far has mounted.

---

### Post by gtdaqua on 2008-07-10
Still wont mount. I can see the USB in dmesg and lsusb. fdisk -l says its /dev/sdb. And I am mounting it manually. How to get around this?

---

### Post by Kimos on 2008-07-17
I just wanted to chime in and say that I was struggling for quite a while with these problems. Automounting would not work but dmesg would show that the device was detected and identified.

This is what fixed it for me, just reinstalling the HAL libraries.

```
sudo aptitude reinstall libhal1 libhal-storage1
```

---

### Post by bobofett on 2008-07-20
Just today I encountered the same problem but, not for the first time.

The other times even under earlier versions, I would give up trying and one day it would "magically" fix itself.

As I was reading through this thread I noticed someone mention something about pmount and I thought about checking to see what apt told me about my installed version, and that's when it hit me!  I had just had some problems with my video card after a hard reboot, and got sick of messing with the drivers, and just sucked up my pride and went the envy route...ha  Which worked great by the way.  During the envy process (forget if it was when I got envy..or a message I saw while envy was doing it's thing with the vid drivers) Which told me:

The following packages were automatically installed and are no longer required:
  debhelper xserver-xorg-video-amd intltool-debian libdns32 po-debconf
  libnm-glib0 html2text dpatch


Then it tells you to do apt-get autoremove to remove them.  Well for whatever reason I didn't go back and do that, but I did just do it about 5 minutes ago.  As soon as I did with no reboot needed the camera automatically mounted.

So at least in some of your cases the problem may be aptitude or at least a file mismatch caused by your packaging system.  I've on more than one occasion had performance related problems almost always revolving around times when apt wants to do an update (Serious video frame rate reduction), after apt does an update and hangs some other process up, or a case like this where it request further user command line intervention.  Point being the vast majority of my problems have revolved around aptitude.  So may be worth some of you checking that out.

---

### Post by Kimos on 2008-07-21
> **Kimos said:**
> This is what fixed it for me, just reinstalling the HAL libraries.

```
sudo aptitude reinstall libhal1 libhal-storage1
```

Arg... So the problem came back again. I did the same reinstall and rebooted and it started to work again, but that's not actually a solution and has definitely not solved the problem.

---

