---
title: "Signature Security Error in Apt-Get"
date: 2005-08-31
forum: General Help
---

### Post by firefly2442 on 2005-08-31
When I try to run apt-get I get this:

Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


Do I need a new sig key?  I ran apt-get update but it keeps telling me this. :???:

---

### Post by arnieboy on 2005-09-01
[QUOTE=firefly2442]When I try to run apt-get I get this:

Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


Do I need a new sig key?  I ran apt-get update but it keeps telling me this. :???:[/QUOTE]
just be patient.  its a temporay problem. will be fine tomorrow.

---

### Post by Ian Green on 2005-09-01
I am getting the exact same problem here (repeatedly) on a server that I had not previously updated. I run " apt-get update " and keep getting the PGP error BADSIG message suggesting I should run apt-get update to fix it. 

 W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

The signature is the same one you got, and I noticed, by Googling for it, that the same signature occurred with the identical message back in January, but as that thread was closed I couldn't reply to it, having just registered, so I searched and found this one.

I have earlier today successfully run apt-get and Synaptic Package Manager on other Ubuntu desktops/laptops, but they were already pretty up to date.

---

### Post by Lux Perpetua on 2005-09-06
[QUOTE=arnieboy]just be patient.  its a temporay problem. will be fine tomorrow.[/QUOTE]
"Tomorrow" has come and gone, and the problem still exists. I take it that this isn't too serious, but does anybody know what causes the problem? It isn't on the user's end, right?

---

### Post by arnieboy on 2005-09-06
[QUOTE=Lux Perpetua]"Tomorrow" has come and gone, and the problem still exists. I take it that this isn't too serious, but does anybody know what causes the problem? It isn't on the user's end, right?[/QUOTE]
please post the contents of /etc/apt/sources.list

---

### Post by Lux Perpetua on 2005-09-06
Here is /etc/apt/source.list:

> 
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


---

### Post by arnieboy on 2005-09-06
change all instances of [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) to [http://archive.ubuntu.com](http://archive.ubuntu.com)
double check to make sure u have changed all. save and exit. and do a:
```
sudo apt-get update
```

---

### Post by Lux Perpetua on 2005-09-06
[QUOTE=arnieboy]change all instances of [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) to [http://archive.ubuntu.com](http://archive.ubuntu.com)
double check to make sure u have changed all. save and exit. and do a:
```
sudo apt-get update
```[/QUOTE]
I still get: 

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

---

### Post by Ian Green on 2005-09-07
No problem here. This machine is fully up to date, and the source.list file is _simply_ as follows:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted



deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe

---

### Post by ektich on 2005-09-20
Sorry for cross-post, but I think it's better to answer eveywere were question has been asked:

try to clean /var/lib/apt/lists/partial and /var/lib/apt/lists (sudo rm /var/lib/apt/lists/partial/* and then sudo rm /var/lib/apt/lists/*), and then re-run apt-get update
That solved my problem.

---

### Post by basfrank on 2005-10-04
the second sudo command did'nt work for me.
it says deletition not possible.

---

### Post by ektich on 2005-10-04
[QUOTE=basfrank]the second sudo command did'nt work for me.
it says deletition not possible.[/QUOTE]

deletion of WHAT is not possible? It will fail to delete partial, because it's subdirectory, but it should delete any files that in there. on an 'ls /var/lib/apt/lists/' you should only see subdirectory 'partial'.

HAve you tried to do apt-get update after rm-ing files?.

---

### Post by basfrank on 2005-10-04
the full -german- text is:
root@Heinz2005:/home/bastian # sudo rm /var/lib/apt/lists/*
rm: [B]Entfernen von „/var/lib/apt/lists/partial“ nicht möglich: Ist ein Verzeichnis
rm: merkwürdige Datei (schreibgeschützt)[/B] „/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_Release“ entfernen? y
rm: **Entfernen von „/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_Release“ nicht möglich: Die Operation ist nicht erlaubt**

---

### Post by ektich on 2005-10-04
Can you do "ls -l /var/lib/apt/lists" and show us the output?

do you have Synaptic up and running then you're trying to delete that file?

---

### Post by basfrank on 2005-10-04
no i don't have s. up and running.
the output:

root@Heinz2005:/home/bastian # ls -l /var/lib/apt/lists
insgesamt 1743251436
drwxr-xr-x      2 root       root       4096 2005-10-04 12:18 partial
?-wxrw-rwt  52992 3486471509 3486449664    8 1970-01-01 01:00 security.ubuntu.com_ubuntu_dists_hoary-security_Release

---

### Post by ektich on 2005-10-04
[QUOTE=basfrank]no i don't have s. up and running.
the output:

root@Heinz2005:/home/bastian # ls -l /var/lib/apt/lists
insgesamt 1743251436
drwxr-xr-x      2 root       root       4096 2005-10-04 12:18 partial
?-wxrw-rwt  52992 3486471509 3486449664    8 1970-01-01 01:00 security.ubuntu.com_ubuntu_dists_hoary-security_Release[/QUOTE]

that doesn't look right at all! permissions, size, date - all wrong.
I suggest you boot into rescue mode (you should have an option in the Grub boot menu), and try to fsck your root partition. what's your /etc/fstab? which disk is mounted as '/' ?

---

### Post by basfrank on 2005-10-04
the system runs stable. the only thing is i can't update or install or deinstall.
i tried to install ooo2 and instead of updating i have now two ooos running.
this causes errors. i can't even deinstall ooo or ooo2.
i get this gpg error for two days now and it's really annoying cause the german forum can't help either.

fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

---

### Post by ektich on 2005-10-04
[QUOTE=basfrank]the system runs stable. the only thing is i can't update or install or deinstall.
i tried to install ooo2 and instead of updating i have now two ooos running.
this causes errors. i can't even deinstall ooo or ooo2.
i get this gpg error for two days now and it's really annoying cause the german forum can't help either.[/QUOTE]

Well, as I said: everything is wrong about that file. That's why apt-get won't work. I strongly reccomend to try and get rid of that file. Something happend on the file system. fsck might be able to correct it (that's what fsck is for), but fsck can screw the system if not used properly. I need to know the name of the device (/dev/hda1 ?) of that file to be able to send you exactly how to run fsck. 

Another possibility is to do "rm -rf /var/lib/apt/lists" and, if sucsessful, do "mkdir /var/lib/apt/lists" and run apt-get update.

---

### Post by basfrank on 2005-10-04
not sucessful. how do i get the information you want? which file do you mean?
you know, as i'm not an expert it's a little fast for me to follow.
sorry 'bout that.

---

### Post by ektich on 2005-10-04
[QUOTE=basfrank]the system runs stable. the only thing is i can't update or install or deinstall.
i tried to install ooo2 and instead of updating i have now two ooos running.
this causes errors. i can't even deinstall ooo or ooo2.
i get this gpg error for two days now and it's really annoying cause the german forum can't help either.

fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0[/QUOTE]

I'm sorry, I rushed to answer and didn't noticed your fstab. 
Your root device is /dev/hda1 (first partition on the first hard drive).

You have to reboot into "rescue" mode (to minimize disk usage). You should see it in the grub boot menu. 
then, from the command prompt, you should execute "fsck -C -r /dev/hda1" and try to repair any errors it reports (if it reports any errors).

If that fails for some reason, you will have to boot from LiveCD (if you have one) and try to do the same (fsck -C -r /dev/hda1).

Hope this helps. It won't hurt to backup any data you have in your home directory, if possible.

---

### Post by basfrank on 2005-10-04
thanks for your advice man.
i'll try my luck.
laters

---

### Post by basfrank on 2005-10-04
fsck said everything's fine

---

### Post by ektich on 2005-10-04
[QUOTE=basfrank]fsck said everything's fine[/QUOTE]

And ls -l in the directory still shows weird things?

can you go into that directory and do "chown root:root security.ubuntu.com_ubuntu_dists_hoary-security_Release" followed by "chmod 644 security.ubuntu.com_ubuntu_dists_hoary-security_Release
"
Then do ls -l and if that fixes permissions and ownership (owned by root:root, persmissions -rw-r--r--) you will be able to rm that file. If not - I would suggest reinstallation.

---

### Post by basfrank on 2005-10-04
root@Heinz2005:/var/lib/apt/lists # ls -l
insgesamt 1743251432
?-wxrw-rwt  52992 3486471509 3486449664 8 1970-01-01 01:00 security.ubuntu.com_ubuntu_dists_hoary-security_Release

---

### Post by basfrank on 2005-10-04
i cannot change attributes of this file. there's always: this operation is not allowed.
whats strange is that this file is called "strange file": **merkwürdige Datei** (schreibgeschützt) „security.ubuntu.com_ubuntu_dists_hoary-security_Release“

---

### Post by smurfix on 2005-10-04
[QUOTE=basfrank]fsck said everything's fine[/QUOTE]

If the system thinks the file system is OK, it'll set a flag in the superblock so that "normal" fsck will skip it (otherwise you'll be waiting a long time after each reboot).

fsck -fy /dev/hda1-or-whatever

(Yes I know, -y is dangerous, but let's face it -- you'll answer every question it asks with "y" anyway.)

---

### Post by smurfix on 2005-10-04
[QUOTE=ektich]
Another possibility is to do "rm -rf /var/lib/apt/lists" and, if sucsessful, do "mkdir /var/lib/apt/lists" and run apt-get update.[/QUOTE]

Personally I'd advise against doing that. The most likely result is a file system that's even more screwed up. Besides, if the file (inode, actually) is too broken to be removed, you won't be able to get rid of it by removing every **other** file in that directory either. :( 

One stopgap fix is to move the thing to another directory, or just to rename it to "this_is_a_broken_file". However, that won't fix the problem, just the immediate effects.

---

### Post by ektich on 2005-10-04
[QUOTE=smurfix]If the system thinks the file system is OK, it'll set a flag in the superblock so that "normal" fsck will skip it (otherwise you'll be waiting a long time after each reboot).
fsck -fy /dev/hda1-or-whatever
(Yes I know, -y is dangerous, but let's face it -- you'll answer every question it asks with "y" anyway.)[/QUOTE]

Ah, yes, I forgot -f flag :( basfrank: you will have to re-execute fsck with -f option, and see if that says anything.

smurfix: I was hoping by deleting directory it will delete skrewed file as well. I don't think it's "skrewed inode" issue, it more looks like "table-of-content". Although I'm not familiar with ext3 on such a low level. 

Renaming it sounds like something worth trying, but I will be surprised if renaming will actualy work. :(

To be honest with you guys - I ran out of ideas...

---

### Post by basfrank on 2005-10-04
thanks for your help ektich. i solved it with fsck -f. works fine now.

---

### Post by flyingman on 2005-10-14
[QUOTE=ektich]Sorry for cross-post, but I think it's better to answer eveywere were question has been asked:

try to clean /var/lib/apt/lists/partial and /var/lib/apt/lists (sudo rm /var/lib/apt/lists/partial/* and then sudo rm /var/lib/apt/lists/*), and then re-run apt-get update
That solved my problem.[/QUOTE]

Hi! I tried that. Now I just get this error:

W: Couldn't stat source package list [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/no.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/no.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/no.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/no.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/no.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/no.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/no.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/no.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/no.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/no.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)


BTW, I put a -r after rm because I got an error using only *. Have I deleted something I shouldn't have? 
Is there a way to get those files back there?

what should I do?

---

### Post by skyboy on 2005-10-16
had the same problem. that fixed it too:
> Sorry for cross-post, but I think it's better to answer eveywere were question has been asked:
 
 try to clean /var/lib/apt/lists/partial and /var/lib/apt/lists (sudo rm /var/lib/apt/lists/partial/* and then sudo rm /var/lib/apt/lists/*), and then re-run apt-get update
 That solved my problem.
thanks

---

