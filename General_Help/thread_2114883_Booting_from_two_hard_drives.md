---
title: "Booting from two hard drives"
date: 2013-02-11
forum: General Help
---

### Post by mkbolivian1 on 2013-02-11
Hey guys, forgive me if I'm just being dense, but I want to make sure I really understand this so I don't hack through it and end up with a faulty understanding of what I did to make it work... 

SO I have a desktop computer with two hard drives, one master, one slave. Now, I install ubuntu on the master drive. Installation is clean, quick, easy, and runs great... Right, so now I decide, "hey, I've got another hard drive sitting there unused, and I would love to fiddle with other distros." So I pop in another live usb, run the installer, install to the slave hd, and reboot. Grub loads up, and doesn't seem to see the other distro, so I boot into ubuntu, run update-grub, and it detects the other os. So now I reboot, and select the second os, and I get a list of errors, stuff about disc not found, first initialize kernel, and so on.. Right. I figure, probably just screwed up the installation. So I do a little reading, and somewhere I read that you need to tell the secondary os to install grub on the master drive, because the bios is only mounting the master drive.. It's greek to me at this point, but hey, I give it a shot. This is an old screwed up desktop that no one loves anymore, so I don't mind a little trial and error. Boot the live usb, re-install, re-formatting the slave drive and selecting the master drive as the location of the boot loader. Reboot - now grub is pissed off, can't find anything, and drops into rescue mode. Drat. Clearly that was the wrong thing to do. Ok, so I do a little more reading, and find a post that mentions telling grub to switch which hd is designated master and slave, and there are people talking about chain loading, telling one grub to point to another, there's even a kid who's wired a switch into his box that lets him use a cable-select setup, or switch to activate wired in jumpers which effectively reverse the configuration... All of this is a bit confusing to me, since in my mind they are both hard drives, the computer sees both of them, so why can't I just install an operating system on both of them and have it work... never that easy though. So can someone walk me through this? 

correct me if I'm wrong here: 

step one - install os on master hd

step two - install os on slave hd, also make sure grub is being installed on the slave hd and not over-writing grub on the master hd... 

step three - boot up the os on the master hd, and insert some cryptic snippet of code into the 40_custom file in the /etc/grub.d directory??? 

The desired outcome here is that when I boot up my computer, I can hold shift and see the grub menu... My two distros are listed there. I can click on either one and they will boot up, even though one of them lives on a master hd, and one on a slave hd. Is this too much to ask? I'm sure there's probably something very simple I'm missing here. 

if someone very patient could take the time to use their baby voice with me, hold my little grubby hands and walk me through this scary mess of master-slave-hd0-/dev/sd1-hdb-sda-grub2-kernel-boot mumbo jumbo, i would appreciate it.

---

### Post by SlugSlug on 2013-02-11
try this 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You have it correct Install on master then install on slave should work.

---

### Post by dino99 on 2013-02-11
dont worry, ubuntu is for humans  ):P

it will boot from everywhere, it only need to find it  :p thats the bootloader job

note:
- you have to respect the formatting limits: 3 primary partitions max and set the 4th as extended (to be able to bypass the 4 partitions limit)
- choose a trusted format: ext3 is the better right now, then ext4 for journalling
- install grub (the bootloader) on /dev/sda (or sdb, ...., z)

note2: dont forget that each time you tweak the storage hardware (hdd, ssd, ...), then new uuids are created; so you also need to update the grub menu, to be able to find the new pathes
sudo update-grub

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

---

### Post by mkbolivian1 on 2013-02-11
Right. Seems fairly straightforward. I'll give it a go and get back to you.

---

### Post by mkbolivian1 on 2013-02-12
Ok, let me preface this by saying, I had not opened this machine before I started this process, I had just plugged it in and started working on it, because I had used it before at the owner's house, and "knew" what was going on inside it... So, before I started trying to fix this boot issue, I decided to open 'er up and see if there were any issues inside. First thing I noticed was, the disc drive wasn't working. I figured that, since they had an external disc drive attached to the box... I also noticed that the second hd was attached to the slave connection on the secondary controller, on a low speed 40wire ribbon. So i yanked the optical drive out, I have a replacement I might pop in there if I feel like it. I also replaced the single connection primary 80wire ribbon with one made to accept two hard drives. I went ahead and set the jumpers on the hard drives, master on the larger 40gb drive, and slave for the 20gb one. Then I booted into bodhi live and installed boot-repair. Ran the recommended repair, and everything seemed to be peachy. The os on the Master drive booted up like a champ, ran beautifully, and all was well. Now I rebooted, and selected my second os (bodhi) from grub. Wouldn't ya know it, bodhi booted right up on the slave drive, and as far as I can tell, there's no longer a problem... SOLVED. Thanks for the prompt response, and the useful information. :D

---

