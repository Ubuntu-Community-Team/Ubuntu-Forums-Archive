---
title: "/boot filled up, unable to update!"
date: 2015-06-16
forum: General Help
---

### Post by jamal5 on 2015-06-16
Hi all,

So recently I got an update notification, clicked Install Now, but it gave me the message

> Not Enough Free Disk Space
The upgrade needs a total of 84,0 M free space on disk '/boot'. Please free at least an additional 66,1 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

My boot partition is 246,8MB in size, of which 216,1mb is used up. I took a look at what's in there, and it seems like I have five initrd.img's of different versions, each 29,7MB in size. Here's a screenshot of the situation:

[ATTACH=CONFIG]262622[/ATTACH]

I'm guessing that these are redundant. Possibly there was an update that failed to remove the old .img after installing the new one. Am I safe if I delete the four earliest versions, and the corresponding config-, abi-, and system.map- files? Or is there something else I can do?

Resizing the /boot partition is out of the question since the disk is encrypted.

Thanks!

---

### Post by howefield on 2015-06-16
Try

```
sudo apt-get autoremove
```

or first

```
sudo apt-get -s autoremove
```

to get an idea of what will be removed.

---

### Post by jamal5 on 2015-06-16
> **howefield said:**
> Try

```
sudo apt-get autoremove
```

or first

```
sudo apt-get -s autoremove
```

to get an idea of what will be removed.

I ran sudo apt-get autoremove, and saw that it did indeed find and remove a redundant initrd.img (forgot to copy the output...), rebooted, and now I see that /boot is 175,0MB used. Trying to run the update tells me

> 
The upgrade needs a total of 84,0 M free space on disk '/boot'. Please free at least an additional 25,0 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

Looking at /boot in Nautilus, four out of five of the initrd.img's are still there (only one gone is 3.16.0-30-), here's what it looks like:

[ATTACH=CONFIG]262623[/ATTACH]

What shall I do now? .....  And thanks for that tip.

---

### Post by Bucky Ball on 2015-06-16
To remove unwanted kernels I've always done this:

Run 'uname -r' in a terminal and make a note of which kernel you are currently booted into;
Open Synaptic Package Manager and search for 'linux image';
Mark to completely remove all kernels except the one you are using and the one before it (I like to have a fallback in case the current kernel breaks);
Hit 'Apply'.

That might do it.

---

### Post by jamal5 on 2015-06-16
Bingo! Update worked and I saw that it added the newest kernel, 3.16.0-41, so now I have three.

Why doesn't Ubuntu handle this automatically? Just wondering since this is an annoying issue that could be very easily prevented by the developers.

---

### Post by mcduck on 2015-06-16
Since there's always a small risk of new kernel causing compatibility issues with some specific hardware etc, kernel updates will not replace old versions but instead install the new one alongside the old version. This way, should something go wrong, you'll always be able to just select the old kernel from your boot menu and stll have a functional machine.

Running "apt-get autoremove" will delete the old kernels automatically, but it will keep a few latest ones around so if you have a really small separate /boot partition you might have to do some manual work. For most users having a few old kernels around shouldn't cause any issues and the *autoremove* is enough.

..of course it would be nice if the user didn't even have to run "apt-get autoremove" in the first place, but that could cause problems in situations where someone intentionally has different kernels around.

---

### Post by QIII on 2015-06-16
Fedora uses a similar method, although there is a command to remove old kernels specifically rather than Ubuntu's more general autoremove.

Old kernels are kept in Fedora for the exact same reasons: a new kernel may present problems and the developers don't presume to know what you want to do with your system.

So it's not just Ubuntu.

---

### Post by dino99 on 2015-06-16
As a few users hit that issue, i've reported a feature request for cleaning that /boot problem; comment if you feel concerned  :p
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1465658](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1465658)

---

### Post by jamal5 on 2015-06-16
> **dino99 said:**
> As a few users hit that issue, i've reported a feature request for cleaning that /boot problem; comment if you feel concerned  :p
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1465658](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1465658)

Thank you, I don't think the autoremove cronjob idea is the best though, since it only removed the oldest kernel for me, which didn't free up enough space. Limiting kernels to two or three before removing old ones seems good to me :) but others know better.

---

### Post by Bucky Ball on 2015-06-16
Yep, current one and the one before it, 3.13.0-54 and 3.13.0-53 for instance, on 14.04 LTS. I kill the rest with Synaptic if autoremove doesn't get them first.

---

### Post by monkeybrain20122 on 2015-06-16
> **QIII said:**
> Fedora uses a similar method, although there is a command to remove old kernels specifically rather than Ubuntu's more general autoremove.

Old kernels are kept in Fedora for the exact same reasons: a new kernel may present problems and the developers don't presume to know what you want to do with your system.

So it's not just Ubuntu.

Fedora only keeps the two latest kernels (you can change the number by editing some config file) rather than letting them accumulate indefinitely like in Ubuntu. In Fedora you don't need to run any autoremove command. When you get a new kernel in update the oldest will be automatically removed if there will be more than two after upgrade.

---

### Post by monkeybrain20122 on 2015-06-16
Unless you use nonstandard file systems or encryption there is no need for the /boot partition. This problem occurs because the /boot partition is tiny.

---

### Post by QIII on 2015-06-16
Fedora still uses package-cleanup --oldkernels to get rid of stuff like kernel-devel and such.  You can add the --keepdevel flag if you want to keep them.

---

