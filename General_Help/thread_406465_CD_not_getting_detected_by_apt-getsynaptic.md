---
title: "CD not getting detected by apt-get/synaptic"
date: 2007-04-10
forum: General Help
---

### Post by rvbhute on 2007-04-10
I have run into a curious problem here.

1. My DVD-writer is on IDE 1 Master - it is correctly mentioned in /etc/fstab as /dev/hda.

2. Till a few days ago, Synaptic/apt-get were able to use the Feisty Fawn CD for installing software. I say "a few days ago" because most of the times it would grab the packages from the net; so I have no idea when exactly this problem cropped up.

3. Now, the CD is simply not getting detected by said programs.

4. It is getting auto-mounted as **/dev/scd0** - which I think is the root of the problem.

5. If I unmount it and then try to mount it either as /dev/hda or /dev/scd0, both fail.
```

rohit@mark2:~$ sudo mount /dev/hda
mount: special device /dev/hda does not exist
rohit@mark2:~$ sudo mount /dev/scd0
mount: can't find /dev/scd0 in /etc/fstab or /etc/mtab

```

6. However, otherwise, the CDs work fine. I see them on the desktop - can copy data etc.

7. Something is causing the CDs/DVDs to be seen as /dev/scd0 instead of /dev/hda. What should I do?

---

### Post by mac.ryan on 2007-04-11
I am a bit confused, as I believed that /dev is not the mounting directory, but the directories where the devices are recognised, while (under ubuntu, at least) it seemed to me /media is the mounting point for those devices...

Anyhow, if you have to access a given device from a given directory, different than the one where it is presently mounted on, you can do one of the following:

Move the mounting point:
```
sudo mount --move OldDir NewDir
```

Create a symlink (from the directory where you want to create the link):
```
ln -s Target Linkname
```

Hope this helps a bit...

---

### Post by rvbhute on 2007-04-11
The mounting directory is **/media/cdrom0**. The problem is that the device which was getting detected as /dev/hda till a few days ago is now getting detected as /dev/scd0. Since there is no entry for /dev/scd0 in fstab, Synaptic can't access it. On the other hand, Synaptic patiently waits for /dev/hda since that is whats mentioned in fstab. Of course, I can easily add an entry to /etc/fstab to reflect this, but its a good idea to know what caused that change in the first place..

---

### Post by rvbhute on 2007-04-12
Replaced the /dev/hda entry with /dev/scd0 entry in /etc/fstab - problem solved. Still wondering about why the device jumped from /dev/hda to /dev/scd0, though.

---

### Post by mac.ryan on 2007-04-12
> **rvbhute said:**
> Still wondering about why the device jumped from /dev/hda to /dev/scd0, though.

[This article]("http://wiki.archlinux.org/index.php/Persistent_block_device_naming") about persistent naming might be relevant.
See specifically second point of "why...". Symptoms seem similar...

---

### Post by rvbhute on 2007-04-15
That was a nice link. Ties in with the theory that this occured after a run by Update Manager getting the new kernel modules/drivers.

---

### Post by grh2006 on 2007-05-17
I had a similar problem with synaptic. For some reason in my /etc/fstab file, the DVD drive was listed as /dev/hda. This prevented the drive from being mounted, with the error message:

mount: special device /dev/hda does not exist

To fix this, in a terminal window I ran the command:

 ls -al /dev/ | grep dvd

lrwxrwxrwx  1 root root            3 2007-05-17 19:24 dvd -> hde
lrwxrwxrwx  1 root root            3 2007-05-17 19:24 dvdrw -> hde

Then I edited my /etc/fstab file and changed line for the DVD drive to /dev/hde.

---

