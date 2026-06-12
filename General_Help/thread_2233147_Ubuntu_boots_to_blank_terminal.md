---
title: "Ubuntu boots to blank terminal"
date: 2014-07-06
forum: General Help
---

### Post by Zefron on 2014-07-06
As title says, whenever I boot ubuntu  it loads into  blank terminal. Can type things but there has been no response to any commands.Changing kernel did not make a difference. 

This issue occured when I tried to shred some files that were in my trash that wouldn't delete (they were 3rd party spotify addons that enabled media keys) and it went to a blank screen, after 5 mins of waiting I manually rebooted.

Tried booting into failsafe mode and got this error: /usr/bin/X: error while loading shared libraries: /lib/x86_64-linux-gnu/libudev.so.1 : invalid ELF header.

I am running 64 bit Ubuntu 14.04, if I have left out any needed info please let me know.

Any help is appreciated, thankyou in advance.

Edit: Turned Grub boot messages on, boot console hangs after: [13.277085] mountall main process (181) terminated with status 127.
I also have access to the filesystem through an lubuntu livecd.
Edit 2: Have since attempted to fix by reinstalling 14.04 via livecd, more info in next post

---

### Post by yancek on 2014-07-06
First, did it ever boot?  Do you get a grub prompt:  grub>  or is it a blinking cursor or just a blank screen?
I don't see how shredding files in your Trash directory could cause this problem but we don't know how you did this.  Since it is a problem being unable to boot, running the bootinfoscript should provide useful information.  Just google 'bootinfoscript', go to the site and read the instructions in the Description box, download and run it and post the output, a RESULTS.txt file.

---

### Post by Bucky Ball on 2014-07-06
In the menu list at boot, choose the recovery kernel. Should be second on the list. When you get to the options, 'Fix broken packages'. Then drop to a shell (a terminal as root, is an option there) and:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Please report back any and all errors. You need to be online for this to work. 

The Spotify server has been problematic and quite a few people have been having issues with it. Might have something to do with that. Might not. When you get back to a desktop, I'd advised unticking that repo in Software Sources for the time being ... ;)

---

### Post by Zefron on 2014-07-07
I have since tried to reinstall 14.04 via live cd to no avail. Now whenever I boot this message comes up:
wait-for-root: error loading shared libs: libudev.so.1 : cannot open shared object file: No such file or directory
gave up waiting on root device
Alert! /dev/disk/by-uuid/81ea7805-024d-46c8-9114a67cbef9957f does not exist.
Dropping to shell.
Terminal has (initramfs) on it

When trying to enter recovery mode, it lists all my devices and then just stops. It lets me type things but it's a blank line and there's no response when I enter things.

I had to post the results of Bootinfoscript on pastebin because the size of the txt file exceeded the forum's limit.
[http://pastebin.com/tSEfqCLf](http://pastebin.com/tSEfqCLf)

---

### Post by Bucky Ball on 2014-07-07
Take the DVD out, go into the BIOS and make sure you are set to boot from the correct hard drive (sda or hd0, whichever is listed). Continue with boot. Any luck?

Just wondering why you did a complete reinstall instead of following the instructions in post #3 ... What you have now is effectively a new and different issue altogether ...

---

### Post by Zefron on 2014-07-07
> **Bucky Ball said:**
> Take the DVD out, go into the BIOS and make sure you are set to boot from the correct hard drive (sda or hd0, whichever is listed). Continue with boot. Any luck?

Just wondering why you did a complete reinstall instead of following the instructions in post #3 ... What you have now is effectively a new and different issue altogether ...

Did all the things you said, got the same error:
wait-for-root: error loading shared libs: libudev.so.1 : cannot open shared object file: No such file or directory
gave up waiting on root device
Alert! /dev/disk/by-uuid/81ea7805-024d-46c8-9114a67cbef9957f does not exist.
Dropping to shell.
(initramfs)

I did the reinstall while waiting for a reply on the thread, didn't think it would mess things up even more :(
The reinstall was the partial option, not the complete overwrite.

---

### Post by Bucky Ball on 2014-07-07
Now you've come this far, I would just do a full install, not partial or anything else. A partial install on a system that is already broken won't get you far I wouldn't think. And hasn't ... ;)

---

### Post by Zefron on 2014-07-07
> **Bucky Ball said:**
> Now you've come this far, I would just do a full install, not partial or anything else. A partial install on a system that is already broken won't get you far I wouldn't think. And hasn't ... ;)

I want to avoid a full overwrite because I have alot of files that I want to keep. Thankyou so much for your help, I'm going to keep looking for a soloution

---

### Post by Zefron on 2014-07-07
So I entered "exit" into the (initramfs) terminal and it gave me: wait-for-root: error loading shared libs: libudev.so.1 : cannot open shared object file: No such file or directory. Then it proceeded to boot as normal.

Not sure if this is a fix or if this is going to cause more problems down the line, but for now everything seems to be fine.

---

### Post by Bucky Ball on 2014-07-07
Now you're back at a desktop (good news) I would immediately:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade 
```

... and reboot.

---

### Post by Zefron on 2014-07-07
> **Bucky Ball said:**
> Now you're back at a desktop (good news) I would immediately:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade 
```

... and reboot.
sudo apt-get update :
W: Failed to fetch [http://repository.spotify.com/dists/trusty/non-free/binary-amd64/Packages](http://repository.spotify.com/dists/trusty/non-free/binary-amd64/Packages)  404  Not Found [IP: 205.251.203.15 80]


W: Failed to fetch [http://repository.spotify.com/dists/trusty/non-free/binary-i386/Packages](http://repository.spotify.com/dists/trusty/non-free/binary-i386/Packages)  404  Not Found [IP: 205.251.203.15 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.

sudo apt-get upgrade
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/restricted amd64 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/multiverse amd64 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/restricted amd64 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/multiverse amd64 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/restricted i386 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/multiverse i386 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/restricted i386 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/multiverse i386 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-updates/restricted amd64 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-updates/universe amd64 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-updates/multiverse amd64 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-updates/main i386 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-updates/restricted i386 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-updates/universe i386 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-updates/multiverse i386 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-backports/main amd64 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-backports/restricted amd64 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-backports/universe amd64 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-backports/multiverse amd64 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-backports/main i386 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-backports/restricted i386 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-backports/universe i386 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty-backports/multiverse i386 Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

No errors on sudo apt-get dist-upgrade

Upon reboot, same situation at post 9

---

### Post by Bucky Ball on 2014-07-07
Full of errors. Untick the Spotify repository. As I've said, it's currently down/broken whatever.

As for the rest, a mess. You have duplicates in your sources list of everything. Major problem. Do:

```
sudo nano /etc/apt/sources.list
```

... and put a hash in front of each and every duplicate (#). It will then be ignored. This will probably not fix your original problem, but it is a problem and needs to be fixed.

---

### Post by Zefron on 2014-07-07
Got no more errors when updating/upgrading now, cheers.

---

