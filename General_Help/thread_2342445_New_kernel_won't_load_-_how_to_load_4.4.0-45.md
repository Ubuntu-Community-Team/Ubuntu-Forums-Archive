---
title: "New kernel won't load - how to load 4.4.0-45?"
date: 2016-11-06
forum: General Help
---

### Post by twittles on 2016-11-06
Hello all. I'm new to Ubuntu (from Mint) and I'm having a hard time of loading kernel 4.4.0-45. It's listed as installed, however, every time I restart it simply loads into 4.4.0-31 (default kernel). I tried updating the GRUB (in which it reports  finding the proper kernel), but no matter what I select - Ubuntu still indicates 4.4.0-31 when I boot up. (via uname-a and system monitor tab)

I am mainly switching kernels for security (dirty cow) and I'm still a little confused if this 4.4.0-31 is still vulnerable...**Was it patched or was 'the patch' an updated kernel? **

I've followed all the google hits and I'm still coming up empty. I've run the updater and 'sudo apt dist-upgrade' and so forth. So how can I make 4.4.0-45 load instead of 4.4.0-31 or am I actually now ok with 4.4.0-31??  I think I'm probably missing something here as oa noob. Thanks!

---

### Post by monkeybrain20122 on 2016-11-06
How did you install 4.4.0-45? On my 16.04 it has been updated to 4.4.0-45 without me doing anything. To see if you installation actually works, reboot and tab the shift key to show the boot menu then from the advanced option or something like that you should be able to choose 4.4.0-45 if it is installed properly. If everything works you can just delete 4.4.0-31 then it will boot to 4.4.0-45. I don't know why you are not booting into it, probably it wasn't installed properly.

---

### Post by twittles on 2016-11-06
>[COLOR=#000000]How did you install 4.4.0-45?
[/COLOR]Synaptic package manager. I chose the packages that looked the same as the ones installed for 4.4.0-31. There are four installed. Two headers things, the image itself and 'extra'. 

What is the correct way to install it? Not to be that guy but on Linux Mint this is so much easier. I just installed Ubuntu today for the first time. I did all the updates as far as I know.

>[COLOR=#000000]reboot and tab the shift key to show the boot menu then from the advanced option or something like that you should be able to choose 4.4.0-45 if it is installed properly.

Like I said, I only see the old one listed in GRUB.

>[/COLOR][COLOR=#000000]I don't know why you are not booting into it, probably it wasn't installed properly.

[/COLOR][COLOR=#000000]Fair enough, how do I install it properly? Could this have anything to do with my 'encrypted Home'?


Forgot to mention I am on [B]16.04.1 MATE

[/B]Here is the output of sudo update-grub

[/COLOR]Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Linux Mint 17.3 Rosa (17.3) on /dev/sdb1


[COLOR=#000000]



[/COLOR]

---

### Post by Bashing-om on 2016-11-07
twittles; Hello;

A thought :
as you have:
> 
Found Linux Mint 17.3 Rosa (17.3) on /dev/sdb1

then where is ubuntu installed to ? AND what is the boot control authority ? ubuntu or Mint ?
What hard drive are your booting up from ?

Show the outputs of terminal commands:
```

sudo parted -l
sudo blkid
sudo grub-probe -t fs_uuid /boot/grub
sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


Now with these we can ask some intelligent questions.

[INDENT][INDENT]there is that path that seems right
[INDENT][INDENT]but leads to a broken system
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by twittles on 2016-11-07
I was able to somehow finally get 4.4.0-45 listed in GRUB but it now hangs right before it loads the encrypted part. I am having the exact same issue as [this guy]("http://askubuntu.com/questions/786267/wont-boot-drop-to-busybox-after-kernel-upgrade-with-encrypted-disks") who has the same problem on two separate machines. It looks like there is an issue with encryption and 4.4.0-45. It seems that the uuid for the encrypted portion is getting messed up somehow.

So now I can boot 4.4.0-31 perfectly as before and I can see the new kernels listed. I can actually boot into 4.4.0-45 but -only- if I go through the recovery consol. Booting normally will cause it will hang like the guy's system in the aforementioned link. It looked like he got his fixed but I couldn't quite follow what he did plus the old kernel is working for me so that makes his solution look murky for me.

Anyway, my guess is that I would have this issue in Linux Mint as well if I were using encryption (I use the 4.4.0-45 on LM currently no encryption)

So I'm thinking maybe my diagnostic output may be a moot point now but I'll post it if you think it will help given the fact it's not just me with this problem I think. 

FWIW, my Linux partitions are on one drive and my windows is on the other. I have never heard of boot authority before.  Thanks.

---

### Post by Bashing-om on 2016-11-07
twittles; Well ..

Upfront, I have no experience with encryption .  If this should turn out to be a de-cryption issue others will have to advise.

swap partition identification: Many things can effect this ID and what the system assigns.
verify that the UUID to boot is correct:
```

cat /etc/fstab

```
And compare the listed UUIDs to the results shown from:
```

sudo blkid
swapon --summary

```

Control authority : Depends on the system architecture; EFI or MBR .
In the legacy (MBR) scheme there can be but one boot code installed to the hard drive's boot sector - that code relates to either the LM OR the 'buntu operating system, but not both . Now, which is the primary operating system installed to the hard drive ? This primary will control the ability to boot the secondary . The last installed or UPdated system becomes that control authority with out that you take  preventive measures to insure that the primary always has that control authority .

EFI: Is a horse of another color, in that all boot codes are installed to  /boot ; and it is efibootmgr that controls the boot process.

So, now we need to know what we are working with.
Show us:
```

sudo parted -l

```

[INDENT][INDENT]we see which way to go
[/INDENT][/INDENT]

---

