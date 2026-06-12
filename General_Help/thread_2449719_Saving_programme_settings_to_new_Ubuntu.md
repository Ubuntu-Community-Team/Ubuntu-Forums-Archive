---
title: "Saving programme settings to new Ubuntu"
date: 2020-09-01
forum: General Help
---

### Post by dorpapst on 2020-09-01
Kia Ora friends,
I am going to do a new installation of Ubuntu (from 20.04 to 20.04, but the old disk from the first installation was an emergency solution on a 32GB usb stick) and I would like to take all of the programme settings and configuration files to the new installation.
This means, I want to transfer all settings of the ubuntu installation and local settings like my thunderbird, firefox, sublime and VScode settings (and addons), as well as ssh-settings, terminal settings and ssh-keys.

I know that a lot of those things are saved within folders/files starting with a dot.
But is there a good way, how I can determine which of all of these are essential and which aren't? Are are they all (generally) in the /home/ folder? 

I just don't want to miss out important settings, while I also don't want to mess up my new PC with old, irrelevant stuff.

Sorry for the very confused thread, I hope I made clear what I want to do :D 

Thanks in advance!

---

### Post by TheFu on 2020-09-01
Backup your HOME, using a good backup too on a Linux file system - not NTFS or FAT32 or exFAT - those will not work.
On the new system, restore everything in your HOME.

The only settings stored outside HOME are system settings or system-wide configurations and programs.  Since you installed and modified those, you are expected to know where they are.  Most should be in /etc/, but since that directory area is customized per-system, caution is necessary in choosing which files can or cannot be restored.  I always include /etc/ in my backups, since files in there have my modifications. Those changes can be re-merged more easily when the differences are available.

As to what is irrelevant, nobody here can determine that for you.  Sorry.

---

### Post by dragonfly41 on 2020-09-01
I am jumping through similar hoops in copying settings from a previous heavily configured Ubuntu 18.04 over to a newly installed Ubuntu 20.04. There are subtle changes required since there are new packages in 20.04.

I am using **meld** by command line to compare old with new and to use this to help decide what to copy over.

First install meld.

**sudo apt install meld**

Then compare source /etc directory with destination /etc content.

Typically:

 meld /etc   <mounted-path>/etc

You can see visually differences between old and new .. *but it will not tell you what to copy over*.

==================================

[P.S.] Right now I am looking through differences in old and new /etc and there are many pointers to files which need to be installed.

Look for files which have lines through them indicating that they are in one OS but not the other. I can see that I have overlooked installing some packages I installed in 18.04 but not yet in 20.04.

---

