---
title: "How to tell what process is automounting a USB flash drive when its not in fstab?"
date: 2014-10-16
forum: General Help
---

### Post by landstander on 2014-10-16
**_Note:_** I did the usual web and forum search and I couldn't find anything related to the strange mounting behavior the USB drive is being treated with here.

**_Specs:_**
**OS:** Lubuntu (login session installed on top of a default install of Ubuntu 14.04 64bit /w a Gnome3 desktop as its default)
**Desktop:** Lubuntu
**Window Manager:** Openbox

**_Description of Problem:_**
Even though its not listed in "/etc/fstab", it appears that randomly (or maybe every time I login to a session) a USB flash drive that I have plugged into the computer gets automatically mounted by something on the path:
/media/username/USBStick

Every time I unmount this drive, I delete the "/media/username" directory (where "username" is of course whatever username I have assigned myself for the login session), but whatever is mounting this drive is recreating this directory before it mounts it there. To me this seems like it suggests that there is reference in a file someplace that is being used by whatever part of the OS is mounting this drive and this file is not "/etc/fstab" because the mount point shown above doesn't exist in that file.

**_Questions:_**
**1.)** I only want this USB drive to be mounted when I tell it to be mounted. How can I stop it from being automatically mounted? The answer to this might be in "man fstab" so I'll look that up again for the trillionth time while I wait for answers.
**1.)** There are some programs that that depend on this USB drive being mounted in a specific location, is there a way to change whatever file is being referenced or whatever is auto-mounting this drive so that when this auto-mounting problem does occur it at least mounts it at the correct location?

---

### Post by cariboo on 2014-10-16
External media are mounted using autofs and automount. For more info have a look at this wiki page:

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

---

### Post by landstander on 2014-10-20
cariboo907

I just checked and autofs is not installed on my system. This means that "automount" which is part of the autofs package can not be doing any auto mounting since it isn't installed.

In fact I also did a search in synaptic for "automount", and non of the packages listed in this search result are installed.

Is there anything else that could be causing this?

---

### Post by oldfred on 2014-10-20
Then is is probably udisks or udisks2. Not sure what Lubuntu has.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by nerdtron on 2014-10-20
I think this is still relevant since the original install is Ubuntu 14.04 [http://askubuntu.com/questions/89244/how-to-disable-automount-in-nautiluss-preferences](http://askubuntu.com/questions/89244/how-to-disable-automount-in-nautiluss-preferences)

---

### Post by Dennis N on 2014-10-20
> **oldfred said:**
> Then is is probably udisks or udisks2. Not sure what Lubuntu has.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Yes - Lubuntu, Ubuntu, and Xubuntu all use udisks2 which automounts removable media at /media/username/xxxxx

How you can tell: Examine the output of **mount**
```
/dev/sdb4 on /media/dmn/Common-Files type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdc1 on /media/dmn/COMMON type vfat w,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
```
Note **uhelper=udisks2** - First line is a partition mounted by udisks2; second line is an external drive mounted by udisks2
In Xubuntu at least, you can prevent automouting of external devices from **Settings > Hardware > Removable Drives and Media**.

---

### Post by landstander on 2014-10-22
**oldfred, nerdtron, and Dennis N;**

**_[Things Learned:]_**
I've figured out that this problem only occurs after a reboot and not after a logout then login. After the reboot I do see the "uhelper=udisks2" at the end of the /media/username/USBStick mount point output for the USB drive when doing "mount -l" on the command line. This suggests that this is indeed a udisks2 problem.

**_[Things Tried:]_**
1.) After rebooting into a Gnome session to follow Dennis N's suggested "Settings > Hardware > Removable Drives and Media" path, I discovered that I have no "Removable Drives and Media" option listed in the Hardware section. Also in Lubuntu there is no "Settings" point to start from which is why I logged out and back into a Gnome session to follow your suggestion.
2.) I attempted to follow nerdtron's suggestion of disabling an "automount" option in deconf by following the suggestion given in the link posted in comment #5 above, and this seems to have had no effect. Seems as if that deconf / automount option has no effect on how udisks2 behaves. Note: I did double check dconf after the reboot to make sure the automount setting was still disabled and it was so... *shrug* :/

**_[Questions Remaining:]_**
1.) Where are the settings or configuration files located for udisks2? (After doing a quick search online it seems that udisks2 is receiving some complaints from the community, [http://igurublog.wordpress.com/2012/03/11/udisks2-another-loss-for-linux/]("http://igurublog.wordpress.com/2012/03/11/udisks2-another-loss-for-linux/"), this makes me wonder if there is even a way to stop udisks2 from automounting USB drives).
2.) I've read a post about forcing udisks2 via symbolic links to use "/media" by default instead of "/media/username" but this seems like a patch or a workaround and doesn't seem to address the issue that udisks2 is working outside the end users ability to decide how there system is operating on a more fundamental level. (Here is the link to the symbolic link method: [http://askubuntu.com/questions/214646/how-to-configure-the-default-automount-location]("http://askubuntu.com/questions/214646/how-to-configure-the-default-automount-location")). Is there a way to get rid of udisks2 all together without completely screwing up the OS, and are there any good replacements or substitutions for udisks2?

Thanks for the answers and the support. I'll look for a udisks2 replacement or substitution and I'll try and report back one what I can dig up.

---

### Post by Dennis N on 2014-10-22
The suggestion about looking at Settings > Hardware > Removable Drives and Media to turn off automounting only referred to Xubuntu. That's why I qualified it "at least in Xubuntu". 

I don't know of any configuration files for udisks2 that we can access as users. My impression is that it is not designed to be user configurable.

udisks (which mounts devices at the old location /media/xxxx) can be installed together with udisks2, but automounting is still done by udisks2. Replacing udisks2 with udisks for automounting external devices is beyond my knowledge.

---

### Post by landstander on 2014-10-22
**_[UPDATE:]_**
I still can't stop the usb drive from being automatically mounted on bootup.

**_[What has changed:]_**
I placed a line in /etc/fstab as follows:
```
UUID=$deviceuuid 	/media/USBStick 	ext3 	rw,suid,dev,exec,noauto,nouser,async
```
Where $deviceuuid is the uuid of the device being mounted (note: from the command line use "ls -l /dev/disk/by-uuid" to see a complete list of devices listed by uuid, to cross reference this list with the actual name of the device use "ls -l /dev/disk/by-label", from those two lists you should be able to discern the uuid for each device attached to the system.)

**_[Problems and partial solutions:]_**
Here is what "mount -l |grep USBStick" (from the command line) now reports after a reboot:
```
/dev/sde1 on /media/USBStick type ext3 (rw) [USBStick]
```
Here we can see that there is no reference to udisks2, so it seems as if this drive is being mounted directly from fstab. We can also see that the device is being mounted in the correct location now instead of the strange and problematic "/media/username" directory that udisks2 forces on any one that is bound by its use on there system. So fstab sort of solves that issue, however the problem with auto-mounting is still persistent. 

In the "What has changed" section above notice that I have given the "noauto" option for this device and yet it is still being automatically mounted even though "man mount" states that this should not be happening.

**_[Questions remaining:]_**
1.) WTF?
2.) How can we stop this drive from being automatically mounted by every single thing under the sun no matter what we do to stop it? (The only solution I can see is to leave it physically unplugged, which isn't good and doesn't work if for example one wanted to remotely administer the computer from some other physical location on the planet and had a need to mount that drive).
3.) Is the only solution to write a script that unmounts this drive on bootup? Even if we do this it will be annoying because the user would have to enter there password a second time for the unmount after the first time for the login each time they boot the computer. There has to be a better way to deal with this problem then this.

---

### Post by landstander on 2014-10-22
>  Dennis N

Re: How to tell what process is automounting a USB flash drive when its not in fstab?

    The suggestion about looking at Settings > Hardware > Removable Drives and Media to turn off automounting only referred to Xubuntu. That's why I qualified it "at least in Xubuntu".

    I don't know of any configuration files for udisks2 that we can access as users. My impression is that it is not designed to be user configurable.

    udisks (which mounts devices at the old location /media/xxxx) can be installed together with udisks2, but automounting is still done by udisks2. Replacing udisks2 with udisks for automounting external devices is beyond my knowledge. 

Thanks for the clarification, and suggestions.

...Still searching for a solution (see post #9 above).

---

### Post by landstander on 2014-10-22
**_[UPDATE:]_**
Strange behavior continues. I've changed fstab to this:
UUID=d56d5d73-9da0-48ab-a72a-1ceb6e1f2088 	/media/USBStick 	ext3 	rw,suid,exec,noauto,user,async

...and after a reboot "mount -l |grep USBStick" now reports this:
/dev/sde1 on /media/USBStick type ext3 (rw,noexec,nosuid,nodev,_netdev) [USBStick]

Notice the flagrant difference between the options I gave in fstab, and the options that were actually assigned by some ghost in the system shown above. What the hell is that all about? /etc/fstab states suid,exec,noauto, and it somehow gets mounted as the opposite of each of those???

I think my brain hurts now.

---

### Post by Dennis N on 2014-10-22
I did a one-off experiment to satisfy my curiosity: 

With Xubuntu 14.04, I plugged in an external USB hard drive before boot up. I found that the drive remained **unmounted** after log in, but was detected by the OS so cound be mounted manually from the command line, or the file manager. Both would be done by udisks2.

I then repeated this with Lubuntu 14.04. This time, the drive was **mounted** after log in - mounting done by udisks2.

Then, to be sure, I repeated again with Xubuntu and a USB flash drive this time. Again, like the external HD, the drive is **unmounted** after log in.

So this suggests the behavior depends on the desktop environment.

Useful?

---

### Post by landstander on 2014-10-22
> **cariboo907 said:**
> External media are mounted using autofs and automount. For more info have a look at this wiki page:

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

To be complete I just wanted to note that I did take a look at this, and it seems to have two problems:
1.) It uses complicated map files that are difficult to understand.
2.) It appears to only be about how and where things get automatically mounted, and the requirement here is to stop automatic mounting of a specific device. The link given doesn't appear to make any mention of this requirement so its unclear if autofs can be used in this way.

This raises a good point though. The thread title was only asking how to figure out which process was responsible for automatically mounting a device. We haven't completely figured that out as it seems like udisks2 "might" be taking priority over fstab even when fstab entries are being mounted, and I'm only stating this because udisks2 is notorious for doing things however it was programed to do them, and fstab should be working as instructed by the end user and this doesn't seem to be happening for fstab at the moment. See post 11.

---

### Post by landstander on 2014-10-22
> **Dennis N said:**
> I did a one-off experiment to satisfy my curiosity: 

With Xubuntu 14.04, I plugged in an external USB hard drive before boot up. I found that the drive remained **unmounted** after log in, but was detected by the OS so cound be mounted manually from the command line, or the file manager. Both would be done by udisks2.

I then repeated this with Lubuntu 14.04. This time, the drive was **mounted** after log in - mounting done by udisks2.

Then, to be sure, I repeated again with Xubuntu and a USB flash drive this time. Again, like the external HD, the drive is **unmounted** after log in.

So this suggests the behavior depends on the desktop environment.

Useful?


This seems like it might help to narrow this problem down a bit, but I'm not quite sure how yet.

**_[Questions:]_**
1.) Is there any way you might be able to check and report how the Lubuntu environment is different from the Xubuntu environment in terms of how things get detected and mounted?


**_[Things I've discovered:]_**
If you install the package "udisks2-doc", you can go to this file on your system: [file:///usr/share/gtk-doc/html/udisks2/udisks.8.html]("file:///usr/share/gtk-doc/html/udisks2/udisks.8.html")
For some reason that link is unclickable, so you'll have to copy and past it directly into your URL to get it to work.
From here if you scroll down to the section tittled "DEVICE INFORMATION" you can find an entry about a setting called "UDISKS_AUTO", which according to the material seems to suggest that the user could make a udev rule to stop automounting from happening.

I'm going to keep reading to see if I can make any sense of any of this.

---

### Post by landstander on 2014-10-22
**_[SOLUTION UPDATE:]_**
I've rebooted and the USB drive was not automatically mounted.

**_[Things I've changed:]_**
The "/etc/fstab" for the USB drive is now as follows:
```
UUID=d56d5d73-9da0-48ab-a72a-1ceb6e1f2088 	/media/USBStick 	ext3 	rw,user,suid,exec,async,noauto,x-udisks-auth
```
**_Note:_** I have essentially only changed two things, I moved the "noauto" argument to the right in case something else was over riding it, I also added an option to force udisks to ask for authentication before mounting this drive via the "x-udisks-auth" option in hopes that this would at least allow me to not authenticate after a system boot which would in effect not allow this drive to be mounted during boot. That last option "x-udisks-auth" might be completely unnecessary (See: [Solution:] below).

**_[How I discovered a solution:]_**
After following the instructions at the above web site, and noticing that there was a documentation package for udisks2 listed in synaptic as "udisks2-doc", I installed that package and started searching to find anything related to automounting. I then discovered the page linked to in post #14 above. It's not necessary for you to install that package or to read the file I'm pointing you to as I will summarize the solution below.

**_[SOLUTION:]_**
[LIST=1] 
[*] Go to this directory on your system (directory given by "man udev" first paragraph of "RULES FILES"):
```
cd /etc/udev/rules.d
```
[*] Create the file as explained here: [http://linux.derkeiler.com/Newsgroups/alt.os.linux.suse/2013-04/msg00055.html]("http://linux.derkeiler.com/Newsgroups/alt.os.linux.suse/2013-04/msg00055.html")
```
gksu gedit /etc/udev/rules.d/99-correct-media-mount-point.rules
```
[*] In the file created in the previous step, insert the following line into the document (**_IMPORTANT NOTE:_** This line is different from the one located at the link given in step 2 above, its important to get the last part of the line shown here):
```
ENV{ID_FS_USAGE}=="filesystem|other|crypto", ENV{UDISKS_FILESYSTEM_SHARED}="1", ENV{UDISKS_AUTO}="0"
```
**_Note:_** The UDISKS_AUTO option was found in the documentation given in post #14. I had to make an educated guess as to how to use it based on the information given in step 2 above. Setting UDISKS_AUTO = 0 turns off automatic mounting.


[*] When you first create this file, it should be empty unless some other process or person has already created this file. If someone or something (a program) has created this file on your system you need to talk to that person, or find out which program made the file and investigate how you might be able to change it so that it works as suggested here. If the file is empty when you first open it then the line shown in step 3 above should be the only line shown once step 3 is completed. At this point save and close the file.


[*] On rebooting the system, the USB drive should no longer be automatically mounted.
[/LIST]
**_[Summary:]_**
**_Goal:_** To find the process that was causing the USB drive to be automatically mounted and stop it from doing this.
**_Solution:_** It is unclear if this solution is the best method for doing this, but the above stated goal appears to have been reached. If the USB drive is plugged into the computer during boot up, and after the computer is booted and the user is logged in, this USB drive is available to be mounted but is not mounted automatically.
**_Possible drawbacks and problems:_** This may be happening for anything that I plug into the computer such as a camera or CD or other device or media which would definitely be undesirable behavior (I haven't tested this possible problem yet as I can't find anything else to plug into the computer at the moment). The documentation found and given in post #14 for udisks2-doc seems to suggest that the udev rules can be used to target a specific device which could solve this problem. At the moment I have no idea how to find that solution or the information that would lead to it.

I will keep this thread open for a bit to see if there are any addition comments or suggestions, especially about the "Possible drawbacks and problems" listed above. Baring that I will mark this thread as SOLVED soon.

**_[Thanks:]_**
Dennis N, thank you for sticking with with the thread. Your replies encouraged me to keep trying to find a solution.

---

### Post by Dennis N on 2014-10-22
Nice investigating!

My **[FONT=Courier New]/etc/udev/rules.d[/FONT]** only has a file 70-persistent-net.rules. There is also a README that explains this directory, and states that one can write their own rules to override behavior of "package supplied rules". The README also points to **[FONT=Courier New]/lib/udev/rules.d/[/FONT]** for "package supplied rules". Rules placed in **[FONT=Courier New]/etc/udev/rules.d[/FONT]** override those. That is what your 99 file does.

**[FONT=Courier New]/lib/udev/rules.d/80-udisks2.rules[/FONT]** actually contains the udisks2 rules and there are a lot of them, I see one section for "USB stick / thumb drives", but parsing the syntax is beyond me.

Maybe you can learn more from these.

This suggests the cause of the difference in behavior between Xubuntu and Lubuntu regarding automounting.

---

### Post by landstander on 2014-10-24
Dennis N,

I've been researching udev rules and tutorials since yesterday. Really heady stuff, sorta puts me to sleep after reading to much of it. Thanks for the information on "80-udisks2.rules" way cool! :D
Think I'll do a system search for ".rules" and udisks2 to see what I can come up with.

Just found this interesting shell script located here:
/usr/lib/udisks2/udisks2-inhibit

Inside this script it states the following:
> # Disallow udisks2 mount operations for anyone but root while a program is running.
# This is similar to udisks 1.x's "udisks --inhibit .." command.
# Author: Martin Pitt <martin.pitt@ubuntu.com>

That script does some nifty tricks that supposedly stay consistent across reboots. This could be useful for scripting other things as well.

---

### Post by landstander on 2014-10-24
Ok, marking this thread as solved.

According to the udev material there should be a way to target rules for a specific device so for example everything else gets auto-mounted except for that device on boot. However I've been to lazy to figure it out, but if I ever do get it figured out I'll try and pull together short tutorial on it and post it as a separate thread.

Thanks again for all the help encouragement and advice. I'm starting to learn to become better at researching some types of problems, and that wouldn't have happened if it wasn't for the patients and support of the community. Thank you! :)

---

