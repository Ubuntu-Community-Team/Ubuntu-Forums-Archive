---
title: "account problem"
date: 2015-05-21
forum: General Help
---

### Post by wyndlass on 2015-05-21
i don't know if i'm the only one to have this problem.  i am exploring different distros and tried to use unetbootin to put an iso on a flash drive, i can't remember the particular distro now,  and rebooted after that was finished but that for some reason didn't work. now when i boot into ubuntu, 15.04 and try logining into my account it just goes into a loop back into the login screen. i can do guest just fine. also grub isn't showing me the bootup menu. i don't know what happened and can't figure out what happened. i tried doing a repair with the live cd but don't want to format the hd. i have a samsung np-nc10 atom cpu, 2 gig ram, 250 gb hd, and atheros wireless n card. i think that if i can get the grub menu back up i can fix the account problem, tho i could be wrong.  what can i do to fix this without reformatting? thanx in advance.

---

### Post by grahammechanical on 2015-05-21
The last Linux we install will put its version of Grub in charge of the boot menu. It will look on its partition for its Grub configuration files. So, you have a non-working installation in charge of the boot menu.

You can try loading the Ubuntu live session and using file manager to access the hard drive. That will mount the hard drive. Then open the terminal and run

```
sudo grub-install /dev/sda
sudo update-grub
```

That will might give you a grub boot menu that will load 15.04. I cannot advise about the login problem.

Regards

---

### Post by Bashing-om on 2015-05-21
wyndlass; Hi ! Welcome to the forum.

Here is the deal. The last system installed is the controlling boot authority. Perhaps what you have done is to remove that controlling authority.
Now what we can do is (RE-)install ubuntu's grub such that it now has that control.
We start by knowing what that controlling authority will be, and where on the hard drive it is installed to.
Post back - Between Code Tags, please - the outputs of terminal commands ( from a liveDVD(USB) :
```

sudo fdisk -lu
sudo parted -l
sudo blkid

``` to tell us what/where, and then we can know the how .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Sebastian_Kindler on 2015-05-24
As I encountered the login loop two days ago, I thought I should share.


(I run Ubuntu 14.04 on an ASUS S400CA, though, and wyndlass' login loop may well be connected to changing linux distributions or driver issues. Anyway, this is for people new to Linux.)


Searching for a solution in other threads, you will find there is one dominant solution: access privileges for both of the files, .Xauthority and .IDEauthority.


How to find whether or not you "own" those files?


Login as Guest, which you have probably done anyway to use the internet.


Open a login terminal with Ctrl + Alt + F2, or alternatively, + F3, + F4, and so on until F6.


Ctrl + Alt + F7 brings you back to your "Desktop", so you can switch back and forth.


(I will use ASUS-S400CA as an example.)


```

Ubuntu 14.04.2 ASUS-S400CA tty2


ASUS-S400CA login:



```


Type in your username. (Your username is the nickname you chose at installation, not your full name you may see on your actual login screen.)


Then type in your password.


```



Ubuntu 14.04.2 ASUS-S400CA tty2


ASUS-S400CA login: yourusername


Password:



```


You should now see:


```



yourusername@ASUS-S400CA:~$



```


If your login loop is caused by missing access privileges for the files mentioned earlier, this code should do:


```



ls  -ld  ~/.*authority



```


If you then get


```



-rw------- 1 root root 2015 May  24 12:38 .ICEauthority


-rw------- 1 root root 2015 May  24 12:38 .Xauthority



```


instead of


```





-rw------- 1 yourusername yourusername 2015 May  24 12:38 .ICEauthority


-rw------- 1 yourusername yourusername 2015 May  24 12:38 .Xauthority



```


you have to use the chown command to get back your access privileges:


```



sudo  chown  yourusername:yourusername  ~/.Xauthority



```


and if necessary the same for .IDEauthority. Note that you will have to verify the result again with the ls command. No error message is a good sign, though.




Your shell does not recognize any of the commands you type in?


This could be the main cause for the login loop as login itself is just a command.



How to use commands under these circumstances?


The shell gives you two pieces of information: First, the command is not accessible. Second, it is found in, e.g.


```



/usr/bin



```


In this case the above mentioned code looks - depending on where "the executable" of the command is located in your system - something like this:


```



/usr/bin/ls   -ld   ~/.*authority


/usr/bin/sudo  /bin/chown   yourusername:yourusername   ~/.Xauthority


/usr/bin/sudo  /bin/chown   yourusername:yourusername   ~/.IDEauthority



```




The reason why your command prompt (shell, Terminal, command line) recognizes and executes commands - including the login command - is, because the paths to their directories - like /usr/bin, /bin, /sbin and so on - are all saved in a file. There they are given as the value to a variable called PATH. (For easy to understand explanations on Linux terms check out linfo.org. In this case [linfo.org/path_env_var.html]("http://linfo.org/path_env_var.html"))




To check, which paths are saved in PATH, type


```



echo $PATH



```


or its equivalent command with directory structure.


It will probably give you something like


```



/usr/local



```


However it should look like:


```



/usr/bin:/usr/sbin:/bin:/sbin:/usr/local/:/usr/local/bin:/usr/local/sbin



```


The different directories between the colons can be arranged in any order.




To save those temporarily, and be able to use commands, type


```



export PATH=$PATH:/usr/bin:/usr/sbin:/bin:/sbin:/usr/local/:/usr/local/bin:/usr/local/sbin



```




To make those changes permanently, you have to save it in the respective file, where your PATH variable is defined.


Depending on your type of shell (bash etc.), this could be a different file, and there are certain (new) conventions about in which (configuration) file to exactly save those paths to your commands. ([unix.stackexchange.com/questions/88201/whats-the-best-distro-shell-agnostic-way-to-set-environment-variables]("http://unix.stackexchange.com/questions/88201/whats-the-best-distro-shell-agnostic-way-to-set-environment-variables"))


In your home directory ~ , which is equivalent to /home/yourusername, there should be a file called .profile. If you temporarily saved your directories to your commands you can open that file by typing


```



sudo gedit ~/.profile



```


This opens the file with the respective text editor gedit. (Just in case you do not have gedit for some reason, use the aptitude or apt-get command in combination with sudo and install gedit or any text editor you prefer: sudo apt-get install gedit .)


At the end of that file you probably find something like:


# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi


PATH=usr/local




However, PATH should be defined just as described above. Simply, add the other directories:


PATH=/usr/local:/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin


save the file, reboot your system, and you should (hopefully) be good to go.

---

### Post by wyndlass on 2015-05-26
The last Linux we install will put its version of Grub in charge of  the boot menu. It will look on its partition for its Grub configuration  files. So, you have a non-working installation in charge of the boot  menu.

You can try loading the Ubuntu live session and using file manager to  access the hard drive. That will mount the hard drive. Then open the  terminal and run

 	Code:
 	sudo grub-install /dev/sda
sudo update-grub 
That will might give you a grub boot menu that will load 15.04. I cannot advise about the login problem.




i get this error when i use your idea, maybe i am missing something

"grub-install: error: failed to get canonical path of `/cow'.'"

i never heard of a directory or file name just cow.. i even tried running sudo grub-install /dev/sdb, would be my flash drive i believe, and get the same error. i would've replied sooner if i had the time to, had my ubuntu hd in my laptop, and internet connection to do so. also i'm doing the above command in live cd on the flsh drive. what exactlyis grub trying to find  and not thus the error???  btw my laptop is a netbook with no aoptical drive at all. i do know this for a fact since i've opened the case many times jusrt to switch tween windows xp and ubuntu.

---

### Post by Bashing-om on 2015-05-26
wyndlass; Hang in there .

My post #3 please. Then we know what partition is what, then we can mount the ubuntu partition, then we can install ubuntu's boot loader.
Until I "see" what is. I can offer no further advise.
Please post the terminal command outputs between code tags to maintain formatting and promote readability:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by wyndlass on 2015-05-26
> **Bashing-om said:**
> wyndlass; Hi ! Welcome to the forum.

Here is the deal. The last system installed is the controlling boot authority. Perhaps what you have done is to remove that controlling authority.
Now what we can do is (RE-)install ubuntu's grub such that it now has that control.
We start by knowing what that controlling authority will be, and where on the hard drive it is installed to.
Post back - Between Code Tags, please - the outputs of terminal commands ( from a liveDVD(USB) :
```

sudo fdisk -lu
sudo parted -l
sudo blkid

``` to tell us what/where, and then we can know the how .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


sudo fdisk -lu

```
Disk /dev/loop0: 1.1 GiB, 1147891712 bytes, 2241976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc33206c4

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sda1  *      2048    499711    497664   243M 83 Linux
/dev/sda2       501758 488396799 487895042 232.7G  5 Extended
/dev/sda5       501760 488396799 487895040 232.7G 8e Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 230.7 GiB, 247661068288 bytes, 483713024 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/mapper/ubuntu--vg-swap_1: 2 GiB, 2134900736 bytes, 4169728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sdb: 30.5 GiB, 32717537280 bytes, 63901440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc3072e18

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *       32 63901439 63901408 30.5G  c W95 FAT32 (LBA)



```

```

sudo parted -l

Model: ATA WDC WD2500BEVT-6 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   250GB  250GB  extended
 5      257MB   250GB  250GB  logical                lvm


Model: PNY USB 2.0 FD (scsi)
Disk /dev/sdb: 32.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  32.7GB  32.7GB  primary  fat32        boot, lba


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 2135MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  2135MB  2135MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 248GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  248GB  248GB  ext4



```



```


sudo blkid

/dev/dm-0: UUID="c0e4e45f-a073-4304-a1c1-ee7a22352ee9" TYPE="ext4"
/dev/sda1: UUID="124aa627-5312-4987-a1b6-09a1228eee89" TYPE="ext2" PARTUUID="c33206c4-01"
/dev/sdb1: UUID="C46C-26F3" TYPE="vfat" PARTUUID="c3072e18-01"
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="KWyjAe-j1MT-MwnI-3guh-7Zt9-kpmw-13X4F3" TYPE="LVM2_member" PARTUUID="c33206c4-05"
/dev/mapper/ubuntu--vg-swap_1: UUID="b1944dcc-c9c8-499b-bd17-aed8081b9792" TYPE="swap"



```


these are the results that i get for each of the three commands.

---

### Post by Bashing-om on 2015-05-26
wyndlass; Great !

At the least we know now where we stand.

Now the bad news - Logical Volume Management (LVM) and possibly encryption on the file system. I have no experience with them and thus am no longer qualified to offer advise.

Let us wait for those who have the experience to assist .

[INDENT]if I knew everything
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wyndlass on 2015-05-26
well, i fixed the problem by using adduser as root and creating a new account. now i need to transfer stuff over to the new account. i'm still having trouble with getting grub to show back up at bootup. grub-install works, i just wasn't working as root for it to i guess. update-grub is giving me problems


[code]

Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done


[code]

this is the output i get. thanx for trying to help with the account login problem, now if i can just fix grub....

---

### Post by Bashing-om on 2015-05-26
wyndlass; Hey ..

One way to go ! Making progress.

With only one operating system installed on the system, the default is not to display a grub boot menu.
If desired that behavior can be changed .
One can display the grub menu by booting the system and as soon as the bios screen clears, depress and hold a shift key.


[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by wyndlass on 2015-05-27
thanx bashing. i would like the menu to always be there at boot in case i have problems. i'm not sure what to do for that tho. i have used ubuntu over the years but not with enough regularity to learn alot or to remember it all, yet. i think my first experience was in late 2005.

i googled and checked several web sites to learn how to get grub to show the menu on a single boot system and the all had the same info on that so now i know what to do there. i appreciate the help from all of you. thanx

---

### Post by Bashing-om on 2015-05-27
wyndlass; Outstanding;

You do good work. Learning grub is a great way to gain a lot of insight into this operating system.
One can start here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) <=drs305 all about grub 2
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If this matter is now concluded;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)


[INDENT][INDENT]seek and ye shall find
[/INDENT][/INDENT]

---

### Post by wyndlass on 2015-05-28
i try to figure stuff out on my own til i get too frustrated then ask for help. i shoulda thought about creating a new account sooner, i was like homer simpson, "Duh!. ](*,)  i added a .jpg to my grub menu. now i see it with a wallpaper pic. i love to learn new thing and ,for me, linux(especially ubuntu) is the newest thing that i can relate to. my puter that i owned was trs-80 model 3 with ldos and trs-80 dos. my first pc was an acer 286 with ms-dos 5 that i eventually upgrade to 6.22. command line stuff is new to me, but of course tween dos and linux there are many differences that i'm still learning about, and always will. in case you don't know the trs-80 model 3's were made in the 70's and my serial number was 10. i don't have any of my old puters anymore

---

### Post by Bashing-om on 2015-05-28
wyndlass; Hey;

Off Topic; but .. Yeah .. I do recall what was fondly called the "Trash80". I came up on mainframes and this one too was  of consideration in my choice of my 1st PC, my choice was a 1st edition Amiga 1000. It had a whopping 512 megs of ram ! And for a Thousand dollars  I got a 1Gig memory expansion board ( later on) .

And Yes agree, this -ubuntu - is the system to learn on. It is constantly evolving and is on the the cutting edge of technology and it's implementation . However cutting edge it may be, it is tested and it just works ! When it fails, we have the support and documentation to learn why not.

Grub; customizing:
Best I have seen:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen) <-Cavsfan

[INDENT][INDENT]who knows what tomorrow will bring
[/INDENT][/INDENT]

---

### Post by wyndlass on 2015-05-29
i'll work on customizing grub to how i like it, i pdfed that article and in the preview i seen the colour list and was like i should change colours to make it easier to see. i even need to change the font size as well.

---

### Post by Bashing-om on 2015-05-29
wyndlass; Yep;

All doable using Cavsfan's wiki as the guide.

There is an active thread on the guide :
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
with a fast response rate for any questions you might have in respect to the guide.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all things are possible[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

