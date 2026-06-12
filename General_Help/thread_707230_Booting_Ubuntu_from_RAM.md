---
title: "Booting Ubuntu from RAM"
date: 2008-02-25
forum: General Help
---

### Post by capink on 2008-02-25
First of all, credit goes to the original author (of the [wiki on how to boot Ubuntu to RAM]("https://wiki.ubuntu.com/BootToRAM"))  Tszanon. I wanted the submit the changes I made to author of the wiki but I didn't find any contact information. So I am going to post it here. I will be quoting some parts from the original wiki itself.


[SIZE="4"]**Boot Ubuntu from RAM[/SIZE]**

This is a guide on how to copy your Ubuntu system to RAM and boot it from there. Booting from RAM is only possible on today's machines because linux does not take as much hard disk space as other operating systems. While it is true that hard disks have grown in size to the point that they can easily hold 10+ G OSs, having an operating system that is economical in it's use of harddisk space has many advantages, and the ability to boot linux from RAM highlights this.


The main idea and the general principles are similar to the original [wiki on how to boot Ubuntu to RAM]("https://wiki.ubuntu.com/BootToRAM").  But this guide has some differences to the original wiki:
[LIST=1]
[*]Rather than using a live CD, we will use the system installed on your harddisk as the basis of the image we will create.
[*]This guide uses live-initramfs instead of casper. This is because live-initramfs is present in both Ubuntu and Debian so that guide can serve wider audience. For those who want to use casper instead it should work the same but I have not tested it, you will just need to replace live-initramfs with casper and /live with /casper.
[*]No editing of the boot scripts as live-initramfs introduced an option to boot from ram automatically.
[*]Unlike the method of the original wiki, using this method all your partitions are going to be mounted automatically exactly as they are mounted when you boot your normal system, with the exception of the root partition.
[/LIST]


Note: Since the system is going to be copied to RAM, the boot process takes slightly longer time.



N.B This guide works only for Ubuntu gutsy and Debian lenny or later.


> 
**Quote from the original [wiki on how to boot Ubuntu to RAM]("https://wiki.ubuntu.com/BootToRAM")**
[COLOR="Red"]Edits and additions done by me are highlighted in Red.[/COLOR]

WARNING: The author asserts that this procedure works for him, but cannot guarantee that this procedure works for anyone else. Although this procedure is meant to be 100% safe, it is feasible that there may be mistakes, or a chance of misunderstanding the instructions in a manner that causes loss of data. Please make a backup and do not attempt on mission critical systems. Read through this article thoroughly, and do not attempt if you do not comprehend or feel comfortable about any of the instructions! 

CAUTION: I hope this is intuitively obvious, but I'll humor you and state it bluntly: Changes you make under the live session are NOT saved and WILL BE LOST when you reboot or shut down. Don't save anything important to the "home directory" and expect it to still be around! If you want to save data permanently, mount a permanent medium (such as your hard drive), plug in a thumbdrive, or use some network functionality built into Ubuntu to save your data to a non-volatile destination. [COLOR="Red"] EDIT: Using the method outlined in this guide, all the partitions in your fstab - except the root partition -, will be mounted automatically at boot time read/write exactly as in your normal system. You have no need to mount anything manually. But this warning still applies, anything written to the ROOT PARTITION will be lost. But files written to other partitions (which have entries in fstab) will be permanent.[/COLOR]


[SIZE="4"]**Use Cases[/SIZE]**

There are many cases where one would like to boot Ubuntu to RAM: 

Performance: The desktop performance is dramatically improved. A 400MB squashed filesystem in RAM, that holds 1200MB of data, is read back on a 1.6GHz Core Duo in about 3 seconds, including decompression time. 

Power, Noise, Durability: Although modern hard disks don't use much power compared to other system components, this may still be important for some. In laptops, hard disks are often the noisiest components, so this setup can reduce system noise. With the hard disk spun down, a laptop can potentially withstand greater shocks without damage. 

Abrupt poweroff: Since the hard disk is only momentarily used in read-only mode during boot, then never touched again, there are few or no negative consequences of an abrupt poweroff. If a system is used where power is inconsistent, or the system is regularly used in a context where fast shutoffs are required, this is very handy. 

Privacy: Anything you do in this session are lost when you reboot or power off. This is great for kiosks or other systems where permanent modification are not desired. (Note that by default the livecd user has full sudo access, so potentially a malicious user can still make permanent changes by mounting the hard drive and following this HOWTO)



Note: As noted above any files saved to the root partition will be lost upon shutdown. This also includes options and configurations. Whenever you change some program setting, the change will will not be permanent.


[SIZE="4"]**Requirements[/SIZE]**

Enough RAM. How much depends on the size of the squashfs image we are going to create from the installed system. A system that is 1.5 G in size will create roughly a 500 M squashfs. Since this 500 M is going to be copied to RAM, your RAM must be larger than 500 M, at least by an additional 256 M of RAM (Amount of RAM required = squashfs size + at least 256 M). But to work comfortably in the previous scenario it is recommended to have 1 G or more of RAM.

If you have a swap partition (which you should since you already have a copy of Ubuntu installed), The system will fall back to it when the RAM gets full. But this will severely limit the speed of the system which defeats the purpose of this guide.


You also need enough harddisk space. At least double the amount taken up by your system.




Note: A command to know how much space is taken up by your system:

```
sudo du -hcs --one-file-system / --exclude=/dev/* --exclude=/tmp/* --exclude=/sys/* --exclude=/proc/* --exclude=/home/*
```








[SIZE="4"]**The process:[/SIZE]**


1. Install some essential packages:

live-initramfs is present in the universe section of the repository. You must first enable universe repository before attempting to install the package. Here is guides to enable universe ([Ubuntu GUI]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096") [,Kubuntu GUI]("http://linux.about.com/od/kubuntu_doc/a/kubudg22t04.htm") [,CLI]("https://help.ubuntu.com/community/Repositories/CommandLine#head-e1a24b1b2037f68b5a95f54388582b58ea4c9bd0")).


```
sudo apt-get update
```
```
sudo apt-get install live-initramfs squashfs-tools linux-ubuntu-modules-$(uname -r)
```




Note: People using Debian replace [COLOR="Magenta"]linux-ubuntu-modules-$(uname -r)[/COLOR] with [COLOR="Magenta"]squashfs-modules-$(uname -r) unionfs-modules-$(uname -r)[/COLOR]



2. Update the kernel modules dependencies:

```
sudo depmod -a
```


3. Update the initramfs

```
sudo update-initramfs -u
```


4. copy your filesystem to temporary directory

```
DEST=/var/squashfs
```

```
sudo mkdir -p ${DEST}
```

```
sudo rsync -av --delete / ${DEST} --one-file-system \
--exclude=/proc/* --exclude=/tmp/* --exclude=/dev/* \
--exclude=/sys/* --exclude=/boot/* \
--exclude=/home/* --exclude=/etc/mtab \
--exclude=/live --exclude=${DEST}
```



Note: You can replace /var/squashfs with any path you wish. Just make sure that it have enough space.



5. Copy you home directory

```
sudo find $HOME  \! -type d -iwholename "${HOME}/.*" \
| grep -vi -e 'cache' -e 'thumbnail' -e 'log' -e 'trash' \
-e 'history' -e 'snapshot' -e 'tmp' -e 'temp' \
| while read file; do sudo cp -vdp --parents "$file" ${DEST}; done
```

This command only copies the settings in your home directory. It does not copy any personal files (unless these files starts with a dot and and resideds in the top level of your home directory). It also omits some unnecessary data such as your browser cache.




6. Modify fstab of the copied filesystem

```
sudo gedit ${DEST}/etc/fstab
```

delete the entry of the root directory. It should look like this:

```
UUID=.....      /         ext3    defaults,.... 0       1
```

After deleting this entry save the file.



People with separate home partition delete the entry of the home partition. It should look something like this:

```
UUID=.....      /home         ext3    defaults,.... 0       1
```



7. Clean some unnecessary files


Delete some files under ${DEST}/var

```
[ -n "$DEST" ] && sudo find ${DEST}/var/run ${DEST}/var/mail ${DEST}/var/spool ${DEST}/var/lock ${DEST}/var/backups ${DEST}/var/tmp -type f -exec rm {} \;
```



Delete only OLD log files:

```
[ -n "$DEST" ] && sudo find ${DEST}/var/log -type f -iregex '.*\.[0-9].*' -exec rm -v {} \;
```
```
[ -n "$DEST" ] && sudo find ${DEST}/var/log -type f -iname '*.gz' -exec rm -v {} \;
```


Clean current log files:

```
[ -n "$DEST" ] && sudo find ${DEST}/var/log -type f | while read file; do echo | sudo tee $file; done
```


Clean Pakcage cache:

```
[ -n "$DEST" ] && sudo rm -v ${DEST}/var/cache/apt/archives/*.deb
```




8. Create the squashfs image

The squashfs image must reside in /live

```
sudo mkdir /live
```

```
sudo mksquashfs ${DEST} /live/filesystem.squashfs -noappend -always-use-fragments
```

Examine the size of the image and make sure it is less than the size of your RAM.

```
sudo du -h /live/filesystem.squashfs
```





9. Add a new entry to /boot/grub/menu.lst of your main system

```
sudo gedit /boot/grub/menu.lst
```

Copy the entry of your main system and modify it to look exactly like this:


```

title		RAM Session
root		[COLOR="Blue"](hd0,2)[/COLOR]
kernel		[COLOR="Blue"]/boot/vmlinuz-$(uname -r)[/COLOR] [COLOR="Red"]**BOOT=LIVE boot=live toram username=[COLOR="Magenta"]user[/COLOR] nosudo noxautoconfig noautologin quickreboot**[/COLOR] ro quiet splash
initrd		[COLOR="Blue"]/boot/initrd.img-$(uname -r)[/COLOR]

```

The text highlighted in [COLOR="Blue"]blue[/COLOR] should match the corresponding parts of your main system entry.
Replace [COLOR="Magenta"]user[/COLOR] with your account username.
The parts highlighted in [COLOR="Red"]Red[/COLOR] are essential.




10. [COLOR="Gray"](Optional) Delete the temporary filesystem from which we created the squashfs.

Do not do this step if you intend to customize the squashfs in the future (which is highly possible).

```
[ -n "$DEST" ] && sudo rm -r ${DEST}/*
```[/COLOR]


11. Reboot and choose the RAM Session from your boot menu.




**[Shameless plug]**: If the resulting squashfs size is bigger than what your RAM can handle and you want to reduce it further. You can try removing unneeded pacakges from your main system by following this [guide]("http://ubuntuforums.org/showpost.php?p=2651015&postcount=1").





==================================================================================

[SIZE="4"]**Special Note for people with a separate home partition:[/SIZE]**

If you have a separate partition for /home you CAN CHOOSE NOT to include your home directory in the squashfs image. Instead your home partition we will be mounted automatically at boot.

***So does this has any advantages/disadvantages?***

DISADVANTAGES: Some programs need to access config files on you home directory when they start. So _**theoretically_** (I have not done any tests or benchmarks so I am not sure), this could create a bottleneck since the rest of program parts are accessed from RAM at much higher speed.

ADVANTAGES: On the other hand, whatever files you write to your home directory will not be lost on reboot or shutdown. For me this is not a big advantage as I don't save any personal data to my home directory anyway. But it can be handy whenever you change some program settings, as that change will be permanently saved to the home directory, rather than saved temporarily to RAM.

***What to do to exclude the home partition from the squashfs image?***

Omit step 5 (which involve copying the home directory). Also in step 6 DO NOT delete the entry of the home partition so that it gets automatically mounted at boot.

===================================================================================





[SIZE="4"]**References:[/SIZE]**

[Wiki on how to boot Ubuntu to RAM]("https://wiki.ubuntu.com/BootToRAM")
[Man page of LIVE-INITRAMFS]("http://live.debian.net/other/manpages/live-initramfs.7.html")

---

### Post by Tu13erhead on 2008-02-29
Hmm, this is an interesting concept.  I've got 2gb of RAM on this bad boy but Gutsy rarely uses more than like half of it.  Maybe I should give this a shot.

I've got a 2gb SD card in an internal card reader on this thing.  Could it be useful with this sort of setup?

---

### Post by markp1989 on 2008-05-06
good guide, will be doing this on my eee as soon as my 2gb ram gets here

---

### Post by markp1989 on 2008-05-06
jus tried this on my desktop, went fine till step 10, i did it in a new terminial by mistake, and i eneded up breaking my system

---

### Post by capink on 2008-05-06
I am very sorry to hear that. I have added a check to step 10 to guard against similar mistakes.

---

### Post by markp1989 on 2008-05-06
> **capink said:**
> I am very sorry to hear that. I have added a check to step 10 to guard against similar mistakes.

dont worry about it, i didnt lost any data, i relizd what i had done and turned my computer off 

good to know you edited it so other people dont have the same problem

thankyou

---

### Post by markp1989 on 2008-05-06
i have done it on my desktop, 2gb of ram ,and a 799M squashfs, but during boot i get an error about being out of memory:S

---

### Post by markp1989 on 2008-05-09
just finished doing this on my eee, got the 2gb ram today, works prefectly, and gives me peace of mind, because now it is not writing any thing to the ssd, extending the life of it

---

### Post by Sam Lars on 2008-06-05
markp1989, was adding more RAM what fixed your issue?

I've got 3 GB of RAM and a 980MB squashfs.
When I booted, it sat reading from the hard drive for a long time and eventually came up with a kernel panic, out of memory.

---

### Post by Sam Lars on 2008-06-06
Ok, I finally got my image down to 633MB, and it booted.  It doesn't seem right, though.
My swap space, 1GB, is totally full, but I'm using the usual of my 3GB of RAM... shouldn't there be more like 2GB of RAM available and plenty of swap?

---

### Post by foureight84 on 2008-06-23
very cool i'm gonna give it a try tomorrow

---

### Post by foureight84 on 2008-06-23
EDIT: This was a stupid and obvious question.

---

### Post by markp1989 on 2008-07-02
how hard would it be to do this,  in combination with unionfs,  so that changes will still be kept?

---

### Post by mastrboy on 2008-07-23
thanks, really helped me bulding a debian image i can boot over pxe :)

---

