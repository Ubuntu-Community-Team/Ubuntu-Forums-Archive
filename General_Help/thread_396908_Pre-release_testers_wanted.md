---
title: "Pre-release testers wanted"
date: 2007-03-30
forum: General Help
---

### Post by tuxcantfly on 2007-03-30
This is the wubi pre-release version (minefield) testing thread. The minefield releases should generally be stable, but have received little to no testing, so if unsure, just use our latest stable release at [http://cutlersoftware.com/ubuntusetup/latest.html](http://cutlersoftware.com/ubuntusetup/latest.html)

Download the pre-release (minefield) versions at

[http://cutlersoftware.com/ubuntusetup/devel/minefield](http://cutlersoftware.com/ubuntusetup/devel/minefield) the direct link to the latest minefield version is at [http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html) and the sources for the minefield versions are at [http://cutlersoftware.com/ubuntusetup/minefield-src.html](http://cutlersoftware.com/ubuntusetup/minefield-src.html)

and report your experiences here. If it works, report it here too. If you have tested another wubi release and it worked, yet the latest minefield version didn't work, make sure you report it here.

---

### Post by tuxcantfly on 2007-03-30
ignore this, I'm subscribing to this thread

---

### Post by dbgeezer on 2007-03-31
> **tuxcantfly said:**
> We're about to release wubi-7.04-beta-v2 (based on minefield5), with a few new bugfixes (in particular, the username input bug), but before we do so, we want to make sure that there are no new major bugs, compared to wubi-7.04-beta. This is for testing purposes, and although the pre-release beta-v2 SHOULD be stable, if unsure, just use our latest stable release at [http://cutlersoftware.com/ubuntusetup/latest.html](http://cutlersoftware.com/ubuntusetup/latest.html)

Download the pre-release beta-v2 at

[http://cutlersoftware.com/ubuntusetup/wubi/downloads/experimental/wubi-7.04-beta-v2.exe](http://cutlersoftware.com/ubuntusetup/wubi/downloads/experimental/wubi-7.04-beta-v2.exe)

and report any problems here. If it works, report it here too. If you have tested wubi-7.04-beta, and it worked, and beta-v2 didn't work, make sure you report it here.

Everything works OK until the second reboot.  This is not a bug in wubi or lupin, but the fact that my video driver (ATI) is not in feisty yet.  Evidently the network driver (Intel 3945) doesn't load either, since I don't have wireless.

You've done a good job on capturing the Windows settings that you currently use...user name, time settings, etc.  Would it be possible to capture the machine characteristics and pre-set repositories to search based on them?

In the absence of an automated facility, can I set these in preseed.conf?

---

### Post by danbutter on 2007-03-31
I have tried both and have noticed no difference between the two.
I see tons of errors while it is booting up, but all seems to work fine when loaded.
Well all of the basic stuff.

Still having issues with nvidia drivers that I can't see to fix no matter how many different times I try.
The (name escapes me now and it is broken so I am posting from windows) restricted drivers thing shows my wireless intel 3495 and enables it.
It shows nvidia, but refuses to enable it.

I can install the nvidia driver multiple ways (I have tried quite a few times), but when I go do enable it and hit ctrl alt backspace it breaks X all together and I can never get it back.

other distros like vector and simply mepis do fine with this machine (dv9000t with nvidia G70/7600)
Not sure why I can't get it to work with ubuntu.

I love the concept of wubi and the fact that I can dual boot without partitioning.
Hopefully I can figure this out soon.

---

### Post by tuxcantfly on 2007-03-31
both these errors are related to video card drivers, and given that there have been no errors where the breakage was expected due to changes (mounting filesystems and the installation phase of wubi). For the nvidia drivers, this will be fixed in a later version; it's due to this bug: [https://launchpad.net/lupin/+bug/87849](https://launchpad.net/lupin/+bug/87849) which I'm working on fixing. Anyhow, there are no new regressions, so beta-v2 has been made the new officially released version.

---

### Post by tuxcantfly on 2007-03-31
this thread has now become the new minefield release testing thread. if interested in helping to test the next versions of wubi, go to [http://cutlersoftware.com/ubuntusetup/devel/minefield/](http://cutlersoftware.com/ubuntusetup/devel/minefield/) download the latest release (exe not source code) (currently beta-minefield6 [http://cutlersoftware.com/ubuntusetup/devel/minefield/wubi-7.04-beta-minefield6.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/wubi-7.04-beta-minefield6.exe)) and report success/failure here. remember, minefield releases should be stable, yet have gotten little to no testing, so if you don't need any of the bleeding-edge functionality/tweaks/improvements, just use the stable release

---

### Post by danbutter on 2007-03-31
> **tuxcantfly said:**
> both these errors are related to video card drivers, and given that there have been no errors where the breakage was expected due to changes (mounting filesystems and the installation phase of wubi). For the nvidia drivers, this will be fixed in a later version; it's due to this bug: [https://launchpad.net/lupin/+bug/87849](https://launchpad.net/lupin/+bug/87849) which I'm working on fixing. Anyhow, there are no new regressions, so beta-v2 has been made the new officially released version.

Ok, sounds good.
If you post a note as to which version of minefield coming up has those fixes committed then I'll test as soon as I can to see if it works for me.

---

### Post by tuxcantfly on 2007-04-01
I've uploaded minefield7, the proposed beta-v3, at  the usual spot at [http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html) test away if interested, it should work (at least it did for me) but remember that the minefield releases are EXPERIMENTAL and you should use the stable release at [http://cutlersoftware.com/ubuntusetup/latest.html](http://cutlersoftware.com/ubuntusetup/latest.html) unless you're interested in helping test wubi.

just a few minor bugfixes that correct some rebooting problems, still haven't fixed the kernel upgrading issue, that'll hopefully come soon

report problems/success with the latest minefield versions here, please, we need your feedback

---

### Post by tuxcantfly on 2007-04-01
alright, I've uploaded a new minefield build, minefield9, usual download spot at [http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html)

**new features:**

**ntfs-3g now enabled by default**, so accessing your windows drives is as simple as doing this:

create a mountpoint:

```
sudo mkdir /media/windows
```

then figure out which drive is your windows drive:

```
sudo fdisk -l
```

which should return something like this:

```
geza@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1**   *           1       12158    97659103+   7  **HPFS/NTFS**
/dev/sda2           12159       15197    24410767+  83  Linux
/dev/sda3           30274       30401     1028160   82  Linux swap / Solaris
/dev/sda4           15198       30273   121097970   83  Linux

Partition table entries are not in disk order
geza@ubuntu:~$ 
```

Then find the line saying HPFS/NTFS (shown in bold), and take the value under "device" (in this case /dev/sda1 which is shown in bold) and substitute it into the bold portion in this command:

```
sudo ntfs-3g **/dev/sda1** /media/windows
```

then you should be able to access it at /media/windows, when done, simply unmount using:
```

sudo umount /media/windows
```

hopefully by final release we'll have it mounted/unmounted automatically on startup/shutdown

other new feature: **initrd regeneration problem (sort of) fixed**

right now, it's possible to upgrade your kernel (for the video card drivers and all), only it's a bit more complicated than usual, hopefully we'll have the behavior identical to that of standard ubuntu by the final release:

first, go into synaptic and install the kernel you need, something like: linux-image-2.6.20-13-generic and if you need it for nvidia/ati drivers, also remember to install linux-restricted-modules-2.6.20-13-generic

if you're doing this for the nvidia/ati drivers, now go to system -> administration -> restricted drivers manager, and click enable. DON'T REBOOT YET

then mount your windows drive as discussed above

then go to /boot and find vmlinuz-2.6.20-13-generic (substitute your kernel version here) and initrd.img-2.6.20-13-generic, and then copy them over to /media/windows/wubi and rename them to linux and initrd.gz

now reboot and all SHOULD work (no guarantees, if you run into problems, report it here)

if this all looks too confusing to you, just wait for the next release, where we should hopefully have all this nicely automated in a user-friendly way, remember, the minefield releases are not for the faint of heart

report success or failure here, please, we need your feedback!

---

### Post by mwilley on 2007-04-02
I tested minefield 9, and am sorry to report that I have the same problem as beta v2 and v1.
After rebooting (in the grub?) code goes down with no errors, until I get to "loading, please wait..."  It stays here for about 5-10 minutes, until I get this:
```
check root=booting cat/proc/cmdline
or missing modules, devices: cat/proc/modules ls/dev
ALERT! does not exist. Dropping to shell
```
There was a topic posted with many people having the same problem here: [http://ubuntuforums.org/showthread.php?t=397769]("http://ubuntuforums.org/showthread.php?t=397769")
Hope some one will find a solution... Wubi is coming along nicely.

---

### Post by ago on 2007-04-02
Do you have a sata disk? What do you see under "/tmp"? What do you see under "/" The command to show folder content is "ls" (that is LS in lower case). Append here the content of / and /tmp as well as C:\menu.lst...

---

### Post by mwilley on 2007-04-02
Well, I don't know what a sata disk is, but this is what I get...
**/** Access denied
**/tmp** Access denied
**C:/menu.lst** Does not exist

---

### Post by ago on 2007-04-02
did you do "ls /"? And "ls /tmp"? 

As for C:\menu.lst it must exist or you would not see any "loading..." message, you access that from windows not form linux.

---

### Post by tomcat23a on 2007-04-03
I tried out minefield9 yesterday and it worked great. Today I'm installing again (minefield10),

*edit*

works great. (error -see later post)  glad to see um, /media/host/ as the drive that wubi is on. I would love to see all disks listed there by label, or something like that. (All my disks don't appear under 'places'...) Yes, i know you guys will get around to  doing something aestetically neato for this eventually. 

The installer still brings my username "Administrator" in uppercase. 

Thanks again.

---

### Post by myoldryn on 2007-04-03
Hi! I tried the minefield10 installation. Had some problems installing it. I found one intresting thing. The grub don't tolerate fragmented disk. So, i defragmented it, but windows only make files contiguouos and leaves the disk looking like chees. So this didn't help. Ok, i uninstalled and then reinstalled ubuntu again, but this time i defragmented disk after wubi install and before reboot, and then everything worked...

EDIT: I think that this is a major problem. Is this possible to defragment the disk before the installation automaticli?

The second problem that i had. The fat filesystem don't support files bigger than 4gb. So, when the wubi installer creates images it skips the root image.

The third problem was that i couldn't choose default disk location for installation. So the installer choose the bigger free space on my fat partition.

---

### Post by ago on 2007-04-03
> **myoldryn said:**
> EDIT: I think that this is a major problem. Is this possible to defragment the disk before the installation automaticli?
That is always a problem when initrd and/or kernel are fragmented. But that is relatively unlikely. Fragmentation of root.img on ntfs should be safe. As for the fragmentation of root.img on fat, I do not know.

> The second problem that i had. The fat filesystem don't support files bigger than 4gb. So, when the wubi installer creates images it skips the root image.
Yes we are aware of that. That fix has already been committed and it will be in new releases.

> The third problem was that i couldn't choose default disk location for installation. So the installer choose the bigger free space on my fat partition.
You can simply move the wubi folder to a different partition. There is a lock on the files at the moment (it should not affect fat though), that will be removed in future versions.

---

### Post by mwilley on 2007-04-03
> **ago said:**
> did you do "ls /"? And "ls /tmp"? 

As for C:\menu.lst it must exist or you would not see any "loading..." message, you access that from windows not form linux.

Okay, I guess I was doing it wrong...  This is what I got this time:

**ls /tmp** zenigata.log
**ls C:/menu.lst** no such file or directory

I'm still not sure why it says that for menu.lst...

---

### Post by ago on 2007-04-03
C:\menu.lst is in windows. When you are in windows you will see it. But what is important is the output of 

more  /tmp/zenigata.log

There should be some errors in there, you can post them here. You can scroll the page by pressing enter.

---

### Post by myoldryn on 2007-04-03
Ok... i have encountered new problems:

1. When i install, then the installer reports that it can't install preseed..or something...after i press continue, then the red screen appears and text is scrolling really fast...after hard-reboot everything seems ok...,but
2. When i try to update system, then the update manager crashes... if i try to install manually with apt-get, then i get errors... it have to do smoething with udev and initramfs-tools...

When i installed beta earlier on dedicated partition, then there was no problems..

---

### Post by mwilley on 2007-04-03
> **ago said:**
> C:\menu.lst is in windows. When you are in windows you will see it. But what is important is the output of 

more  /tmp/zenigata.log

There should be some errors in there, you can post them here. You can scroll the page by pressing enter.

Whoa, that's a big log (of course, what do I know?)...  Found a big line with *ERR_* and the end looked like there were some errors, but otherwise it all looked okay.  
About one fourth into the log, I found this:
```
ERR_MNT_ROOT=1
ERR_NO_INIT=2
ERR_RUN_INIT=3
ERR_MNT_HOST=4
ERR_NO_HOST=5
ERR_LOOP_ROOT=6
ERR_LOOP_HOME=7
ERR_LOOP_SWAP=8
ERR_LOOP_EXTRA=9
ERR_MNT_ISO=10
ERR_NO_ISO=11
ERR_INVALID_ISO=12
ERR_LOOP_ISO=13
ERR_NO_PRESEED=14
ERR_FAIL=15
ERR_MNT=16
ERR_LIVE_ISO=17
ERR_ALTERNATE_ISO=18
ERR_NO_FILESYSTEM=19
ERR_WRONG_FILESYSTEM=20
```

And at the end of the log...

```
log_warning_msg Could not find host...
_log_msg_warning  Could not find host...
warning:  Could not find host...
return 5
log_Failure_msg Could not find host folder, please check boot parameters.
_log_msg Failure: Could not find host folder, please check boot parameters.
echo Failure: Could not find host folder, please check boot parameters.
Failure: Could not find host folder, please check boot parameters.
```

Hope these are of any use to you... there were many times it said something was unknown, but it never said it was an error so I didn't write it down.

Oh, and is there a better way to get this log to you (besides writing it down)?  That would be very useful.

---

### Post by tomcat23a on 2007-04-03
With my last minefield10 install I got the same errors that Myoldryn reports. Red screen at the end of ubuntu install. (I thought it was a keyboard error, as it kept repeating with an input error message and I had no keyboard control... did a cold reset and ubuntu worked... until the package manager went crashy. 

Here's another bug:
Though I've renamed the wubi folder, (to wubi2)  I can't seem to delete the disk images. (Windows says something's got them open...?) I know the folders were set 'read only'... Is there something in the boot process that would be searching for wubi*/disk/ and locking the images there?

I was able to delete /wubi2/disk/swap.img from within ubuntu, but not windows. Renamed and moved my /wubi2/disk/root.img to extra.img in the new wubi install IN Ubuntu, too.

But can't move the *.img files in windows, and I've unset the read only bit on the folders. Can't rename the files, either -- but from within windows I can rename the folders.

---

### Post by tomcat23a on 2007-04-03
Reinstalled under minefield9, after getting an error on the ubuntu REinstall for minefield10 -- the ubuntu setup couldn't find the installation files... it dumped me back into the blue/red ubuntu setup and I didn't have keyboard control.

Mind you, though I reinstalled ubuntu via minefield10, I had an extra.img in /wubi/disks that had previously been a root.img. Not sure if it mounted everything but may have found the ubuntu root stuff on extra.img and somehow that messed up the install.

Also, after minefield9 install ubuntu is asking for the password to be entered again.

---

### Post by ago on 2007-04-03
> **mwilley said:**
> Hope these are of any use to you... 

From windows, do you see "c:\wubi\linux" ? all lower case?

---

### Post by mwilley on 2007-04-03
> **ago said:**
> From windows, do you see "c:\wubi\linux" ? all lower case?
Yes, it's there...

---

### Post by dbgeezer on 2007-04-03
I just downloaded minefield 11, which didn't work (invalid file, or something).  It's only 2.7MB on in the folder. Looks like a botched upload.

---

### Post by tuxcantfly on 2007-04-03
> I just downloaded minefield 11, which didn't work (invalid file, or something). It's only 2.7MB on in the folder. Looks like a botched upload.

oh yes I built minefield11 as a test build of the currently broken devel branch (bunch of grub issues) so I aborted in the middle of uploading (it doesn't work), so I've removed the minefield11 download for now, use minefield10 or 9 for now (minefield10 gives an error at the end of install for some strange reason, but works fine after a hard reboot)

---

### Post by ago on 2007-04-04
> **mwilley said:**
> Yes, it's there...


Then chek the log again there should be some errors before "Could not find host..."

---

### Post by whitehawk24 on 2007-04-04
First of all thank you!   Wubi is GREAT!  I'm doing my best to move away from windows where I can and Wubi is making that possible.

I've used the Beta-V2 version to get machines up and running and it pretty much has allowed me to start learning Linux (Ubuntu and Kubuntu running - can't make up my mind which I prefer).

Now, to make a long story short, I've also got an Nvidia 7600GT that I can't get to run in Enhanced mode.  Tried all the installation tips that I could find on these forums and end up editing xorg.conf to get the X server running again with the "nv" driver.  I've even tried the instructions higher up in this thread with minefield 10 and that caused the system to hang as it was trying to load the kernel.   I think my problem related to having two different kernels in /boot (12 & 13) and uname -a reported 12 so that was the one I used.  However it appeared that somehow inrtd.img installed was 13.  Not sure how that happens, maybe through all the "updates" that the system does after the initial install.  Also could have been something I did in trying to follow the instructions.  In any case, I'm going to load minefield 10 again and give it one more shot before just going back to Beta-V2 and waiting for the new release.

Don't know if any of this helps, but did at least want to say thank you...

---

### Post by danbutter on 2007-04-04
> **whitehawk24 said:**
> 
Now, to make a long story short, I've also got an Nvidia 7600GT that I can't get to run in Enhanced mode.  

I have issues with my 7600 also.  Mine is in a laptop and is seen as a G70.
It has been commented on earlier in this forum and has something to do with drivers.

I am also waiting for a fix for this.

---

### Post by hamishaus on 2007-04-04
Morning all from sunny downtown China (I'm an Aussie working here for a while). Thought you might like some feedback on Wubi Beta V2 installer and what happened to me. 

I have an Asus A6Rp laptop, which is known as being one of the most Linux UN-friendly machines around. I have used the LiveCd of Feisty Beta and most things work, with the notable exception of wireless (Broadcom Corp 4318 chipset). So, when I found out about Wubi I lept on it, as I thought I might be able to get the wireless working, and then maybe get away from MS completely!

The install process needs a few tweaks (which may well have been done with some of the minefield releases, but I thought I'd still feedback anyway). 

This, and many other laptops, require the "hpet=disable" kernel switch. I need to add this for Ubuntu, Kubuntu, Knoppix, SystemRescueCd, etc to get them to boot up (LiveCDs). After some searching I found that I had to modify the C:\menu.lst file to include that, and then it would boot up. I suggest that this is included somewhere in the documentation or on a screen to change kernel parameters. There are a LOT of laptops which require the "hpet=disable" switch, and I'd suggest that  it is included in a tick a box screen, along the lines of... "Are you using a laptop (maybe put in some model nos if applicable), then tick this box to enable hpet=disable?" Does anyone know what this switch does?! If it is enabled for ALL laptops, would it be a bad thing?

The install, when done, consumed about 16 GB of my hard disk. I think that a warning should be placed at the very beginning of the install process that it will take up a LOT of disk space and the person given the option of continuing, or maybe the installer could check for disk space and notify if it's too low. 

The Windows username on the laptop has the first letter capitalised. The Ubuntu installer doesn't accept it and throws an error, which may be a showstopper for a complete newbie. I'd suggest that in the Wubi installer screen, which asks for the username and password, that a warning is placed that the username must be in lower case.

Also, the password does not seem to come across, as the Ubuntu installer asks for the password again. Not a big issue, but if you want to streamline for Linux newbies,  then that might be a small issue to look at.

Post install:

I found this post: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) to get the wireless working. After install of the Feisty package and a reboot, I had to switch the eth1 to "roaming mode" to get a DHCP assigned IP address. After another reboot, I had working wireless! :-)

Most of the other hardware that is on this laptop works, including the sound, although there are a few quirks with it. The FN+ buttons don't quite work, as the volume control seems to be linked to Line In (Microphone) rather than PCM for some reason. The volume buttons (FN+F11 & F12) do work, but the mute button does not. I don't know if this is a Wubi thing or an Ubuntu thing, but I thought I'd mention it.

The screen brightness buttons FN+F5 & F6 do work. 

I didn't really try much else (wired lan works), but I did try an update using Synaptic. I got 262 packages to install, which downloaded (using wireless!!!). But a lot of the Open Office packages got broken, and didn't want to get fixed. There was an issue with the fonts package too. However, OO still seemed to actually work.

All in all, I am VERY impressed!!! This is a GREAT project, and I will certainly come back to it when it is a little more polished. I will subscribe to this thread, to see if there's any reaction to my feedback. 

At the moment, this has led me to believe that I can get Ubuntu Feisty working on my laptop. I have about 50 GB spare space (after Wubi is uninstalled), and I think that I might partition and install the full version. Thanks so much for giving me the opportunity to test my hardware and make sure I can get the wireless to work.

Hamish

---

### Post by ago on 2007-04-05
Thanks for the feedback:

* Username: has been fixed

* 16GB: That depends on the free space available, it varies from 5 to 22. In future version it will be possible to override virtual disk size via parameters/extra dialog

* hpet: will investigate that

* password: it's strange it should come across

* keyboard: it may depend on the detection of the keyboard variant, but that can be changed from within ubuntu

---

### Post by hamishaus on 2007-04-05
Hi ago

Thanks for the response. I figured that some of the things you mention might been the case (disk space, and keyboard things), but I also know that sometimes the little things that people mention in passing turn out to be the key to fixing a problem!

One other suggestion, which is project related, rather than usage related. There is mention in this forum thread about the minefield builds, but I can't find any (useful) information about them, and what fixes they may contain. 

Whilst I know that the minefield builds are not the official release (I believe that Beta V2 is), it would be good to know what the project has done since then, especially as it seems to be going ahead in leaps and bounds!

So, I suggest a "changelog" of what has been done in the different builds available, preferably somewhere really accessible like from the wiki, so that when the "official release" is updated, we know what has been done, and what we can look forward to.

Keep up the great work! :-)

Hamish

---

### Post by ago on 2007-04-05
You can find more detailed info in the 2 projects that create the wubi product,

[https://launchpad.net/wubi](https://launchpad.net/wubi)
[https://launchpad.net/lupin](https://launchpad.net/lupin)

The minefield are in this folder [http://www.cutlersoftware.com/ubuntusetup/devel/minefield](http://www.cutlersoftware.com/ubuntusetup/devel/minefield)

At the moment there are a few changes to be sorted out, then you will se new threads on this forums about new minefields. There will probably be some this w/e.

---

### Post by hamishaus on 2007-04-05
Hi again ago

Sorry to be a pain, but I did look at those sites on Launchpad, but the information on where the project is going is difficult to find and assimilate. There does not seem to be much info on open bugs and the status of them, or what fixes each minefield build has in it. I thought that a simplified version of all that might be a good thing.

Also, just to be REALLY picky, you have to know where the minefield builds are, as there is no direct link to them (that I can find,except from these forums), and the download options from the Wubi web page lead you to a different directory tree structure ([http://cutlersoftware.com/ubuntusetup/wubi/downloads/](http://cutlersoftware.com/ubuntusetup/wubi/downloads/)) rather than the one you have indicated in the post above ([http://www.cutlersoftware.com/ubuntusetup/devel/)](http://www.cutlersoftware.com/ubuntusetup/devel/)). The www. and the lack of the www might be just an oversight on someones part, but they seem seperated, and lead to different places, though both lead back to the webpage if you hit Up or Parent Directory (in Firefox) a few times.

I fully realise that this is primarily a tech project and after that comes the communications and so on. So, I will not hold it against you to get the work done first and then streamline the process of communicating it to us, especially as I know how much work it must be at the moment! Once again, I think this is an admirable project and you should all be applauded for it. I will be looking forward to the minefield builds as you mention.

Hamish

---

### Post by ago on 2007-04-05
> **hamishaus said:**
> Hi again ago

Sorry to be a pain, but I did look at those sites on Launchpad, but the information on where the project is going is difficult to find and assimilate. There does not seem to be much info on open bugs and the status of them, or what fixes each minefield build has in it. I thought that a simplified version of all that might be a good thing.
Good point we will try to mention in the bug report in what revision the bug has been fixed, and the minefields will also refer to revisions. 

> Also, just to be REALLY picky, you have to know where the minefield builds are, as there is no direct link to them (that I can find,except from these forums)
That's the intention. The website is intended for regular users, that mostly want something that "works". The forum are generally frequented by more advanced users, who might be willing to help and can better understand the development cycle and its problems. Therefore the minefields are only advertised on the forum.

---

### Post by mwilley on 2007-04-05
> **ago said:**
> Then chek the log again there should be some errors before "Could not find host..."

Okay, I looked again, there are no obvious errors, so I pretty much guessed at what parts were important...
This part comes after all the "ERR_" messages:

```
find_host_folder 
wait_for_devs
log_begin_msg...waiting for devs...
[-x /sbin/usplash_write]
/sbin/usplash_write TEXT... waiting for devs...
_log_msg Begin: ...waiting for devs
echo Begin: ...waiting for devs...
udevtrigger--subsytem-match=block
udevsettle
log_end_msg...devs loaded
[-x /sbin/usplash_write]
/sbin/usplash-write SUCCESS ok
_log_msg Done.
echo done.
Done.
```
And a few lines down...
```
Begin: Fast scan
list_devices
ALLDEVICES=
check_fs /dev/hda1
dev= /dev/hda1
get-s /dev/hda1
[-n]
[ntfs=unknown]
[ntfs=swap]
return 0
ALLDEVICES=/dev/hda1
check_fs /dev/hda
dev=/dev/hda
get_fs  /dev/hda
[-n]
[unknown=unknown]
```

Hopefully **this** will help... I wish I knew what you were looking for (specifically), that would help my search so much more.

---

### Post by tomcat23a on 2007-04-05
Perhaps a suggestion for what command to do to save the /tmp/zenigata.log ? (Linux newbie here, but I think that's what you Wubi team guys need to see when ubuntu hangs?)

I think I've got my xorg.conf down cold though, so I'll give things another install later tonight. If you guys have a new minefield up, I'll give it a go then. Let us testers know what to watch out for!

Thanks again!

---

### Post by ago on 2007-04-06
> **mwilley said:**
> 
Hopefully **this** will help... I wish I knew what you were looking for (specifically), that would help my search so much more.

The error should be below, when trying to find the host folder and trying to mount the host device.

---

### Post by dannyboy79 on 2007-04-06
i am having a hell of a time trying to get edgy or dapper installed on an emachine. (have attempted both live cd's and alternate discs)
**Specs**
600mhz Celeron
196mb ram
intel onboard graphics
4x4x24 cd-rom on ide0
10.2gb seagate hd on ide1 (4gb NTFS Win2000, remaining ext3 formatted with gparted live cd)

if it matters i used the latest gparted livecd to shrink the NTFS parititon from 10.2 down to 4gb and I made a ext3 parition for ubuntu. (oops, forgot /swap at that time) 

**Issue with Live cd** dapper and edgy (NOTE: puppy linux 2.14 works fine)
infamous black screen with blinking cursor in the upper left hand corner. tried the break=bottom trick but it would just freeze during booting and it would never make to the intramfs prompt. (or whatever that is)

**First Issue with alt cd and boot options:**
installer told me it couldn't mount partition 1 (win 2000 install) to ANY mount point no matter where I tried. I just chose not to mount it. It froze during installing the base system with about 18% complete. Had to do a hard shutdown, from that point on I can't get this far.

**Second main Issue with alt cd and boot options:**
during scanning cdrom and loading additional components it fails. The installer will say it failed to read files from the cd, try again or no. What's weird is that when the error pops up, the cd stops spinning, like it can't read it. The progress bar has been at different locations. 

**Questions:**
*I am going to put in a 120gb sata parititon that will be hooked up to a pci sata card with the VIA VT6421L chipset which is where i will be installing wubi. Will this work? (NOTE:I did extensive research to make sure I got a chipset that was supported by dapper and on. according to this: [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)  that chipset has been supported by libata since the middle of 2005). 
*Should I run the .exe when it's stored on the sata drive or do I put the .exe on the 4gb partition with windows and run it from there?
*I have read that this takes up 16gb of space, is there a point it's going to ask me where I want to install the 16gb of files?
*What should the 120gb sata drive be formatted as, would fat32 be better than ntfs?
*Is the installer going to allow me to shrink it and make the /swap and / partitions just like the real installer or should I prepare the drive first with my gparted live cd?
*kind of off topic, how come puppy works fine but edgy live cd doesn't
*hypathetical question: why can't all distro's just use the same base to ensure maximum hardware compatibility?
*I think that Puppy is debain based, would i be able to use ubuntu's repos within a Puppy hdd install if I can't get ubuntu to work on this machine?
*Would I at least be able to install ubuntu packages (.deb) or would this just cause a dependency nightmate? thanks again.

**attempted solutions:** all combinations of noapic, nolapic, irqpoll, pci=irqroute that you can possibly think of
break=bottom (trick where it breaks out into the intramfs at the command line, then edit xorg.conf blah blah)
redownloaded it
verified checksum
verified cdr "media" is readble by cd-rom thru windows 2000
changed from 40wire to 80wire ide cables on both ide channels
open cdrom door and sprayed it with air to try to clean it out
changed cdrom from cable select to master



THanks for anyone's help and any answers to the many questions.

---

### Post by ecology2007 on 2007-04-06
Can you edit your post with and make it more readable ?

---

### Post by ecology2007 on 2007-04-06
> **dannyboy79 said:**
> i am having a hell of a time trying to get edgy or dapper installed on an emachine. (have attempted both live cd's and alternate discs)

Current version of wubi only targets Feisty.
> if it matters i used the latest gparted livecd to shrink the NTFS parititon from 10.2 down to 4gb and I made a ext3 parition for ubuntu. (oops, forgot /swap at that time) 
You need at least 6 GB free on a NTFS partition to use wubi. The more the better.
> 
**First Issue with alt cd and boot options:**
installer told me it couldn't mount partition 1 (win 2000 install) to ANY mount point no matter where I tried. I just chose not to mount it.

I assume you know what you were doing, but i was not aware that the installation assistant allows you to mount non empty or NTFS partitions.

> 
**Second main Issue with alt cd and boot options:**
during scanning cdrom and loading additional components it fails. The installer will say it failed to read files from the cd, try again or no. What's weird is that when the error pops up, the cd stops spinning, like it can't read it. The progress bar has been at different locations. 
Then it is probably a CD error, did you check the integrity of the file you downloaded and of the CD you burned ?
> 
**Questions:**
*I am going to put in a 120gb sata parititon that will be hooked up to a pci sata card with the VIA VT6421L chipset which is where i will be installing wubi. Will this work? (NOTE:I did extensive research to make sure I got a chipset that was supported by dapper and on. according to this: [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)  that chipset has been supported by libata since the middle of 2005). 
Ago is currently working on adding a better SATA support for standard controllers.

> *What should the 120gb sata drive be formatted as, would fat32 be better than ntfs?

FAT32 used to be better, but feisty and wubi have now full read and write support for NTFS partitions.
> *Is the installer going to allow me to shrink it and make the /swap and / partitions just like the real installer or should I prepare the drive first with my gparted live cd?

No
> 
*kind of off topic, how come puppy works fine but edgy live cd doesn't
*hypathetical question: why can't all distro's just use the same base to ensure maximum hardware compatibility?
*I think that Puppy is debain based, would i be able to use ubuntu's repos within a Puppy hdd install if I can't get ubuntu to work on this machine?
Find puppy forum and post there?
> 
*Would I at least be able to install ubuntu packages (.deb) or would this just cause a dependency nightmate? thanks again.
apt-get is 100 % working.

> 
**attempted solutions:** all combinations of noapic, nolapic, irqpoll, pci=irqroute that you can possibly think of
break=bottom (trick where it breaks out into the intramfs at the command line, then edit xorg.conf blah blah)
redownloaded it
verified checksum
verified cdr "media" is readble by cd-rom thru windows 2000
changed from 40wire to 80wire ide cables on both ide channels
open cdrom door and sprayed it with air to try to clean it out
changed cdrom from cable select to master
Try wubi, if it does not work, give up and stop wasting time on this old computer, ubuntu will probably crawl.

---

### Post by dannyboy79 on 2007-04-06
> **ecology2007 said:**
>  You need at least 6 GB free on a NTFS partition to use wubi. The more the better.  When did this change, i just read that you 16gb is required, I am going to use the stable version (wubi-7.04-beta-v2.exe) , no beta for me. Is your statement still true?

> **ecology2007 said:**
> 
I assume you know what you were doing, but i was not aware that the installation assistant allows you to mount non empty or NTFS partitions. 
when you say installation assistant, you're talking about the alternate install cd installation process correct? during the partitioning stage, if you chose to do manual partitioning instead of guided you get way more control and you have to chose whether you want any partitions that already exist to be mounted and then where. the alt install cd is way better than the live cd install due to it's flexibility.

> **ecology2007 said:**
> 
Then it is probably a CD error, did you check the integrity of the file you downloaded and of the CD you burned ? 
yes. i had already stated that I verfied the checksum as well as check the cd for defects.
> **ecology2007 said:**
> 
Ago is currently working on adding a better SATA support for standard controllers.
that doesn't answer my question unfortunately. where should I store/run the .exe from? also, will wubi allow me to install fiesty onto a sata hard drive? if so, which chipsets are currently supported? 

my question was, "Is the installer going to allow me to shrink it and make the /swap and / partitions just like the real installer or should I prepare the drive first with my gparted live cd?"
> **ecology2007 said:**
> 
No
your answering no to what? i thought the point of forums were for all of us to help each other. this doesn't help me at all. you could have informed me that it doesn't even install onto a partiiton but into a image file.

> **ecology2007 said:**
> Try wubi, if it does not work, give up and stop wasting time on this old computer, ubuntu will probably crawl.  I read the faq, it says you can change to any other desktop environment you want. Is that true or not?? Since you didn't code wubi with choices of xubuntu, ubuntu, or kubuntu. i'll just install ubuntu and go with my desktoip of choice.

thank you for your help. this looks like a promising solution to get more windows people to test drive linux without scaring them of partitioning!! great work.

---

### Post by MethodOne on 2007-04-06
> *I think that Puppy is debain based, would i be able to use ubuntu's repos within a Puppy hdd install if I can't get ubuntu to work on this machine?Puppy is not Debian-based.  It is made from scratch.  It does support installing debs using Busybox's version of dpkg, but I don't recommend it.  Also, Puppy doesn't come with APT, but instead uses its own custom package manager.

---

### Post by dannyboy79 on 2007-04-06
> **MethodOne said:**
> Puppy is not Debian-based.  It is made from scratch.  It does support installing debs using Busybox's version of dpkg, but I don't recommend it.  Also, Puppy doesn't come with APT, but instead uses its own custom package manager.

thank you very much for responding with a little bit of effort. some people just tell you to go somewhere else and I don't feel that reflects the true sence of the open source world.

---

### Post by ago on 2007-04-06
There is a new minefield if you want to try [http://www.cutlersoftware.com/ubuntusetup/devel/minefield/wubi-7.04-beta-minefield12.exe](http://www.cutlersoftware.com/ubuntusetup/devel/minefield/wubi-7.04-beta-minefield12.exe) 

In this one you will find your windows partition automatically mounted under /media/host. Moreover it should allow to upgrade the kernel (thanks also to tuxcantfly work). Those were probably the 2 most requested features. + there are several fixes in lupin and wubi. Have a go.

EDIT: Updated the link to Minefield-12.

---

### Post by tuxcantfly on 2007-04-07
Whoops, seems like ago left out grldr (the bootloader) in minefield12, copy it over from another minefield build into C:\ or use an earlier minefield version for now, until I upload a minefield13 with the fixes...

---

### Post by tuxcantfly on 2007-04-07
alright, just uploaded minefield13 (the lucky number 13) which should fix the issue with minefield12 of grldr not getting copied to C:\

---

### Post by sandos on 2007-04-07
> **ago said:**
> There is a new minefield if you want to try [http://www.cutlersoftware.com/ubuntusetup/devel/minefield/wubi-7.04-beta-minefield12.exe](http://www.cutlersoftware.com/ubuntusetup/devel/minefield/wubi-7.04-beta-minefield12.exe) 

In this one you will find your windows partition automatically mounted under /media/host. Moreover it should allow to upgrade the kernel (thanks also to tuxcantfly work). Those were probably the 2 most requested features. + there are several fixes in lupin and wubi. Have a go.

EDIT: Updated the link to Minefield-12.

Wow, how does updating the kernel work? I cant imagine it working with regular apt-get? Would you somehow mount /boot to the correct NTFS place? Sounds like true magic ;)

---

### Post by ago on 2007-04-07
> **sandos said:**
> Wow, how does updating the kernel work? I cant imagine it working with regular apt-get? Would you somehow mount /boot to the correct NTFS place? Sounds like true magic ;)

yep you just use apt-get/update-manager as always. For the technically inclined, the initrd creation mechanism is modified so that lupin clones are generated instead of standard initrds (lupin clones can handle booting from loopmounted files), then the new kernel and initrd are copied to the c:\wubi\. A bit like star wars... ;)

---

### Post by sandos on 2007-04-07
> **ago said:**
> yep you just use apt-get/update-manager as always. For the technically inclined, the initrd creation mechanism is modified so that lupin clones are generated instead of standard initrds (lupin clones can handle booting from loopmounted files), then the new kernel and initrd are copied to the c:\wubi\. A bit like star wars... ;)

Ok, cool. Now I aways have to move wubi to my D:\ partiton, and this seems to misdetect the /boot/host softlink (Maybe because I still have a copy of wubi on C:, I know I should not) . Is pointing this to the right place enough to safely allow updating kernels or are there other things I should do?

---

### Post by mwilley on 2007-04-07
> **ago said:**
> The error should be below, when trying to find the host folder and trying to mount the host device.

Okay then, this comes up right before the "could not find host..."
```
update progress
[-d/dev/.initramfs]
[-z5]
PROGRESS_STATE=6
echo PROGRESS_STATE=6
[-x/sbin/usplash_write]
/sbin/usplash_write PROGRESS 6
return 5
```

If you need code farther up, I can get that (if this code is useless).

---

### Post by tuxcantfly on 2007-04-07
alright, since minefield13 appears to be working fine, I've released it as beta-v3, download from [http://cutlersoftware.com/ubuntusetup/latest.html](http://cutlersoftware.com/ubuntusetup/latest.html) source at [http://cutlersoftware.com/ubuntusetup/latest-src.html](http://cutlersoftware.com/ubuntusetup/latest-src.html)

---

### Post by ago on 2007-04-07
> **sandos said:**
> Ok, cool. Now I aways have to move wubi to my D:\ partiton, and this seems to misdetect the /boot/host softlink (Maybe because I still have a copy of wubi on C:, I know I should not) . Is pointing this to the right place enough to safely allow updating kernels or are there other things I should do?

The link is generated automatically when you boot so that if you move/rename the wubi folder the link should still hold water. Any changes to the link will be overridden on next reboot. Having 2 installations on C: and D: does not help much... Just rename one of the 2 to wubi.old to avoid problems.

---

### Post by ago on 2007-04-07
I forgot to mention that since minefield12/beta3 we include the sparkling new hampus plugin which makes it possible (among other things) to resume an interrupted download.

---

### Post by dbgeezer on 2007-04-09
OK, I'm up on minefield 13.  Looking good so far.

However, I have to say I'm still having problems, though they are no fault of this team's.    I'm reporting them here because they will have an impact on the stated goal of this project.

1. After the final reboot, my system comes up in the command line.  It won't start xserver.  In order to start xserver, I have to, at minimum, do a dpkg-rconfigure and answer the questions.  Then I get a 1024X768 screen until I can apt-get update and install my ATI Radeon X1300 driver.
2. I can't get a wireless connection from the command line. (Wired seems to come up automatically everytime try it, but only if it's plugged in when I'm building it.)  
   a.) If I modify preseed, the correct values for networking, static IP, gateway, etc. are in interfaces, but the network doesn't come up.  I have to use ifup.  Then I have connectivity to my wireless unit, but not beyond through the gateway.
   b.)  As soon as I get into xwindows, everything comes up on the wireless, including external internet connectity.
3. Each new version I modify preseed as follows
   a.) Enable universe, restricted and backports in apt. [Can we make this the default?]
   b.) insert my static ip address, gateway, subnet mask, dns server, essid and wireless key (we use wep on campus here) in networking [see above for the results]
   c.)switch xwindows from autodetect to vesa [see above for the results]

Although I'm relatively new to Linux, I've been working on microcomputers for almost thirty years, so I was able to figure this out.  However, I don't think that the average user would be able to do so; AND THAT will be harmful to this project.  We must get it to a point where it works for most everyone transparently.  (My system is a Dell Inspiron E1505 with an Intel 3945 wireless card and an ATI Radeon X1300.  I think that this a pretty generic machine).

I've started poking around in the source, looking at preseed.nsh.  Would it be worth it to try and pull all these values from Windows to build into preseed?   I'm not currently convinced that configuring from preseed works (see above), but perhaps I'm misunderstanding some things.

These are the last two problems that I'm facing.  Otherwise, I think that this product is ready to go from my testing.  Good job to-date;)

---

### Post by ago on 2007-04-09
> **dbgeezer said:**
> 
   a.) Enable universe, restricted and backports in apt. [Can we make this the default?]

We will try to make that default, I do not think that backports should be included though.

> 
   b.) insert my static ip address, gateway, subnet mask, dns server, essid and wireless key (we use wep on campus here) in networking [see above for the results]

We can probably autodetect static IP, subnet, gateway of default interface. It would not be possible to get the wirless key anyway. 
 
> 
  c.)switch xwindows from autodetect to vesa [see above for the results]

Possibly preinstalling the restricted modules package might fix the problem. I'll have a look. I am ideologically against that, but if X does not work at all...

---

### Post by tuxcantfly on 2007-04-09
> Enable universe, restricted and backports in apt. [Can we make this the default?]

Universe and restricted are already enabled by default in feisty, but backports are unsupported software, and kinda unstable/prone to breakage, so no
> 
switch xwindows from autodetect to vesa [see above for the results]

Shouldn't be necessary; with this (should be in feisty) [https://blueprints.launchpad.net/ubuntu/+spec/bullet-proof-x](https://blueprints.launchpad.net/ubuntu/+spec/bullet-proof-x) X should work no matter what, and with that nifty new restricted drivers manager, getting nvidia/ati drivers set up is pretty easy.

---

### Post by danbutter on 2007-04-09
> **tuxcantfly said:**
> and with that nifty new restricted drivers manager, getting nvidia/ati drivers set up is pretty easy.

Are the nvidia drivers supposed to work now?
As of minefield 13 they still don't work for me.

I am using an HP dv9000t with the G70 or 7600 and the restricted drivers manager sees that I have an nvidia card, but when I hit enable, nothing happens.
If I type out the sudo nividia-glx config enable  (or whatever it is...I don't remember exactly right now) i can never get back to a gui as the xserver is broken as soon as I try to enable the drivers.

Nothing I have tried has gotten the nvidia drivers to work.

They work on this computer though as mepis and vector live cd's have worked great with this laptop and loaded the nvidia drivers.

---

### Post by mabo06 on 2007-04-10
Just installed the Wubi ubuntu-7.04-beta-alternate-i386. After installing and reboot i only come to a promt saying

dhcppc0 login

No matter what i type ubuntu does not start as the earlier software did

What is this?

---

### Post by sandos on 2007-04-10
> **danbutter said:**
> Are the nvidia drivers supposed to work now?
As of minefield 13 they still don't work for me.

I am using an HP dv9000t with the G70 or 7600 and the restricted drivers manager sees that I have an nvidia card, but when I hit enable, nothing happens.
If I type out the sudo nividia-glx config enable  (or whatever it is...I don't remember exactly right now) i can never get back to a gui as the xserver is broken as soon as I try to enable the drivers.

Nothing I have tried has gotten the nvidia drivers to work.

They work on this computer though as mepis and vector live cd's have worked great with this laptop and loaded the nvidia drivers.

This might actually be a Ubuntu bug, and not a wubi bug. For some reason, after I upgrade using apt-get the restricted manager "forgets" that I can enable Nvidia at all. But I manually installed Nvidia-glx before and that itself complained about a missing lib, but I cant remember the name of it right now I am afraid.

---

### Post by Spegelius on 2007-04-10
I tested the kernel autoupdate and seems to be working. I didn't use latest Wubi-package, as i tested this on my laptop, which has wubi-herd4-v1 Feisty installed. I've been 'upgrading' it by recompiling the lupin kernel every now and then from latest bazaar sources and did it also this time. I noticed that linux and initrd were moved to /wubi/boot and i needed to install the lupin-package.deb to get kernel workin. Also menu.lst needed some changes obviously. Now it's working dandy and uname -r indicates latest kernel installed.

I did try installing latest Wubi on my main machine. I noticed that minefield13 and beta-v3 do not have initrd.gz and linux in /wubi/boot? is this normal, or have i understood something wrong?

Anyway, installation to my main pc went without errors. The problem with my pc and Feisty is that Feisty beta freezes when login screen shows (or actually it does that little before that. I cannot input anything). This error happens even when Feisty is installed normally, so it isn't Wubi related. I did manage kinda to get to the system by adding break=bottom to menu.lst. Also hitting ctrl+alt+del little after 'Reading files needed to boot...' seems to break loading some processes and allows me to login and use the system to some extent, allthough lot of things do not work (as processes aren't started...). I think i'll have to do some experimenting about the processes (a breakpoint approach would be nice), but i'm affraid it might be something about the kernel (or the restricted modules... maybe my bluetooth keyboard and mouse?). Anyway, this begins to be off-topic.

The newest lupin seems really well working, it boots fast and seems stable. Nice work. I actually did some quick testing and got some older version modified to install Edgy. But the Edgy installer complained something about not finding restricted modules, hence devices didn't work and the installation was botched up... didn't bother trying to find reason for that as final Feisty should be released at some point and i hope it fixes my problem.

---

### Post by ago on 2007-04-10
> **Spegelius said:**
> 
I did try installing latest Wubi on my main machine. I noticed that minefield13 and beta-v3 do not have initrd.gz and linux in /wubi/boot? is this normal, or have i understood something wrong?
You understood correctly, simply, there have not been new builds yet on latest sources.

---

### Post by sandos on 2007-04-11
> **sandos said:**
> This might actually be a Ubuntu bug, and not a wubi bug. For some reason, after I upgrade using apt-get the restricted manager "forgets" that I can enable Nvidia at all. But I manually installed Nvidia-glx before and that itself complained about a missing lib, but I cant remember the name of it right now I am afraid.

My Nvidia problems were solved by the apt-get upgrade I did just now. You might want to try if this solves your problem as well.

---

### Post by hamishaus on 2007-04-13
Hi

More feedback. Using Beta Version 3.

* The username issue is NOT fixed. In the Wubi installer I put in the username: Hamish, and the Ubuntu installer threw an error again.

* NTFS-3g works really well! :-)

* There were 351 updates, but a few of them did not install. Not sure if this was a Wubi issue or an Ubuntu issue. End of the installation as follows:

E: ttf-opensymbol: subprocess post-installation script returned error exit status 65
E: openoffice.org-core: dependency problems - leaving unconfigured
E: openoffice.org-common: dependency problems - leaving unconfigured
E: openoffice.org-style-crystal: dependency problems - leaving unconfigured
E: openoffice.org-style-industrial: dependency problems - leaving unconfigured
E: openoffice.org-calc: dependency problems - leaving unconfigured
E: python-uno: dependency problems - leaving unconfigured
E: openoffice.org-writer: dependency problems - leaving unconfigured
E: openoffice.org-draw: dependency problems - leaving unconfigured
E: openoffice.org-impress: dependency problems - leaving unconfigured
E: openoffice.org-java-common: dependency problems - leaving unconfigured
E: openoffice.org-filter-mobiledev: dependency problems - leaving unconfigured
E: openoffice.org-base: dependency problems - leaving unconfigured
E: openoffice.org-gtk: dependency problems - leaving unconfigured
E: openoffice.org-gnome: dependency problems - leaving unconfigured
E: openoffice.org-evolution: dependency problems - leaving unconfigured
E: openoffice.org-filter-binfilter: dependency problems - leaving unconfigured
E: openoffice.org-math: dependency problems - leaving unconfigured
E: openoffice.org: dependency problems - leaving unconfigured
E: openoffice.org-style-human: dependency problems - leaving unconfigured
E: openoffice.org-style-andromeda: dependency problems - leaving unconfigured
E: openoffice.org-style-default: dependency problems - leaving unconfigured

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb)
  403 Forbidden [IP: 91.189.89.6 80]

* I installed the Automatix for Feisty (recently released), but could not get the licence for Skype to go forward when I got the licence screen. Again, not sure if Automatix or Wubi or Ubuntu issue, but thought I'd mention it

Hope this helps,
Hamish

---

### Post by tuxcantfly on 2007-04-13
> There were 351 updates, but a few of them did not install

This is natural; wubi is using the still-unreleased feisty, so until april 19 (when feisty's released), the feisty updates might still cause breakage; after that, there should be few problems. This issue affects all feisty users; not a wubi issue.

> I installed the Automatix for Feisty (recently released), but could not get the licence for Skype to go forward when I got the licence screen. Again, not sure if Automatix or Wubi or Ubuntu issue, but thought I'd mention it

From what I hear on these forums, Automatix is rather breakage-prone (screws up updates due to changes to sources.list, tinkers with system internals), and it's also completely unsupported, so you really shouldn't be using it, especially since now in feisty codec installation and graphics card configuration are far easier and less error-prone with the user-friendly, built-in tools. It's an issue with automatix, not ubuntu; if you want to install skype, just follow the instructions for debian/ubuntu at [http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

---

### Post by Spegelius on 2007-04-14
I'm having a problem: i get some errors during booting. Some folders cannot be mounted and booting is halted with 'kernel panic: Attempted to kill init!'.

At first i thought that the errors happen because i built lupin kernel based on linux-image-2.6.17-386 as opposed to -generic kernel. But trying to boot the -generic kernels that have been working ok before, produces the exact same error. The reason for building -386 based lupin is that i noticed that the Edgy installation problem (not finding kernel modules) is simply caused by the fact that Edgy's init is based on -386 kernel.

I've re-generated all disk images, defragged hd etc.

edit: nevermind, got it working. Seems that Edgy's iso was messed up (maybe by me when fooling around in Edgy's installer command prompt...). Anyway, now i have Edgy installed with lupin, but the installation seems unfinished as it booted to linux kernel, not to login screen. Maybe the preseed doesn't work properly with Edgy or something?

---

### Post by Spegelius on 2007-04-14
Ok, re-installedwith fresh preseed.fg (taken from latest package). Apparently the one i was using before had some error which prevented proper install. Now all works like it should and i've full lupin-Edgy working. Great.

---

### Post by danbutter on 2007-04-14
> **sandos said:**
> My Nvidia problems were solved by the apt-get upgrade I did just now. You might want to try if this solves your problem as well.

Thanks for the tip, it worked perfectly after doing this AND letting the update manager do what was left.  
MUCH better desktop experience for me now.

Haven't even gotten around to installing beryl again.  
The built in desktop effects are holding me over nicely however.

---

### Post by tomcat23a on 2007-04-17
Hey, i'm still not able to shutdown properly due to umount2 errors or something about not being able to unmount loop7... any suggestions on how to post the shutdown log here?

---

### Post by ago on 2007-04-17
all logs are in /var/log, see syslog, messages, kernel.log

Can you pls also post the output of

ls -al /etc/rc6.d

and of /etc/init.d/fixsendsigs

---

### Post by tomcat23a on 2007-04-17
Can't find anything in the logs... can't find the messages from the shutdown there... probably because I'm seeing errors from the filesystem shutting down in the wrong order. I get a message about 'remounting filesystem read-only and then it hangs for a very long time.  (And Thanks again!)

ls -al /etc/rc6.d
total 20
drwxr-xr-x   2 root root  4096 2007-04-16 23:13 .
drwxr-xr-x 123 root root 12288 2007-04-17 09:52 ..
lrwxrwxrwx   1 root root    13 2007-04-06 17:48 K01gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root    17 2007-04-06 17:46 K01usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root    17 2007-04-16 23:13 K09apache2 -> ../init.d/apache2
lrwxrwxrwx   1 root root    15 2007-04-06 17:46 K19hplip -> ../init.d/hplip
lrwxrwxrwx   1 root root    15 2007-04-16 13:21 K19samba -> ../init.d/samba
lrwxrwxrwx   1 root root    16 2007-04-06 17:45 K20apport -> ../init.d/apport
lrwxrwxrwx   1 root root    20 2007-04-06 17:39 K25hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx   1 root root    20 2007-04-06 17:40 K50alsa-utils -> ../init.d/alsa-utils
-rw-r--r--   1 root root   353 2007-04-10 14:45 README
lrwxrwxrwx   1 root root    18 2007-04-06 17:50 S01cpkernel -> ../init.d/cpkernel
lrwxrwxrwx   1 root root    41 2007-04-06 17:40 S01linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
lrwxrwxrwx   1 root root    21 2007-04-06 17:50 S10fixsendsigs -> ../init.d/fixsendsigs
lrwxrwxrwx   1 root root    22 2007-04-06 17:40 S15wpa-ifupdown -> ../init.d/wpa-ifupdown
lrwxrwxrwx   1 root root    18 2007-04-06 17:39 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx   1 root root    17 2007-04-06 17:39 S30urandom -> ../init.d/urandom
lrwxrwxrwx   1 root root    22 2007-04-06 17:39 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx   1 root root    20 2007-04-06 17:50 S32umounthost -> ../init.d/umounthost
lrwxrwxrwx   1 root root    18 2007-04-06 17:39 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx   1 root root    20 2007-04-06 17:39 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx   1 root root    16 2007-04-06 17:39 S90reboot -> ../init.d/reboot
lrwxrwxrwx   1 root root    20 2007-04-06 17:50 S99killntfs3g -> ../init.d/killntfs3g

---

### Post by ago on 2007-04-17
press ctrl+alt+f2 to get a terminal

You should should run manually all the commands in rc6.d in alphabetical order and with the "stop" argument.  

cd /etc/rc6.d
sudo sh K01gdm stop
sudo sh K01usplash stop
...

see which one fails and write down the error

---

### Post by Dave_Man on 2007-04-18
Hi, 

I've successfully installed Ubuntu using wubi on my other computer.
only problem I've had was the windows installer kept crashing with memory allocation errors, but once I got the download to start, it was all perfectly smooth.

Suggestions for improvement:
1. Allow me to choose how much HD space to dedicate to it.
2. For some reason it only auto mounts drive D: and not drive C:. It should be fixed.

Thats it.
I think this is a much better way to install Ubuntu for all dual booters and I'll recommend this method to all my friends.

Dave.

---

### Post by ago on 2007-04-18
> **Dave_Man said:**
> Suggestions for improvement:
1. Allow me to choose how much HD space to dedicate to it.
2. For some reason it only auto mounts drive D: and not drive C:. It should be fixed.


In the new version you will be able to select both hd space and drive. At the moment the installation drive is selected based on the amount of free space, if it defaults on d: is because it does have more free space. If possible I would like to have more info on the memory errors.

---

### Post by Aquashark on 2007-04-19
Questions:

1. Is Wubi working with Ubuntu 7.04 Final?
2. Will i be able to install video drivers without screwing up the install?
3. Is the drive where Ubuntu has been installed automounted at startup?
4. Does the system reboot without errors?

---

### Post by ago on 2007-04-19
> **Aquashark said:**
> Questions:

1. Is Wubi working with Ubuntu 7.04 Final?

Not at the moment, we have some changes to finish then we will start pushing out minefields which will work with final, then, if all goes well, we will update the official link. The first minefields will come out fairly soon. Or you can use betav3 and upgrade. But I imagine that the servers will be quite overloaded for a few days, so the best option now is to wait for the minefields.

> 2. Will i be able to install video drivers without screwing up the install?
You should be able to do that already. Of course that does not mean that when working in sudo mode the system is bork-proof, it only means that wubi installations have almost identical behaviour to actual ubuntu installations (the only differences are necessary ones to make the initrd boot/reboot properly from a loopfile as opposed to a real partition).

> 3. Is the drive where Ubuntu has been installed automounted at startup?
Yes

> 4. Does the system reboot without errors?
So far there was only one user that mentioned some reboot issues but we did not hear back from him (see a few posts back) and we do not know exactly what was the reason, all tests on my machines with betav3 went fine so far and other users reported positive feedback.

---

### Post by tuxcantfly on 2007-04-22
new release, wubi-7.04-v1, no changes whatsoever compared to beta-v3, just that it's now using the final feisty release, not the feisty beta

it has received little testing, due to the urgency of the release (beta isos are no longer available) so note that it might not work

---

### Post by Jimbob7 on 2007-04-22
tuxcantfly, do you have a link to the latest version?  The wubi site still has v3 beta for download.

Thanks.

Edit, don't worry, I've found it.

---

### Post by frenchy82 on 2007-04-22
Hello,

I tried to install with this new version.
The install start nice then download the iso file, then checksum and download again iso, chechsum, ...

Maybe i should first download the iso and put it in c:\wubi\install

---

### Post by Antimethod on 2007-04-22
I installed ubuntu with the new release of wubi and it worked just fine!
thanks!

---

### Post by ago on 2007-04-22
> **tuxcantfly said:**
> new release, wubi-7.04-v1, no changes whatsoever compared to beta-v3, just that it's now using the final feisty release, not the feisty beta

As mentioned by tux note that the above does not include all the code which is supposed to go in the final (new drives, support for raid0, migration assistant, localization etc...), it's only the old code recompiled so that it can work with the new final ubuntu ISO, we would have normally waited but we had to push out a release since the beta ISO is no longer available on the servers.

I have renamed it to wubi-7.04-final-minefield1 to avoid confusion, since that uses Ubuntu final ISO, but it is not our final version. You can access that from the wubi website. Again, we would not normally put a minefield on the website, but we did not have much choice.

---

### Post by Spegelius on 2007-04-22
I tried building my own kernele from latest stable vanilla sources and it seems to be working on my laptops Feisty installation. The resulting initrd is 4.5MB ins size. I also tried this on me desktop PC's Edgy installation, kernel compiled ok but during boot i get error message:
FATAL: install of fuse failed
no block devices

I also tried to manually install Uli's SATA driver. The installation package has the module precompiled for different distros and Suse 9.2-folder contains only module for kernel 2.6. Insmod complains about incompatible module format. So no dice on that front. Gonna convert my RAID0 setup to dynamic disk and see if that works for me.

---

### Post by ago on 2007-04-22
If you know how to build your own initrd from lupin sources, the modules are in src/initramfs/modules. Start adding raid0, you can use normal tools (lsmod & co to find out other required modules). If you manage to get raid0 working let us know.

---

### Post by frenchy82 on 2007-04-22
Hello,

Finally it works very fine. I just have to download the iso on my desktop and then launch wubi

Many thanks for it

---

### Post by dannyboy79 on 2007-04-23
cutlersoftware sites posted in thread 1 of this thread are dead.

---

### Post by Aquashark on 2007-04-23
the install process doesn't start here.
it stops shortly after boot with a loading message

earlier versions worked fine.

---

### Post by ysuire on 2007-04-23
Yes, i have the same problem

---

### Post by varchar255 on 2007-04-23
> **Aquashark said:**
> the install process doesn't start here.
it stops shortly after boot with a loading message

earlier versions worked fine.

I have the same problem here. I had installed wubi-7.04-beta-v3.exe successfully, then I downloaded the final ubuntu alternate iso and ran wubi-7.04-minefield2.exe and selected the reinstall option. After rebooting it got stuck on the "Loading" message. I edited menu.lst and changed "quiet" to "splash" and the startup output got stuck when it said "waiting for root file system" (or something similar, I forgot the exact text but I know it mentioned "root"). Booting back into Windows, I ran the defragmenter but it finished and said that root.img could not be defragmented.

Hope that means something to you...I had Feisty beta installed but something is wrong with the Update Manager (it always crashes before finishing) so I am looking forward to using Wubi to install the final version.

---

### Post by Spegelius on 2007-04-26
> **ago said:**
> If you know how to build your own initrd from lupin sources, the modules are in src/initramfs/modules. Start adding raid0, you can use normal tools (lsmod & co to find out other required modules). If you manage to get raid0 working let us know.

I've been trying to get Raid0 working. First, proper driver support for my chipsets raid OR support in dmraid package would be required to get the Uli raid0 to work in linux. Problems:
- driver module in driver package downloadable from Uli's homepage isn't compatible with Ubuntu and no driver source available. Linux kernel has sata_uli.ko, but this driver doesn't support RAID. It is loaded in boot, but module is not used by my mobo's chipset, as it works in AHCI mode. Anyone know how to de-engineer a driver module :)
- dmraid doesn't support Uli metadata. A request for it has been apparently made, but no progress on that front. dmraid source is available and contains instructions to build your own metadata support, but i'm Labview coder, not C and i don't understand all requred aspects of RAID functions to code my own functions. Still, I could fiddle around with the RAID set as it is empty right now, i could see what data (metadata) is written to the disks when RAID is set up.

So i removed Uli RAID0, disabled raid ROM entirely and created a Windows software RAID0 setup, with default parameters.
In here [http://www.linuxquestions.org/questions/showthread.php?t=345232&page=2](http://www.linuxquestions.org/questions/showthread.php?t=345232&page=2) is a good example of how things should work. Also this document outlines another two appreaches for LDM raid support: [http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt)

Good news is that the Edgy installation i'm using detects LDM disks (dynamic disks) properly. Bad news is that above RAID creation procedures fail to properly setup the array, because i cannot mount the created RAID array in linux. NTFS-3G complains that cannot read last sector or NTFS fs not found. Kernel NTFS mounts the RAID, but produces errors when trying to read.

I'm gonna try installing Feisty (hopefully the freeze bug from Feisty beta release is fixed). It might be that Edgy's kernel doesn't properly support something and causes this (OTOH, the first example above does use Edgy...).

---

### Post by Spegelius on 2007-04-27
Installed Feisty with minefield2 installer. Same freeze bug as with previous versions, but i got it figured out. Turns out it's not a freeze state, but a misdetection of my bluetooth mouse and keyboard; removing and re-attaching USB cable fixes this and Feisty works... never thought of that before :).

Anyway, situation with RAID0 has not changed. Allthough installing the dmraid and mdadm package from Feisty repos automatically finds and activates my RAID0 (which i had to do manually in Edgy), i still can't mount the bloody thing. No NTFS etc etc blah blah yadda yadda... i'm beginning to wonder if Windows 2003 has some kind of perverted version of the dynamic disk RAID (no such note in M$ documents...). I know Vista has newer version of dynamic disks and current kernel might not support it, but i haven't booted to Vista for 2 months (so i find it hard to believe that it would somehow screw Win2003 to create unsupported RAID sets...).

---

### Post by tuxcantfly on 2007-04-29
if anyone's interested in installing a standard Ubuntu to a dedicated partition, rather than a loopmounted file, without using a CD, see here:

[http://ubuntuforums.org/showthread.php?t=427793](http://ubuntuforums.org/showthread.php?t=427793)

Note that this version, wubi-netboot, isn't one of the official wubi releases, and has much less functionality (no autodetection); it was simply designed so that it can be possible to make a stock ubuntu install without a CD.

Wubi-netboot is simply intended to be a temporary solution to provide the functionality of creating a real install on a partition, until Wubi has added these features

Ask questions about wubi-netboot in the linked thread if you have issues

---

### Post by ecology2007 on 2007-05-04
7.04 minefield 3 is out. If wubi is allready working for you, there is no need to upgrade.
[http://ubuntuforums.org/showthread.php?t=432808&highlight=minefield](http://ubuntuforums.org/showthread.php?t=432808&highlight=minefield)

---

