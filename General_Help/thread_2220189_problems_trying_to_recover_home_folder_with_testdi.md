---
title: "problems trying to recover home folder with testdisk"
date: 2014-04-27
forum: General Help
---

### Post by rizos on 2014-04-27
i have a dual boot win7/ubuntu 12.04 

partition table got messed up when i reinstall fresh 12.04 on "a" / partition but forgot to acivate home partition "c", now win it's ok and ubuntu installation start as fresh, but my home folder is gone with all my files.


i used testdisk to rewrite the partition table with no avail.

this is how it looks my partition table running testdisk

```


Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63

     Partition               Start        End    Size in sectors

 * HPFS - NTFS              0  32 33    12 223 19     204800 [System Reserved]
 P HPFS - NTFS             12 223 20 29095  42 52  467207025
 P Linux                29095  61 23 31007 120 25   30720000
 L HPFS - NTFS          31007 152 58 31645   2 37   10240000
>[COLOR=#ff0000]L Linux                31645  35  7 60801  47 46  468391936[/COLOR] <--- here is my home folder


```

the red last line holds all my files from both accounts guests and admin in ubuntu, and they are list there, but i been trying to rewrite the partition table but is not working, gparted shows 500gb unallocated when clearly 250 belongs to win partition.

my files are there i can see my home folder but cant recover the partition table.


can any one help, i would appreciate this.


thanx


R.

---

### Post by ajgreeny on 2014-04-27
You may not need testdisk at all; I think you may simply need to edit /etc/fstab in your Ubuntu installation, assuming, of course, that you have not overwritten the old /home partition when you reinstalled, and that it is still a good partition.

From a live ubuntu system can you show us the output of ```
sudo fdisk -l
sudo blkid -c /dev/null
``` and tell us which partition is your old /home.  We can then give you details of the edit to make, but it will look something like
```
# /home was on /dev/sda4 during installation
UUID=2a1a9b57-4d0a-4570-974f-d6114fb25ef1 /home           ext4    defaults        0       2
``` with the UUID found from the blkid command you just made.

After editing and saving fstab, run command ```
sudo mount -a
``` and if there is no error shown all should be OK at next boot.

If you have really messed up your partitions and do have to resort to testdisk I can not help as I have (so far, thank goodness) never needed to recover a partition.

---

### Post by rizos on 2014-04-27
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1e7edf66

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   467413872   233603512+   7  HPFS/NTFS/exFAT
/dev/sda3       467415040   498135039    15360000   83  Linux
/dev/sda4       498135078   976784129   239324526    f  W95 Ext'd (LBA)
/dev/sda5       498137088   508377087     5120000   82  Linux swap / Solaris
/dev/sda6       508379136   976771071   234195968   83  Linux

Disk /dev/sdb: 15.5 GB, 15479597056 bytes
255 heads, 63 sectors/track, 1881 cylinders, total 30233588 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x65796c5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    30232575    15115264    b  W95 FAT32


```
```

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="System Reserved" UUID="6A7ACF807ACF4811" TYPE="ntfs" 
/dev/sda2: UUID="38A6D1F9A6D1B798" TYPE="ntfs" 
/dev/sda3: UUID="6a1b491f-bbd0-4bd4-8c21-f761af3795d8" TYPE="ext4" 
/dev/sda6: UUID="bdffe4ca-caf0-4a89-90c0-86be4c6e28ac" TYPE="ext4" 
/dev/sdb1: UUID="0D9E-46B7" TYPE="vfat" 

```

this is the home partition /dev/sda6: UUID="bdffe4ca-caf0-4a89-90c0-86be4c6e28ac" TYPE="ext4"

sda 4 is unallocated space.

---

### Post by ajgreeny on 2014-04-27
OK.  Edit /etc/fstab as root with ```
gksudo gedit /etc/fstab
``` and add the following lines to it at the bottom.
```
# /home on /dev/sda6 after installation
UUID=bdffe4ca-caf0-4a89-90c0-86be4c6e28ac /home           ext4    defaults        0       2
```
Now run ```
sudo mount -a
``` and report back any error messages you see

Incidentally, sda4 is not unallocated space but is an extended partition, a sort of container space, which actually contains the logical partitions sda5 and sda6.

---

### Post by rizos on 2014-04-28
wicked!...


have 2 accounts admin and guest account, guest account and all files is back!!... awsome.


now, every time im trying to login into admin account i can't, keeps in loop on the login page.


one thing i notice is that the old admin account name is chkuly and the new one in chkly.


i delete the new account chkly and created a new account from guest account names chkuly, but the problem still persist, cant log in into the admin account, what can be the issue?.


tahnx.


R

---

### Post by ajgreeny on 2014-04-28
If I use command groups in terminal I get the following output
```
*ajgreeny* **adm** lp cdrom **sudo** audio dip plugdev fuse lpadmin netdev sambashare vboxusers usb
```
See what you get if you log in as your user, if you still can, that is; I am a bit confused by your description of usernames etc etc.
Did you think the username you made in this reinstall was the same as previously used, and if so did you just make a typo error?
Do you have a user who can use sudo to carry out admin actions or has that possibility now gone? If so you may need to use command in recovery mode ```
mount -o rw,remount /
``` to mount the file system as read/write and then```
adduser *username* sudo
``` and also perhaps ```
adduser *username* adm
```using your current username, whatever that is instead of the word ***username*** to add you to the sudo group and make you an admin user for a start, but if your username has changed we may also need to change ownership of all those old /home files and folders.

Let's go one step at a time, so do what I've said here and come back again if needed with any problems/error messages that you see.

---

### Post by rizos on 2014-04-28
***Did you think the username you made in this reinstall was the same as previously used, and if so did you just make a typo error?*** yes, there is a typo issue on this account.


***Do you have a user who can use sudo to carry out admin actions or has that possibility now gone?*** i created a new admin account with sudo power.

the output of the code, bring this:

 
```


mount -o rw,remount /

The user `chkuly' is already a member of `sudo'.


```
 
and the code, also brings 

```


adduser username adm

The user `chkuly' is already a member of `sudo'.



```


 i can't login as admin user, (i just have 2 accounts admin and guests, guest account is back with all it's files on it and working fine, but admin account "chkuly" isnt, everytime i put my passwrod the login page fades out and come back to login page and cant get into my account, i created another account meanwhile with administrative  permits so i can go on sudo. 

account "ad" this works fine and as expected but my files from chkuly home folder are not there.

 now i cant really get into my account, please tell me what can i do to recover that account, or change the file to the new account.

i hope im clear enough on my explination, please let me not if not.


thanx,


R

---

### Post by ajgreeny on 2014-04-29
What is the full pathway to all those /home files and folders that you can not get into when as user chkuly?  They should be in **/home/chkuly** but I am wondering if they are now in **/home/chkly** because of the typo you made when you installed.

Whatever is the case, and assuming you are not locked out of user chkuly for some other reason (have you used sudo for a GUI application ever? That can cause this problem sometimes) it should be possible to copy all those old files and folders back into chkuly's home and make sure they are all owned by that user with the use of a simple chown command.

---

### Post by rizos on 2014-04-30
there is no path to the home folder of chkuly, is gone but "guest account" files are all there, i can't in any way access the chkuly account from login page nor access any files or folders, while on login page after typing passwd keeps loading fade out and come back asking me my passwd again and again, apps like gparted wont work either when asking for my passwd on "chkuly" from admin account,  i created a third account ("ad") with sudo privileges as there is no way i can see any of my files or access them on chkuly account, they arent any where except when running testdisk i can see they are there on the parition plus guest account has all files back!.

best thing would be to move to ad (new account) all the files from chkuly account so i can replace the whole account, is this possible at all?.


  something went wrong and i cant access from the login page the chkuly account, but "ad" account is working with sudo privileges.


 also gparted shows 495 gb of unallocated space, this means no partition table or space between win and ubuntu...

 should i rewrite fstab file completely so it will reflect on gparted the partitions?

thanx for all your time.


R

---

### Post by ajgreeny on 2014-05-01
So what is the full pathway to all those files that you want to be in the /home of the current user?  What folder do they appear in when you look in nautilus?  Or if you can't see them, how do you know they are still there; is this only when using testdisk?  If so I am not going to be much help as I have never had to recover any lost files or folders.

Once I know where they are actually sitting, I can tell you how, if necessary, to make a new partition, then copy all those files to that partition, and then make that new partition your home.
At the moment I am totally confused over what you've done so far, what and where all those files really are, and what exactly you want the new admin user to be called.  A screenshot of gparted would be helpful with an indication from you of which partition is which, as far as you're aware.

---

### Post by rizos on 2014-05-01
the full path of the folder is /home/chkuly/Access-Your-Private-Data.desktop they are there, i log from a live cd and the files are all there!!.




here is a picture of gparted:


[ATTACH=CONFIG]252724[/ATTACH]

 as you can see shows unallocated space and i have win partirion and linux partitions, i dont know what to do, my blame for the confusion, i didnt got what you were asking straight, now i can tell that all files are there but can't log into the chkuly account.


by the full path you mean this path i send?... if not please tell me how to get it...


cheers!.


R

---

### Post by ajgreeny on 2014-05-01
OK, I am afraid I really don't think I can help you more than I have tried to do so far.  I have absolutely no experience of testdisk, but if it is able to find all your files I think the easiest way to recover them may be to use testdisk to put them on an external disk (if that's possible with testdisk) and reinstall ubuntu again on the disk.

Or you could try using testdisk to recover the old partition table, which I believe it can do, but once again I do not know how to do so, never having been in that position.

---

### Post by rizos on 2014-05-02
i manage to have all the old files in this path /tmp/ecryptfs.gxfGWg57, how can i copy this to a new partition and make this new partition my home folder?

 best thing to do so far cause i recovered all my files but dont have an external drive at the moment i can rely to pass all those files and do a new install.


also gparted shows no partitions at all but windoze is present as dual boot when restarting the system, should i configure fstab in orther to get gparted to recognize dual boot partitions?


thanx...

---

