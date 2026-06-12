---
title: "lost all write access; lost sudo. &quot;unable to resolve host&quot; error"
date: 2022-03-17
forum: General Help
---

### Post by anandamide on 2022-03-17
So, real humdinger here, hopefully someone will have some pointers.

I have a Pi4 running Ubuntu LTS

Currently, I'm unable to do anything substantive on the system as I've lost write access

From my home directory:

```
touch: cannot touch 'something': Read-only file system
```

Any sudo returns:

```
sudo: unable to resolve host HOSTNAME: Temporary failure in name resolution
```

A line seems to be missing from /etc/hosts

```
127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

However I cannot add the missing line because of aforementioned errors with write access / attempting to sudo

It seems like I'm caught in an impossible bind. Any help much appreciated

n.b. prior to this I'd edited my postfix config file and fstab. fstab looks fine to me but I suspect postfix might have deleted the /hosts line (I'm new to postfix). System was clearly upset after reboot as no welcome message or kernel information was displayed after reboot and login

I usually just SSH into this machine but on the off-chance it was something to do with the SSH connection I plugged some peripherals into the Pi, but still no luck

---

### Post by TheFu on 2022-03-17
Ubuntu LTS isn't clear enough.  There are lots of those.  Exactly which release and which DE?  The Gnome DE really shouldn't be used on any Raspberry Pi computers. It is too heavy.

If name resolution doesn't work, sudo might not work either. sudo settings are dependent on the hostname.

A read-only file system is common whenever the storage device is starting to fail.  Backup all data that you can immediately. I'd also run an fsck on each file system. An unclosed file system will not be mounted read-write. It is a protective measure.

---

### Post by MAFoElffen on 2022-03-17
So on RaspPi: Which model? Are you booting default from MicroSD card or did you mod to boot from USB drive? 

Is your Storage where /boot 'resides' full or does it have more than 20% free?
```

 df -hT -x tmpfs -x devtmpfs | grep -v '/snap/'

```
Do you have another computer, where you can read an SD card... In other words, be able to interact with the storage device with it off-line? For my Raspberry PI, I have many MicroSD Cards setup fpr it, where I can still boot it and do things to another MicroSD card with a card reader...

---

### Post by pissedoffdude on 2022-03-18
Hey thre,

Sounds like your file system may be corrupted.  Assuming you're using an ext* filesystem we can force an fsck to run on reboot by:

1. Restarting the machine
2. Getting to the grub menu (hold shift if it's a bios setup, otherwise try esc)
3. Locate the kernel you want to boot, and hit 'e' so you can edit the grub entry
4. In the kernel section, after the words 'quiet splash' append fsck.mode=force fsck.repair=yes so that it looks like 'quiet splash fsck.mode=force fsck.repair=yes'
5. Hit ctrl+x to boot
6. It should ideally run an fsck and repair your filesystem that will then result in it getting properly mounted with write permissioms

Best,
Gabe

---

### Post by ActionParsnip on 2022-03-18
What is the output of:
```

cat /etc/hostname

```

You need an entry for that name in /etc/hosts to get rid of the "unable to resolve host" errors

---

### Post by anandamide on 2022-03-19
Thanks so much for all your replies folks, it's been super helpful.

I've sorted both problems and I'm genuinely embarrassed by what the underlying issue was for one of them!

@MAFoElffen - thanks for the tip; it allowed me to get into the /hosts file and add the missing line. Sudo sorted.

That still didn't fix the write access problem; as many suggested I ran fsck but while it noted a few problems - presumably from failing to unmount the drive (hard to sudo poweroff when I can't sudo), fixing them didn't resolve any issue. Plenty of space left on the SD.

After much back and forth I finally took another look as fstab...

Somehow - *somehow* - I'd commented out the first damn line, which pertains to the root filesystem. Absolute scenes. After loading up the SD card into another machine and editing the file from there, everything is back to normal.

Marking this as solved. And me as properly red faced.

Thanks for all the help :-)

---

