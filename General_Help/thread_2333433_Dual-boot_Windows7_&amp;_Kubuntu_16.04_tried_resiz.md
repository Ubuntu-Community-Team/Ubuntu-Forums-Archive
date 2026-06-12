---
title: "Dual-boot Windows7 &amp; Kubuntu 16.04 tried resize partition now grub rescue"
date: 2016-08-10
forum: General Help
---

### Post by boxcorner on 2016-08-10
Could someone help me, please?
    My Lenovo Z570 laptop is/was configured for dual-booting Windows 7 & Kubuntu 14.04 LTS
    I wanted to reduce the size of the Windows partition in order to allocate more space for Kubuntu.
    So, I backed up my data to an external drive.
    I booted from a memory key containing Kubuntu 16.04 LTS
    I think I was using KDE Partition Manager (but it might have been GParted that I was using early this morning). Sorry my memory is a bit hazy this evening.
    I've had a calamitous day, am only just getting back to trying to fix this problem.
    Currently, when the laptop is started, it displays : grub rescue.
    I have been trying to locate which is the root drive.

    What I have tried :
    
    I found info that seemed helpful here :
    [https://www.quora.com/How-do-I-fix-a-grub-rescue-unknown-file-system-error](https://www.quora.com/How-do-I-fix-a-grub-rescue-unknown-file-system-error)
    
When I tried, this was the result :

    grub rescue>
    ls
    (hd0) (hd0,msdos8) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0,msdos4)
    (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)
    grub rescue>
    set prefix= (hd0,msdos1)/boot/grub
    error: unknown filesystem
    set prefix= (hd0,msdos2)/boot/grub
    error: unknown filesystem
    set prefix= (hd0,msdos3)/boot/grub
    **error: no such partition**
    set prefix= (hd0,msdos4)/boot/grub
    error: unknown filesystem
    set prefix= (hd0,msdos5)/boot/grub
    error: unknown filesystem
    set prefix= (hd0,msdos6)/boot/grub
    error: unknown filesystem
    set prefix= (hd0,msdos7)/boot/grub
    **error: attempt to read or write outside of partition**
    set prefix= (hd0,msdos8)/boot/grub
    error: unknown filesystem

    I can still boot into 16.04 LTS from the memory key.
    When I open Dolphin, on the left-hand side under Devices :
    Loop Device
    KUBUNTU16_
    200.0 MiB Hard Drive <<== this contains folder called Boot
    53.7 GiB Hard Drive
    LENOVO_PART
    3.0 GiB Hard Drive
    New Volume
    301.4 GiB Hard Drive <<== when I select this a red panel is displayed :

    An error occurred while access 'Home', the system reponded. The requested operation has failed. Error mounting /dev/sda7 at media/kubuntu/93cf7a70-d7770=487b-af12-dd7baf23eac: Command-line 'mount-t "ext4" -o "uhelper=udisk2,nodev.nosuid" "/dev/sda7" "edia/kubuntu/93cf7a70--487b-af12-dd7baf823eac" exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda,
    missing codepage or helper program, or other error
    In some cases useful info is found in syslog - try
    dmesg | tail or so.
    
    Well, that was day before yesterday. I tried to post a new thread. It wouldn't let even though I was logged in and had permission to create new threads.
    
    I will try again now  ... 
    
    Forbidden

You don't have permission to access /newthread.php on this server.
Apache/2.4.7 (Ubuntu) Server at ubuntuforums.org Port 443


    So, today I tried something else. I discovered something on ubuntu.com 
    It's called : Boot-Repair
    I booted Xubuntu 16.04 LTS from a memory key
    Then I made a connection to the Internet 
    sudo add-apt-repository ppa:yannubuntu/boot-repair
    sudo apt-get update
    sudo apt-get install -y boot-repair && boot-repair
    
    boor-repair
    "Recommended repair"
    Then it worked and reported problem fixed, re-boot.
    [http://paste2.org/hEdk606e](http://paste2.org/hEdk606e)
    So, I rebooted :
    error: attempt to read or write outside of partition.
    Entering rescue mode ...
    grub rescue>
    
    So, I ran it again & same thing happened, reported problem fixed, reboot.
    [http://paste2.org/FA3N95KF](http://paste2.org/FA3N95KF)
    So, I re-booted, again
    **error: attempt to read or write outside of partition.**
    Entering rescue mode ...
    grub rescue>
    
I emailed details to boot.repair@gmail as requested, but haven't received a reply (yet).
I don't what time zone they are in ; maybe I should wait longer ...
That was yesterday.
    Today I'm out of ideas
    What should I do to restore access to my data on the HD in my laptop?
Any help would be much appreciated.
Thank you in advance.

**Addendum**
While endeavoring to run boot-repair again, earlier,
when I ran sudo apt-get update
after the line Get: 35 it reported :
** (appstreamcli:2788) : CRITICAL **: Error while moving old database out
of the way. Appstream cache update failed.
Reading package lists... Done

I did not notice this yesterday.
I have reported this to [email]boot.repair@gmail.com[/email] but have not received any reply.
My options seem to be :
1 - Wait for a reply from the developer of boot-repair
2 - Wait for a reply from someone on this forum
3 - Try to recover Windows 7. Lenovo provides OneKey recovery from hard disk, no CD-ROMs. I don't know whether it would work, as I am unable to boot the computer
4 - Try to find some way of creating a bootable copy of 14.04 LTS. Difficult without my computer & Internet access. The notebook that I am using to type this, which has 16.04 LTS is pitifully slow. I have reduced swappiness but that hasn't helped much.
5 - Install 16.04 LTS from memory key, which I used to install 16.04 LTS on this notebook & which I can use to boot the Lenovo. As my 14.04 LTS data was backed up using KDBackup I'm not sure it would restore to 16.04 LTS assuming I can remember all the apps that I would need to install beforehand.

I'm running out of ideas again. Any help would be much appreciated.

---

### Post by yancek on 2016-08-10
Your problem is shown in the boot repair output and boot repair tried to run filesystem check and failed.  I'd try doing an online search or a search here at the forums on "how to repair corrupt superblock or partition table" while waiting for a response here.

> Either the superblock or the partition table is likely to be corrupt!

When resizing a windows partition, it is always best to use the windows tools such as Disk Management and when that completes, reboot and run chkdsk.
The boot repair output generally shows the boot files available on the Linux partition but that is not the case here due to filesystem corruption.  Not sure how you would repair this, hopefully someone else will come along.  The only thing you might try is to use testdisk if you have another computer with an internet connection.  The site is the first link below.  The second link contains a Step By Step guide to using testdisk if you scroll down the page a bit.

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

---

### Post by oldfred on 2016-08-10
Boot-Repair is saying sda7 is corrupt, normally it does try to run fsck.
But usually better to run full fsck.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda7 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda7
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda7

But in one place it also says sda4 is NTFS, but partition table says it is XENIX root.
I would use Disks to change type to 07 (not format) or manually change type to 07 and then run chkdsk on sda4 from Windows.

      
 change sda4 to type 07
sudo sfdisk --change-id /dev/sda 4 07 
Note: sfdisk in 16.04 updated to include gpt and commands may have changed some.

---

### Post by boxcorner on 2016-08-10
Many thanks for your helpful reply.

---

### Post by boxcorner on 2016-08-10
> **oldfred said:**
> Boot-Repair is saying sda7 is corrupt, normally it does try to run fsck.
But usually better to run full fsck.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda7 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda7
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda7

But in one place it also says sda4 is NTFS, but partition table says it is XENIX root.
I would use Disks to change type to 07 (not format) or manually change type to 07 and then run chkdsk on sda4 from Windows.

      
 change sda4 to type 07
sudo sfdisk --change-id /dev/sda 4 07 
Note: sfdisk in 16.04 updated to include gpt and commands may have changed some.

Many thanks for your helpful reply. I'm not sure that I fully  understand, so I want to be sure before I try doing anything, in case I  make matters worse. 

I presume everything is unmounted, when the computer switched on and it says boot rescue. 
Is my assumption correct?
I don't understand what you mean by "swap off if necessary.
When I switch the computer on, without the USB key, it says boot rescue.
When I switch the computer on, with the USB key, 16.04 LTS boots all right.
What do you mean by "change example shown", which example, where?
Are the lines in your message which are prefixed # meant as comments?
Are you suggesting that I run the following three lines of code that are in your message?
sudo e2fsck -C0 -p -f -v /dev/sda7
sudo e2fsck -f -y -v /dev/sda7
sudo sfdisk --change-id /dev/sda 4 07 
Run them one at a time, and report results, before moving on?

---

### Post by oldfred on 2016-08-10
The commands posted are an example, so others that may see thread could also use it. My normal example uses sdb1, and says to change to yours, I already edited it.

The live installer normally mounts swap. Some things cannot be done with swap mounted. I think the commands you are running, whether swap is mounted or not, does not matter.
But just clicking on sda7 will try to mount it in live installer. Make sure you have not mounted it.
You can check what is mounted:
mount

---

### Post by boxcorner on 2016-08-10
> **oldfred said:**
> The commands posted are an example, so others that may see thread could also use it. My normal example uses sdb1, and says to change to yours, I already edited it.

The live installer normally mounts swap. Some things cannot be done with swap mounted. I think the commands you are running, whether swap is mounted or not, does not matter.
But just clicking on sda7 will try to mount it in live installer. Make sure you have not mounted it.
You can check what is mounted:
mount

Thanks again.
I ran ;
sudo e2fsk -C0 -p -f -v /dev/sda7
it reported :
/dev/sda7: The filesystem size (according to the superblock) is 155992576 blocks
the physical size of the device is 79009280 blocks
Either the superblock or the partition table is likely to be corrupt!
/dev/sda7: UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY.
(i.e. without -a or -p options)

When I type the following, in Terminal when the computer is booted from USB containing 16.04 
sudo fsck
fsck from util-linux 2.27.1

When I just type :
fsck
fsck from util-linux 2.27.1

What am I doing wrong, please?

**Addendum (updated)**

Should I be typing :
sudo fsck /dev/sda7
?
I guessed fsck is benign so I ran :
fsck from util-linux 2.27.1
The filesystem size (according to the superblock) is 155992576 blocks
the physical size of the device is 79009280 blocks
Either the superblock or the partition table is likely to be corrupt!

So I will now try the 2nd line of code that you gave me.

[B]Updated

[/B]sudo e2fsck -f -y -v /dev/sda7
e2fsck 1.42.13 (17-May-2015)
The filesystem size (according to the superblock) is 155992576 blocks
the physical size of the device is 79009280 blocks
Either the superblock or the partition table is likely to be corrupt!

So, I will now try the 3rd line of code that you gave me.

---

### Post by oldfred on 2016-08-10
The third line is just to allow you to boot Windows if Windows type boot loader in MBR.

fsck & e2fsck are the same.
The second e2fsck was without the -p option, but it still failed. Or major issues.
You do have good backups? Both Windows & Ubuntu?

You are now into advanced repairs, that may or may not work, or even cause more damage.
 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda7 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda7
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by boxcorner on 2016-08-10
> **oldfred said:**
> The third line is just to allow you to boot Windows if Windows type boot loader in MBR.

fsck & e2fsck are the same.
The second e2fsck was without the -p option, but it still failed. Or major issues.
You do have good backups? Both Windows & Ubuntu?

You are now into advanced repairs, that may or may not work, or even cause more damage.
 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda7 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda7
One user could not get partition unmounted (may have needed swapoff), but used another live distro

I ran sudo sfdisk --change-id /dev/sda 4 07
but was interrupted by supper, needed to take meds 
anyway, here's what it reported :
sfdisk: change-id is deprecated in favour of --part-type
The partition table has been alterred.
Calling ioctl() to re-read partition table.
[B]Re-reading the partition table failed.: Device or source busy <<== this was displayed in red
[/B]The kernel still uses the old table. The new table  will be used at the next reboot or after you run partprobe(8) or kpartx(8).
Syncing disks.

I will now read your message above and will not do anything (ie I will not reboot etc.) until told to do so otherwise.
It seems that I'm in dire straits. I don't want to make it worse, in case it can be recovered.

**Addendum**

I do have good backups of Kubuntu, created using KBackup (if I recall the name correctly). 
Most recent was created immediately before I attempted to alter partition sizes.
I'm afraid I don't have a recent backup of Windows. 
I know I should have, but I'm afraid I didn't really think about it.
It's ages since I've used Windows. 
I've got so used to using Ubuntu for years, more recently Kubuntu, that I forgot to backup Windows.
I only use it to update my Garmin GPS. 
I can't remember anything else, other than a Nokia phone which I no longer use.
I only ever use Windows, when I cannot find a Linux version of an app.
Any Windows backup would be very old.
The Lenovo laptop has something which I think is called OneKey Recovery. 
I have never used it, so I don't really know what it does.
I have no idea whether it would work. 
I don't really know how it is meant to be used, but guess the OneKey button should be pressed during boot.
[B]
Further update

[/B]All right. I hear what you are saying about advanced recovery.
I accept it might make matters worse, and accept I'm to blame for creating this mess.
Before I launch into following those links, 
do you think it would be worth me trying the OneKey Recovery button, for Windows?
When I bought the Lenovo laptop, it had Windows 7 already installed on it.
I installed Ubuntu for dual boot, having previously done so on the desktop PC that I used to use.
As I have a good backup of Kubuntu and not of Windows, 
and I don't have much to lose as regards Windows,
do you think it worth trying OneKey, or would it be better to proceed as you outlined for advanced recovery?

[B]Another question

[/B]If the OneKey Recovery enabled me to use Windows, 
could I use the Kubuntu backup that I created using 14.04 if I installed 16.04 from the USB key?
I realise I would need to reinstall the apps that I was using, before restoring from the backup.
What I'm not sure is whether or not the backup is version specific.
The problem is I don't have a bootable copy of 14.04 on CD-ROM or USB, 
so I would need to create one. Note easy on this slow notebook.

**Correction**

I have found a USB key with a bootable copy of Ubuntu 12.04 LTS (but not 14.04 LTS).
I have found a copy of Lenovo's manual online, so I now know how to use OneKey Recovery.
Device labelled LENOVO_PART contains a folder called OneKey, which contains folders & files, so appears usable.

**Lastly, for today**

As I understand it, if OneKey Recovery restored Windows, it would be back to the factory installed version. 
Then eons of time required for downloading & installing dreaded Windows updates. 
Most likely would it destroy anything else, pretty much like reformatting.
So, I think that would have to be my last resort.
I feel more inclined to press on with attempting to recover, via the links you kindly provided,but not tonight. 
I'm too tired, so I would probably make more mistakes.
So, it will have to wait until tomorrow. Thanks again for your help.

---

### Post by oldfred on 2016-08-10
I do not know then if sfdisk command worked or not.
But that is a minor issue, compared to issues on sda7.

Do not know about backup. 
Some are images & some are files. If you updated to new version of Ubuntu, you had to make a new backup. I normally use rsync and just back up my data, export list of installed apps and some configuration settings from /etc like the grub files I manually modify.

You boot was from live installer?
So a reboot should not matter. May be best to swap off anyway just to be sure. That unmounts swap.
Use Disks or gparted to unmount swap.

First try rerunning the e2fsck commands.

---

### Post by boxcorner on 2016-08-11
> **oldfred said:**
> I do not know then if sfdisk command worked or not.
But that is a minor issue, compared to issues on sda7.

Do not know about backup. 
Some are images & some are files. If you updated to new version of Ubuntu, you had to make a new backup. I normally use rsync and just back up my data, export list of installed apps and some configuration settings from /etc like the grub files I manually modify.

You boot was from live installer?
So a reboot should not matter. May be best to swap off anyway just to be sure. That unmounts swap.
Use Disks or gparted to unmount swap.

First try rerunning the e2fsck commands.

No, the Lenovo Z5760 laptop hasn't been updated recently. 
I updated it from 12.04 LTS to 14.04 LTS ages ago.

I updated this Toshiba NB550D notebook to 16.04 LTS recently.
I am using it while trying to get my Lenovo Z570 laptop to working again.

I have a USB key with 16.04 LTS on it which I used to install 16.04 on the Toshiba notebook, as it doesn't have a CD drive.
Lenovo recognizes 16.04 on the USB key and will boot from it.

When I boot the Lenovo without the 16.04 USB key plugged in, it reports :
error: attempt to read or write outside of partition.
Entering rescue mode ....
grub rescue>

If I type :
ls
(hd0) (h0,msdos8) (h0,msdos7) (h0,msdos6) (h0,msdos5) (h0,msdos4) (h0,msdos3) (h0,msdos2) (h0,msdos1)
grub rescue>

Currently, I am trying to find how to install gparted on a USB key, to unmount swap on the Lenovo.

---

### Post by boxcorner on 2016-08-11
While downloading Tuxboot & GParted to create live installation on USB key
Rerunning the e2fsck commands
sudo e2fsck -C0 -p -f -v /dev/sda7
Unknown command 'sudo'
grub rescue>
e2fsck -C0 -p -f -v /dev/sda7
Unkown command 'e2fsck'.

Something has changed since yesterday, as today I can no longer use a wireless mouse with the Lenovo.

**Correction**

Ah, mea culpa. I remember now, I was using Terminal, that's why I was able to use a mouse.

**Addendum**

sudo e2fsck -f -y -v /dev/sda7
Unknown command 'sudo'

I will now boot the Lenovo from USB key with 16.04

So, from Terminal :

sudo e2fsck -C0 -p -f -v /dev/sda7
/dev/sda7/: The filesystem size (according to the superblock) is 155992576 blocks
The physical size of the device is 79009280 blocks
Either the superblock or the partition table is likely to be corrupt!
/dev/sda7/ UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY.
(i.e. without -a or -p options)

**Addendum**

sudo e2fsck -f -y -v /dev/sda7
e2fsck 1.42.13 (17-May-2015)
The filesystem size (according to the superblock) is 15599252576 blocks
The physical size of the device is 79009280 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? Yes

**Update**

I have now installed GParted live on a USB key
I have booted the Lenovo from the key so GParted is running

/dev/sda1 ntfs 200.00MiB
/dev/sda2 ntfs 53.72GiB
/dev/sda3 extended 629.98 GiB
/dev/sda7 EXCLAMATION MARK IN TRIANGLE ex4 301.40 GiB
unallocated 293.67 GiB
/dev/sda8 linux-swap 5.92 GiB
/dev/sda5 ntfs 3.05 GiB
/dev/sda6 ntfa New Volume 9.95 GiB
unallocated 16.3 GiB
/dev/sda4 ntfs LENOVO_PART 14.75

**Addendum**

I have turned linux-swap off
So, now there is a padlock icon, the square is red and also a padlock icon appeared alongside /dev/sda3
Furthermore, alongside /dev/sda3 there is a small triangle (drop-down) handle
Clicking on the handle collapses the list :
/dev/sada1
/dev/sada2
/dev/sada3 padlock icon | extended
/dev/sada4

I will try to append an image of GParted running on the Lenovo.
Upon further consideration, I don't think it would be easy.
Please let me know whether doing so would be helpful.

Ah, I discovered GPparted has a screenshot option - nice feature.
I grabbed an image, which GParted said was stored in Home > Users (at least that's what I think was displayed briefly).
However, I don't know how to access the image.

**Question**

Should I try : GParted > Device > Attempt Data Rescue ?

---

### Post by oldfred on 2016-08-11
Gparted is on the Ubuntu installer.
Although I often download the gparted live ISO as another repair tool. I believe gparted live ISO does not automatically mount the swap partition, where the Ubuntu live installer does.

Ubuntu terminal commands will not work at a grub> terminal. Grub as boot loader only has a few limited commands for trying to boot.

Padlock icon in gparted is partition is mounted.

Red or yellow icons in gparted indicate issues. Although new UEFI systems require some unformatted partitions which will show yellow error icons but are correct, just that they are unformatted. You can click on icon and it should tell you more about error, but I expect it to be similar to what fsck is saying.

In forum advanced mode, use paperclip icon. That should open a attach a file and you can browse to the location of the screenshot. Live installer & Ubuntu have screenshot. But if terminal output copy & paste that, do not use screenshots. If long or formatting makes it better use code tags which are the # icon in Forum's advanced editor.
       If you use the advanced editor, you can use the paperclip icon to attach screenshots. Post #4
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

---

### Post by boxcorner on 2016-08-11
Many thanks for all the info.
I will try again to grab a screenshot to show you.
I tried HOWTO: Repair a broken Ext4 Superblock in Ubuntu [https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
but it didn't work for me.

**Addendum**

The 3rd link that you gave me appears to be broken [http://planet.admon.org/using-altern...to-check-ext3/](http://planet.admon.org/using-altern...to-check-ext3/)

---

### Post by boxcorner on 2016-08-12
What I wanted to do was to grab a screenshot of the the /dev/sda - GParted window, which shows the primary and extended partitions.
I have taken screenshots grabbed using the Screenshot option in GParted, but apparently they are stored automatically in Home/Users.
I don't know how to retrieve them, as I don't have access the location where they're stored, from boot rescue prompt.
It would be more helpful if GParted allowed the user to select location where they are saved, in my case USB key.

**Correction**

Mea culpa. I can access /home via the GParted's Terminal option, but I don't seem to be able get down to /home/user
I'm going to re-start GParted in case is it's something to do with the keyboard keys.

**Addendum**

When GParted is started, a window is displayed in the top left-hand corner of the screen. 
Eventually I discovered that the window can be dragged aside with a mouse, to reveal 7 icons :
Exit, Screenshot, Terminal, GParted, Screen resolution, Web Browser & Network config.
This might seem obvious to those who have used GParted before, but it wasn't to me.
I'm mentioning it here in case it helps someone else.

Something else that it took me a while to grasp, in the bottom left-hand corner there an option enabling user to toggle between 4 workspaces.
So, for example, GParted can be displayed in workspace_1, Terminal in workspace_2, and so on.

Furthermore, it took me a while to discover that when Terminal is opened :
user@debian:~$
user@debian:~$ dir
user@debian:_$ 
user@debian:_$ cd /home 
user@debian:/home$
user@debian: dir
user
but I don't seem to be able to get into /home/user , which is apparently where Screenshot stores its images.

**Update **

Currently running testdisk in Terminal

---

### Post by boxcorner on 2016-08-12
Nothing that I've tried thus far has given me any reason to feel confident that I will be able to recover from this mess. So, while waiting for testdisk. I investigated KBackup which I used to backup my Kubuntu data. According to the KBackup handbook there there isn't any restore option. Backup files are stored in TAR format, so they recommend using konqueror, but it doesn't seem to be in either Discover Software Center or Ubuntu Software Center. I expect I'll be able to find it somehow, otherwise I will use another program to unzip the files.  Useful as I'll be able to restore data on an ad hoc basis, after I have installed relevant apps. Also, backups do not appear to be Kubuntu version specific, which allows for the possibility of installing 16.04 LTS.

So, if I am unable to recover from this mess, I will have to decide whether to attempt to restore Windows 7, via Lenovo's OneKey Recover system. Then assuming that is successful, I will install Kubuntu (either 14.04 LTS or 1604.LTS), configured for dual-boot, as it was before. Or, dispense with Windows altogether and just install Kubuntu. The latter is the most appealing.

---

### Post by oldfred on 2016-08-12
I do not need to see screenshot. It rarely shows much more than this:
       sudo parted /dev/sda unit s print 
or
sudo fdisk -lu

I have never used tar, but there is this:
[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

Back when 5 1/4 floppy disks were expensive and did not hold a lot of data, I used compression. But those disks also were not reliable, so one bit and entire disk could not be extracted. Lost lots of data. Since then I have only saved/backed up files even though it uses a lot more space. Data storage is now so inexpensive that the hassle of compression is not worth it for me.

---

### Post by boxcorner on 2016-08-12
Thanks for the link. If you remember 5 1/4 inch floppies then you probably also remember 8 inch floppies. Yes, nowadays data storage is extraordinarily inexpensive. Thankfully so.

**Addendum**

I found this :
```
sudo apt-get install konqueror
```
here :
[https://konqueror.org/download/](https://konqueror.org/download/)

---

### Post by boxcorner on 2016-08-13
This is helpful, too : Linux Partition HOWTO [http://www.tldp.org/HOWTO/Partition/](http://www.tldp.org/HOWTO/Partition/)

---

### Post by boxcorner on 2016-08-14
TestDisk is still slogging its way through my hd. Meanwhile, apart from learning a bit more about Linux, I've been reading some of the accounts given by people who have dual-boot systems and those who have tried to upgrade Windows. I've made up my mind, irrespective of whether or not testdisk succeeds in recovering some, or all, of my data, this is where I part company with Windows, which in any case I've only used once or twice a year to update my Garmin GPS maps, etc. From now on my Lenovo laptop will be solely for Kubuntu. If I need Windows then it will have to be on another machine. I don't want to repeat my present predicament, if I can possibly avoid it. Depending on what testdisk actually achieves, I might need help in removing any trace of Windows & dual-boot, but I guess the best way forward would be to reformat the hd and do a fresh installation of Kubuntu.

---

### Post by boxcorner on 2016-08-15
Success! 
Many thanks for all your help.   
I read the TestDisk step-by-step instructions.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
It paid to be patient.
TestDisk succeeded in recovering my data
Félicitations au développeur Christophe GRENIER. 
Then I used Parted Magic to copy my data to an external drive. 
Next, I made a clean installation of Kubuntu 16.04 LTS
No Windows, hence no dual-boot installation. 
So, goodbye Windows. No regrets.
Installed the applications that I had been using and then restored my data.
It worked for me.

---

### Post by oldfred on 2016-08-15
Glad you got it working. :)

---

### Post by boxcorner on 2016-08-15
Believe me, so am I :)

---

### Post by boxcorner on 2016-08-21
**Footnote** 

One of the things that I said, when I started this thread, was that I emailed Boot Repair requesting their help. Yesterday, I received the following reply :

[I]We, volunteers at Boot-Repair project, have received your request.
Please note that solving a boot problem can be long, and unfortunately
we do not have time any more to answer all requests, so we offer this
help service only to our contributors.

In order to assist you, please indicate:
1) how you have contributed to the Boot-Repair project. If you haven't
contributed yet, you can find on our homepage several ways to
contribute, such as translating or doing a small Paypal donation to
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] . Thanks for your support.
2) if not done yet, a detailed description of your problem before
using Boot-Repair
3) the BootInfo (URL or text file) that appeared after you used the
"Recommended Repair" of Boot-Repair
4) a detailed description of your problem after using Boot-Repair's
Recommended Repair.

[/I]Given the length of time they took to reply and the nature of their first question, I would not recommend their software[I].
[/I]

---

