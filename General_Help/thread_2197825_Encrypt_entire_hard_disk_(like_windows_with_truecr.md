---
title: "Encrypt entire hard disk (like windows with truecrypt)"
date: 2014-01-05
forum: General Help
---

### Post by stefbeukers on 2014-01-05
Hi there,

I'm looking for a way to encrypt my entire hard disk (laptop). I know it's not 'entirely' possible because of the root-stuff. I've encrypted my ubuntu on the installation, so is it possible to encrypt it again? Like I have my windows (on my desktop) encrypted with a password before boot, by using Truecrypt. 

So is there a way to encrypt my hard disk with a password before 'boot'? I'm using Ubuntu 12.04 LTS.

Thnx already!

---

### Post by jamesisin on 2014-01-05
If you installed your OS using encryption, that would be it.  This would encrypt all partitions for that instance of Ubuntu.  Is that not what you are after?

---

### Post by stefbeukers on 2014-01-07
I installed ubuntu with the encryption option on the installation. So only my 'home' is encrypted, right? Is that just as strong as a full disk encryption?

---

### Post by Impavidus on 2014-01-07
During installation, you can choose to encrypt nothing (or just isolated directories, which can be set up later), the home directory or everything except /boot. Obviously, the more you encrypt the securer the system is and the more important your backups are, because you have no chance of restoring anything if something goes wrong. Not sure whether you can encrypt your system after installation. For full disk encryption I don't think so.

Run for example **mount** or **df -T** to view your partition types and mountpoints. It should tell you which ones are encrypted.

---

### Post by stefbeukers on 2014-01-07
Is there a way to check what I've encrypted? You say "mount" & "df-T", but how do I run them?

---

### Post by Impavidus on 2014-01-07
In a terminal. You can also try the disk utility or system monitor, they must be hidden somewhere in your system. The difficulty with those shiny graphical tools is that you have to find them in a different place on every different version and flavour of Ubuntu. All of them basically give the same information: file system types and mount points.

---

### Post by jamesisin on 2014-01-07
In a terminal use this command:

```
df -T
```

It will return a list of partitions and include information about which is what.

Yes, as reported above, there are two options for encrypting which you might choose at installation.  If you choose to install your Home directory, you will unencrypt it when you make a login attempt (per user).  If you choose to encrypt your installation, then you will be prompted to unencrypt it when you first boot the machine (before the login screen).

---

### Post by stefbeukers on 2014-01-08
I ran ```
df -T
``` and this is my output:

```
Filesystem     Type     1K-blocks     Used Available Use% Mounted on
/dev/sda1      ext4     151650468 22197056 121743308  16% /
udev           devtmpfs    956168        4    956164   1% /dev
tmpfs          tmpfs       387012      860    386152   1% /run
none           tmpfs         5120        0      5120   0% /run/lock
none           tmpfs       967524       84    967440   1% /run/shm
```

Anyone who can tell me which parts are encrypted, by seeing this?

I think I encrypted my home directory on install. Is there any way to do an encryption on the boot, like before the login screen?

---

### Post by jamesisin on 2014-01-09
I see no evidence of encryption there.  If your Home directory were encrypted, you'd see an ecryptfs entry (at /home/username/.Private).  If your installation of Ubuntu were encrypted you'd see an entry called /dev/mapper/this--vg-root.

---

### Post by stefbeukers on 2014-01-09
Is there any way to do this now? To encrypt my installation?

---

### Post by Dave_L on 2014-01-09
See this: [http://ubuntuforums.org/showthread.php?t=2198118](http://ubuntuforums.org/showthread.php?t=2198118)

---

### Post by stefbeukers on 2014-01-09
Yeah, i've seen that one. But I'm using 12.04 because of the hardware I have. And I believe there is no such thing for entire encryption on the installation of 12.04...

---

### Post by mastablasta on 2014-01-09
truecrypt works on ubuntu as well if you are more comfortable with it. : [https://help.ubuntu.com/community/TrueCrypt](https://help.ubuntu.com/community/TrueCrypt)

---

### Post by Dave_L on 2014-01-09
> Yeah, i've seen that one. But I'm using 12.04 because of the hardware I have. And I believe there is no such thing for entire encryption on the installation of 12.04... 

If I recall correctly, the alternate install .iso for Ubuntu 12.04 gives you an option for full-disk encrypted LVM.
[http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads) 
Ubuntu 12.04.3 alternate (64-bit)
Ubuntu 12.04.3 alternate (32-bit)

Or you can set it up manually, but it's much more complicated.

---

### Post by Dave_L on 2014-01-09
> **mastablasta said:**
> truecrypt works on ubuntu as well if you are more comfortable with it. : [https://help.ubuntu.com/community/TrueCrypt](https://help.ubuntu.com/community/TrueCrypt)

With Truecrypt you can create an encrypted container and put files in it. I use Truecrypt for that myself.

But can you encrypt the entire disk, and do it in a way that's integrated into the boot process? I didn't think Truecrypt supports that for Linux.

---

### Post by stefbeukers on 2014-01-16
I've been trying to get my home directory encrypted and I ran ```
df -T
``` again. This time the output is: 
```
Filesystem          Type     1K-blocks     Used Available Use% Mounted on
/dev/sda1           ext4     151650468 46654740  97285624  33% /
udev                devtmpfs    956160        4    956156   1% /dev
tmpfs               tmpfs       387012      860    386152   1% /run
none                tmpfs         5120        0      5120   0% /run/lock
none                tmpfs       967524      120    967404   1% /run/shm
/home/stef/.Private ecryptfs 151650468 46654740  97285624  33% /home/stef/Private

```

So I think it worked. Is my entire home directory encrypted right now? Or just my /home/stef/private folder?

---

### Post by Dave_L on 2014-01-16
There are a couple of ways to verify that it's encrypted.

1. Create another user account, e.g. "stef2". Reboot and log in as the new user. Try to access the old user's files (/home/stef).

2. Reboot into recovery mode and select the option to drop to a root shell. Or boot from a LiveCD/USB. Try to access the old user's files (/home/stef).

---

