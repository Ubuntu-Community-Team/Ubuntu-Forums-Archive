---
title: "resizing /home (/media/host/wubi/disks/home.virtual.disk)"
date: 2007-07-20
forum: General Help
---

### Post by ChaoticMind on 2007-07-20
I'm trying to increase the size of my /home partition, and according to [this]("https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b"), I can use [Toporesize]("http://csemler.com/cs.html") to do so. I tried doing that, however there is little documentation apart from the readme file which states: > In order to increase the size of base.img you must first increase the size of the file itself. That is where this program comes in. Select the file and adjust the slider to the size in MB that you want the file to be then click "resize file" If you are enlarging the file extra blank space will be appended to the end of the file. 

At first i did so using cmd, since i wasn't sure how to run the gui version, which apparently is ran through the ,bat file. Anyway, I did increase the size from ~450mb? or so, to a more comfortable 2 gbs.
However, after booting back into ubuntu, I found that while the home.virtual.disk file shows as 2gbs of size, my home directory is still at a measly 461.75mb. 

My next course of action was to scroll down to the [next section]("https://wiki.ubuntu.com/WubiGuide#head-58fe61976825a2b764bfd5c4cbca243cb9db12a4"), and try the suggested approach there. However this resulted in another failure which is: 
> kevin@ubuntu:~$ sudo mkfs.ext3 /dev/loop4 
Password:
mke2fs 1.40-WIP (14-Nov-2006)
mkfs.ext3: Device size reported to be zero.  Invalid partition specified, or
        partition table wasn't reread after running fdisk, due to
        a modified partition being busy and in use.  You may need to reboot
        to re-read your partition table.


I, of course, have no idea what that means. (tried rebooting to no avail)

On a sidenote, Wubi is great and has my thanks for introducing me to the world of ubuntu and linux, and hopefully windows won't be around for much longer ;p

---

### Post by tuxcantfly on 2007-07-20
You'll need to create the file extra.virtual.disk first.

Say, if you want it to be 10 GB:

```
cd /media/host/wubi/disks
dd if=/dev/zero of=extra.virtual.disk bs=1000 count=0 seek=$[1000*1000*10] 
```

Then reboot. Read the Wubi Guide for more details, I've updated it.

---

### Post by ChaoticMind on 2007-07-20
Oh yeah, I forgot to mention, that I already did that, although the command i used was slightly different, but it should do the same thing. It was: ```
dd if=/dev/zero of=/media/host/wubi/disks/extra.virtual.disk bs=1M count=1024
```

I also wanted to ask, shoudl the file be how much i want to increase it or the end-size? 

I also don't think that the problem is here, since the command that was giving me an error was ```
sudo mkfs.ext3 /dev/loop4 
``` which to me hardly seems to have anything to do with the newly creatd file. Although i must admit, i'm very blurry as to what it is it actually does.

---

### Post by tuxcantfly on 2007-07-20
Try this instead:

```
sudo mkfs.ext3 -F /media/host/wubi/disks/extra.virtual.disk
```

> Although i must admit, i'm very blurry as to what it is it actually does.

It formats the virtual disk file as an ext3 filesystem so that it can be mounted when Wubi boots.

---

### Post by ChaoticMind on 2007-07-22
I'm guessing you meant: 
```
sudo mkfs.ext3 -F /media/host/wubi/disks/extra.virtual.disk
```
I did that, and it seemed that the format went well. However, it doesn't help with my problem. It still gives the same thing when i go back to the following three steps described in the guide: 
```
sudo mkfs.ext3 /dev/loop4 
sudo mount /dev/loop4 /media/extra
sudo rsync -avx /home/ /media/extra
```

in other words, I'm still guetting the same error as described in the first post..

---

### Post by tuxcantfly on 2007-07-22
Try this, and do NOT follow the commands on the guide, this should do the same thing:

```
cd /media/host/wubi/disks
dd if=/dev/zero of=extra.virtual.disk bs=1000 count=0 seek=$[1000*1000*10]
sudo mkfs.ext3 -F /media/host/wubi/disks/extra.virtual.disk
sudo mount -t ext3 -o loop /media/host/wubi/disks/extra.virtual.disk /media/extra
sudo rsync -avx /home/ /media/extra
sudo umount /media/extra
```

Then afterwards boot Windows and move your C:\wubi\disks\home.virtual.disk to somewhere safe and rename C:\wubi\disks\extra.virtual.disk to C:\wubi\disks\home.virtual.disk and reboot to Ubuntu.

---

### Post by ChaoticMind on 2007-07-25
hmm, it still didn't work. This time however, the problem is different. My PC is simply freezing midway through the rsync step (I tried twice, froze at different places). I'm not sure you can help me much there... If you have any ideas, that's great, otherwise it's not that big of a deal since i will probably be getting new hardware and installing things from scratch in a month anyway... 

In any case, thanks for your help :)

---

### Post by tuxcantfly on 2007-07-26
Try doing the same thing again, only instead of the rsync command, try this:
```

sudo cp -r --preserve /home/ /media/extra
```

PS, make sure to give it lots of time (30 min - 1 hour, maybe more if you have more than a few gigabytes of data in /home)

---

### Post by jshbbe on 2007-07-28
I'm having the exact same problem as ChaoticMind, and I have tried everything that you have said in this thread.  I just tried:

```
sudo cp -r --preserve /home/ /media/extra
```

That just froze my computer again.  I let it sit for over an hour and it didn't do anything.  I couldn't click on anything, and I couldn't shut down my computer.  So I tried to manually restart my computer, but then Ubuntu wouldn't load.  I had to go back into Windows and uninstall and reinstall everything again.  This has been my 5th or 6th time installing Ubuntu using Wubi, and it would be nice if there was a quick and easy way to increase my virtual disk size.

---

### Post by Sceotend on 2007-08-03
I was having the same problems, but have managed a workaround that resolved the issue.  There are two things that I did differently from the instructions, though, either one of which may have been the solution.

I followed all the steps as previously outlined, except for a change to the mount command.  I noticed in the /etc/fstab that all the virtual filesystems are mounted with options 'loop,sync', and the command being provided only has loop.  So I added sync to the mount command...

```

sudo mount -t ext3 -o loop,sync /media/host/wubi/disks/extra.virtual.disk /media/extra

```

The next thing I did was to exit the GUI completely.  Close all the windows and log out, then switch to one of the text-based console screens using CTRL-ALT-F1.  Log in with the same username/password you use at the GUI.  Its a scary place, but works the same as being in a terminal on the GUI.

From there, the rsync command ran smoothly with no hangs.  You might want to paste the command into a text file in your home directory before you exit the GUI, then run it as a script.

---

### Post by ChaoticMind on 2007-08-24
Late reply, but i finally tried it again, and thankfully it worked. 

I tried to use cp instead of rsync, but it froze as well. 

Next I went back to rsyncing with the sync option when i mounted the 'extra' partition, as suggested by Sceotend. It still froze, but it seemed to me that it took longer to do so, although it might have been a coincidence. Most of my stuff was copied, so i restarted, and figured i'd check if rsync actually resumes before going to the terminal view, and it did. I should have tried this before, i think it probably would have worked back then. Anyway, it copied the rest of the files, and now i'm on a bigger partition \o/ 

Thanks for all the help :)

---

### Post by tuxcantfly on 2007-08-24
virtual disk resizing support has been incorporated into LVPM, you can use that instead. LVPM at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

### Post by mvisconte on 2007-08-26
Unfortunately, for those of us who don't Linux often, the process is still confusing.  

I initially did Wubi w/ a 4G size, which resulted in 3.285 for System, .231 fo home, and a swap disk of indeterminate size.

My System is full (got carried away adding programs), and I would like to expand it so that Ubuntu runs well again.  I have 88M of space left.  

I d/l the LVPM deb file, and tried to install it, but I get two errors:  I am missing zenity and gksu.  

OK, I am confused.  What am I doing wrong?

Also, is there a way to get a list of the stuff I added (I added a LOT) and I will just un- and re-install Wubi w/ a larger virt partition.

M

---

### Post by tuxcantfly on 2007-08-26
> **mvisconte said:**
> Unfortunately, for those of us who don't Linux often, the process is still confusing.  

I initially did Wubi w/ a 4G size, which resulted in 3.285 for System, .231 fo home, and a swap disk of indeterminate size.

My System is full (got carried away adding programs), and I would like to expand it so that Ubuntu runs well again.  I have 88M of space left.  

I d/l the LVPM deb file, and tried to install it, but I get two errors:  I am missing zenity and gksu.  

OK, I am confused.  What am I doing wrong?

Also, is there a way to get a list of the stuff I added (I added a LOT) and I will just un- and re-install Wubi w/ a larger virt partition.

M

You should just be able to double-click the LVPM deb file, and it'll start GDebi, or if you're using Kubuntu, first install zenity and gksu using this command:

```
sudo apt-get update
sudo apt-get install zenity gksu
```

then use the package installer to install LVPM; then you can either upgrade your install to one with dedicated partitions or expand the size of your virtual disks.

---

### Post by mvisconte on 2007-08-27
> **tuxcantfly said:**
> You should just be able to double-click the LVPM deb file, and it'll start GDebi, or if you're using Kubuntu, first install zenity and gksu using this command:

```
sudo apt-get update
sudo apt-get install zenity gksu
```

then use the package installer to install LVPM; then you can either upgrade your install to one with dedicated partitions or expand the size of your virtual disks.
[I]"You should just be able to double-click the LVPM deb file, and it'll start
  GDebi, or if you're using Kubuntu, first install zenity and gksu using this 
 command:"[/I]

I ran a command to install LVPM, which threw the Zenity and gksu errors.  I haven't been able to load zenity, but I will try your suggestion tomorrow.

[I]"Code:
sudo apt-get update
sudo apt-get install zenity gksu[/I]

*then use the package installer to install LVPM; then you can either upgrade your install to one with dedicated partitions or expand the size of your virtual disks.*

I'll have tp go with the *expand the size of your virtual disks..*.  The laptop is a borrowed machine, so there is little I can do at the loaest levgela tomoaske it 

Don't lklknoe hoeiqeee isntassgbret5yhgujgfbfdcccfgg.

---

### Post by realbadapple on 2007-08-28
> **tuxcantfly said:**
> virtual disk resizing support has been incorporated into LVPM, you can use that instead. LVPM at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)
I first tried the new LVPM approach and I had similar hang issues as the original poster of this thread. I am using LVPM 7.7 so it should work but hangs during copying (rsync'n). My recommendation for any one wishing to expand their home or system.virtual.disk is to use tuxcantfly's earlier post in this thread only use the 'loop,sync' option instead of just 'loop' when mounting the extra.virtual.disk before rsync'n the appropriate directories.

---

### Post by hh93 on 2007-08-28
Hi All,

Just wanted to list steps i did to resize my home disk.

1. downloaded and installed LVPM ([http://sourceforge.net/project/showf...roup_id=198821](http://sourceforge.net/project/showf...roup_id=198821))
2. Ran LVPM (Applications --> System Tools --> LVPM
3. Waited until pop up windows appears, selected task 'resize home'.
4. Inputed the new size
5. Waited until the program finish creating a new disks file, copying files from original home disk file and pop up a final instruction window instructing to backup the original home disk file and renaming the newly created disk file
6. booted into windows, navigated into c:\wubi\disk; noticed 4 files including new.virtual.disk, verified it's size.
7. moved home.virtual.disk to a different folder as backup, renamed new.virtual.disk as home.virtual.disk
8. Reboot into ubuntu

some screenshots attached; hope this helps.

---

### Post by tuxcantfly on 2007-08-28
Since people seem to be reporting more success with the -o loop,sync option, I've made that the default in LVPM, see lvpm 78

---

### Post by tuxcantfly on 2007-08-28
Thanks for the nice instructions hh93, just noticed I forgot to post them on the main site, so I've updated them with your screenshots and instructions

---

### Post by hh93 on 2007-08-28
> **tuxcantfly said:**
> Thanks for the nice instructions hh93, just noticed I forgot to post them on the main site, so I've updated them with your screenshots and instructions

Glad if it helps; the thanks is yours though, for working it out fervently.

---

### Post by joelj on 2008-11-20
Well no need to exit the gui,

the system crashes and hangs were caused by the fact that the mounted drive being copied to itself recusively.

follow this and it will be fine,
```

cd /host/ubuntu/disks
dd if=/dev/zero of=extra.virtual.disk bs=1024 count=0 seek=$[1024*1024*10]
sudo mkfs.ext3 -F /host/ubuntu/disks/extra.virtual.disk
sudo mount -t ext3 -o loop /host/ubuntu/disks/extra.virtual.disk /media/extra
sudo rsync -avx / --exclude=./host --exclude=./lost+found --exclude=./media --exclude=./tmp --exclude=./home/joel/extra.virtual.disk /media/extra/
sudo umount /media/extra

```

btw change "joel" to your username, THIS IS IMPORTANT TO AVOID SYSTEM CRASH.

any additions to this are welcome.

---

