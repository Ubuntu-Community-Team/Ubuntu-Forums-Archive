---
title: "Wubi &amp; 7.10 (Gutsy)"
date: 2007-10-20
forum: General Help
---

### Post by Ptrack on 2007-10-20
I want to use Wubi with Ubuntu's new 7.10 release.  I have a copy on CD can I make Wubi use this ISO instead of the 7.04 version it wants to pull from the internet?

Thanks--

---

### Post by antimatter15 on 2007-10-20
I think you need to download the alpha version of wubi:

[http://wubi-installer.org/devel/minefields/Ubuntu-7.10-alpha.exe](http://wubi-installer.org/devel/minefields/Ubuntu-7.10-alpha.exe)

---

### Post by ago on 2007-10-20
[http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield)

---

### Post by neodorian on 2007-10-20
Just tried the new alpha on my tablet.  It got to the part where you pick your timezone, but then failed at partman.  That's a new one for this machine.  It usually gets past that part just fine.

---

### Post by roratonet on 2007-10-21
Hi,
I need to install UBUNTUSTUDIO 7.10, but in the DISTRO list of WUBI 7.10 ALPHA there isn't UbuntuStudio!
How can I install it with wubi?
Thnaks:guitar:

---

### Post by Futureking on 2007-10-21
I want to use ubuntu 7.10 with wubi. I downloaded it. and burned the cd. when I explored the cd I saw that it contain wubi-cdboot exe file.
I run it. after processing somethings it says to me to reboot.

I rebooted. and booted from harddisk. where I saw two option to boot

Windows xp pro
ubuntu-linux

I choosed ubuntu linux. At that time cd was in cd tray. ubuntu loaded it reads the cds.

But after reading cds and fully loding it gives me a desktop.
No installation occurs.

It worked like live cd. it does not installed ubuntu.


When I use alpha release of wubi from minefield and use iso image insted of cd. ubuntu installed but I get error when I choose to boot into ubutnu.

something like this...

Error 17 File NOt found.

Press any key to continue.


I am big fan of wubi. I want to install ubuntu gusty as soon as possible.

So please help me.

---

### Post by rohedin on 2007-10-21
> **Futureking said:**
> 
When I use alpha release of wubi from minefield and use iso image insted of cd. ubuntu installed but I get error when I choose to boot into ubutnu.

something like this...

Error 17 File NOt found.

Press any key to continue.


I am big fan of wubi. I want to install ubuntu gusty as soon as possible.

So please help me.


Try defragmenting your hard-drive on windows.

---

### Post by Geokim on 2007-10-21
Greets and thanks for you effort on this one

I used to have the "Ntfs" problem too but after a chkdisk i pass this stage. The problem now is that the installation always stops at 32% ! Dunno why, maybe i should remove all "not so known hardware" from my pc? 

Thanks again

---

### Post by ago on 2007-10-21
> **Futureking said:**
> 
I choosed ubuntu linux. At that time cd was in cd tray. ubuntu loaded it reads the cds.

But after reading cds and fully loding it gives me a desktop.

wubi-cdboot does what it says on the tin: it BOOTS a CD. 
I'll soon add Ubuntustu to regular wubi

Try the latest alpha (347+).

---

### Post by ago on 2007-10-21
> **ago said:**
>  I'll soon add Ubuntustu to regular wubi

Hmm it looks like Ubuntustudio only provides an alterante ISO... That means we cannot add it this time around.

---

### Post by MSchenker on 2007-10-21
I just downloaded Wubi 7.10 alpha rev 357.  I'm really hoping it works!  Will report back later.

Thanks again for all the effort on the Wubi project!

---

### Post by acegear on 2007-10-22
358 has just been release im already using ubuntu right now using 358 installer..

---

### Post by ago on 2007-10-22
If the alpha works for you let me know!

---

### Post by dahamsta on 2007-10-22
Tried 358 twice. On the first try it crapped out on installation at 61%, although in hindsight it might have been scanning apt and just not feeding back correctly, as in the second attempt it was just after this point it went to apt. On uninstall got messages about filesystem problems, had to CHKDSK /F before I could delete the remains.

On the second go the installation was slow but seemingly successful, however I simply got a blinking cursor after choosing Ubuntu from the Windows boot menu. Had the same problem with filesystem errors on uninstall, currently running a full CHKDISK /R. I'll try again later.

Straight Ubuntu doesn't install clean on this rig - fakeraid - so please don't try to tempt me down that road again. :)

HTH,
adam

---

### Post by ago on 2007-10-22
> **dahamsta said:**
> Straight Ubuntu doesn't install clean on this rig - fakeraid - so please don't try to tempt me down that road again. :)
If normal Ubuntu struggles with your system as a rule of thumb, wubi will have similar problems too...
Software raids might be problematic... Particularly when you have to replace "Software" with "Windows"...

---

### Post by jonseemor on 2007-10-22
Hi guys.....

all I wannano isssssss, does anyone have a clue as to when the official wubi for Ubuntu 7.10 will be ready for primetime?

I used the wubi for 7.04 and loved it, and now the new one can't get here fast enough!

Thanx...

John

---

### Post by dahamsta on 2007-10-22
Seems unlikely when the partition manager is working with a virtual disk, and doesn't go anywhere near the RAID disks.

---

### Post by ago on 2007-10-22
> **dahamsta said:**
> Seems unlikely when the partition manager is working with a virtual disk, and doesn't go anywhere near the RAID disks.

I am mostly concerned that if you have raid1 in windows, Linux only sees 2 separate identical drives and use only 1 of the 2. So the drives go out of sync when you are in windows. That has nothing to do with partitioning, any simple write operation might affect it.

---

### Post by dahamsta on 2007-10-22
I didn't think Wubi worked like that. Why would Ubuntu try to write outside it's own (virtual) partitions (unless it's told to, of course).

I guess I'm thinking along the lines of VMs in general. One of these days I'll have an Ubuntu install that just works.

adam

---

### Post by ago on 2007-10-22
> **dahamsta said:**
> I didn't think Wubi worked like that. Why would Ubuntu try to write outside it's own (virtual) partitions (unless it's told to, of course).
In fact it won't. But wubi has still to write to the disk within the windows partition, and to do so it does not use a windows driver, but a vfat/ntfs linux driver. So if Linux is not aware of the existance of a raid1 array, because the raid is implemented on the windows side, when it writes a file into your ntfs partition, will do so only in 1 of the 2 drives only. It will be a perfectly good write, and it will be within the windows partition, but your drives will not be in-sync anymore.

> I guess I'm thinking along the lines of VMs in general.
A VM will probably run in Windows in your case, hence when you actually write files to the disk the windows driver is used, and windows knows about the array so it knows that it has to write stuff twice and not once...

IMHO software raids (particularly windows ones) are not really worth it...

Now all of the above is speculation, since I do not know how Linux copes with Windows Software Raids (particularly Raid 1), but that would explain your corruptions.

---

### Post by acegear on 2007-10-23
im having trouble in shuting down ubuntu

ill post the error when i get back..

---

### Post by ago on 2007-10-23
Did you upgrade any package? Can you post here /etc/init.d/umountfs. Also look if you have a file called: /var/run/sendsigs.omit with a number in it.

---

### Post by jrharvey on 2007-10-23
I heard alot of problems with wubi and upgrading or updating. I know you cannot upgrade the distro but can you do regular updates and kernal updates??? These questions are for both wubi 7.04 and 7.10

---

### Post by ago on 2007-10-23
> **jrharvey said:**
> I heard alot of problems with wubi and upgrading or updating. I know you cannot upgrade the distro but can you do regular updates and kernal updates??? These questions are for both wubi 7.04 and 7.10

You cannot upgrade from 7.04 to 7.10 (I will provide an upgrade script later on), but non-dist upgrades within 7.04 should work (including kernel upgrades). Upgrades within 7.10 we haven't test much to this point, will probably be fully supported within 1 or 2 days though.

If there are users with Wubi issues, feel free to redirect them to this forum.

---

### Post by jrharvey on 2007-10-23
Im not sure if it is you who does all this work or if its a team but whoever it is needs a big "Thank You". I personally run a seperate partition for my ubuntu but I feel like this program is the perfect thing for someone who has used windows all there life. I think if more people knew about it, more people would use ubuntu. One question though??? Does wubi emulate anything or does it simply use virtual diskpace to run completely native.


PS. I am testing out the alpha now.

---

### Post by ago on 2007-10-23
Thanks

> **jrharvey said:**
> Does wubi emulate anything or does it simply use virtual diskpace to run completely native.
The second one.

---

### Post by jrharvey on 2007-10-23
Well that is just too cool.

---

### Post by jrharvey on 2007-10-23
I will say that I wish there was an option to install the ISO with a cd. My wireless internet is terribly slow and take about 2 hours. So about an hour from now i should be installing the alpha 7.10.

---

### Post by ago on 2007-10-23
> **jrharvey said:**
> I will say that I wish there was an option to install the ISO with a cd. My wireless internet is terribly slow and take about 2 hours. So about an hour from now i should be installing the alpha 7.10.

Yes 7.10 (rev360+) should work with a physical CD, it should be able to detect it automatically if it is inserted when wubi runs. It is better to close any other application that may be accessing the CD though.

---

### Post by jrharvey on 2007-10-23
OMG you are right. I wish i knew this before, haha. It took like 2 minutes instead of 2 hours.

---

### Post by jrharvey on 2007-10-23
Ok I just started ubuntu gutsy and it is giving me an error about """the file system type ntfs cannot be mounted on /. because it is not a fully-functional Unix file system. Please choose a different file system, such as ext 2.""""

Is there a fix for this???

---

### Post by ago on 2007-10-23
It means ntfs is marked as dirty, you need to run chkdsk /r from within windows and then reboot into Ubuntu again.

---

### Post by jrharvey on 2007-10-23
Thank you, it worked. I love this program. I now have a flashy new install of gutsy on my girlfriends laptop. No partitioning needed :)   Alpha confirmed to work on Dell Inspiron B120

---

### Post by jrharvey on 2007-10-23
Ok I got gutsy installed fine and I thought I would update since it seems to be safe. After updating (mostly firefox and other stuff) ubuntu will no longer boot. It gets stuck at "running local boot script". Is this a wubi problem or an ubuntu problem?

---

### Post by ago on 2007-10-23
> **jrharvey said:**
> Ok I got gutsy installed fine and I thought I would update since it seems to be safe. After updating (mostly firefox and other stuff) ubuntu will no longer boot. It gets stuck at "running local boot script". Is this a wubi problem or an ubuntu problem?

Probably a wubi problem. Can you get more information on that? What packages did you update and where exactly does the hang occurs?

---

### Post by acegear on 2007-10-23
> **ago said:**
> Did you upgrade any package? Can you post here /etc/init.d/umountfs. Also look if you have a file called: /var/run/sendsigs.omit with a number in it.

yes i have updated ubuntu by update manager. 




/var/run/sendsigs.omit 2416

ill post again the display text while shutting down.

---

### Post by ago on 2007-10-23
> **acegear said:**
> ill post again the display text while shutting down. 

No need, I have enough info. I'll provide a patch tonight.

---

### Post by acegear on 2007-10-23
wow ago you post fast ^_^

this is the display screen while i was shutting down ubuntu
it stop on the networkmanager 
libdal shutdown fail
...dbus_connection failed 

stops there

---

### Post by ago on 2007-10-23
Check out rev 364+. Should work after updates.

---

### Post by garybrlow on 2007-10-24
I have downloaded the Xubuntu  Gutsy 7.10 alternate final iso and the wubi rev 364. I have placed both on the same location but wubi ignores the iso file and insists on downloading from cdimage.ubuntu.com. Offline installation fails. Are others having this kind of problem too?

---

### Post by ago on 2007-10-24
Make sure it is the DESKTOP iso

---

### Post by freechelmi on 2007-10-24
Hi , I try Wubi for gutsy : 

[LIST]
[*]ON CD -cdboot  : After restart installation fail and fall to a LIveSession CD 
[*]through minefields : I put My iso in the right folder , I reboot , ubiquity starts &  stops while creating the Root partition telling " you can't use NTFS partition format for / , you shoudl use ext2 "
[/LIST]

One reason could be that the D: drive I'm trying to install on is really fragmented so maybe the 5 GB file is not contiguous and it's a problem for ubiquity ? 

SO i'll keep on feisty  for now 


But Anyway I'd like to say that all the Wubi concept :guitar:  !!!

---

### Post by ago on 2007-10-24
> **freechelmi said:**
> Hi , I try Wubi for gutsy : 

[LIST]
[*]ON CD -cdboot  : After restart installation fail and fall to a LIveSession CD
The purpose of cdboot is simply to boot a physiscal CD 
 
> 
[*]through minefields : I put My iso in the right folder , I reboot , ubiquity starts &  stops while creating the Root partition telling " you can't use NTFS partition format for / , you shoudl use ext2 "

You need to run chkdsk /r from windows before running wubi

---

### Post by PGHammer on 2007-10-25
> **ago said:**
> The purpose of cdboot is simply to boot a physiscal CD 
 

You need to run chkdsk /r from windows before running wubi

Apparently Ago has a point.

I removed/uninstalled my previous 7.04 install and installed 7.10 (or tried to); however, it refused to successfully install until I ran chkdsk/r, then ran the install (using the alpha-368 installer and the 7.10 desktop ISO I downloaded separately).

Utterly *flawless* escept that it detected that I had no swap file (then again, with 1 GB or more, in most cases, a Linux desktop shouldn't need a swapfile); does Wubi create a swap partition?

---

### Post by garybrlow on 2007-10-25
Desktop CD install is pretty slow for my test box. I can get past the boot screen but gets stuck while loading X. I can see the desktop wallpaper but its gets stuck there for an hour or more. I hope the alternate install iso could be supported soon. :)

Cheers! :biggrin:

---

### Post by ago on 2007-10-25
Alternate will not be supported in this release cycle, but if ubiquity does have a text interface (have to check), then it should be possible to start in non-graphic mode

---

### Post by anrichp on 2007-10-27
Hi everyone 

I'm kinda new to ubuntu, and need some help I've got the latest version of wubi alpha rev 377 but after i install it and reboot my system , and boot up in ubuntu linux , it has the ubuntu starting screen and then goes to a black window saying something about busybox debian etc.
What do i need to do to get this working?

thnx

---

