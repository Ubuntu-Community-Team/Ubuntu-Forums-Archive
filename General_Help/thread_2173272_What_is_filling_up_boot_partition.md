---
title: "What is filling up boot partition?"
date: 2013-09-08
forum: General Help
---

### Post by VirginiaDrifter on 2013-09-08
After my last update, it was showing my boot partition full. I have searched and ran all the commands I can find about removing old kernels and they seem to  have worked (I'm now at only 89% full). My problem is there seems to be some files hiding somewhere that I need to delete, but I can't find them.
 
My system monitor shows I'm using 246.1MB

But properties in the /boot folder only shows 29.7MB. being used.

Can someone please tell me what I need to do to clean up my boot. Thanks a lot in advance.
 
Ron

---

### Post by Bashing-om on 2013-09-08
VirginiaDrifter' Hi !

To see all files contained in "/boot"; terminal command:
```
ls -la /boot
```
The following command is useful for finding out which directories are using all your space...
```
 du -h --max-depth=1 | sort -hr
```

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by VirginiaDrifter on 2013-09-08
Here is what I get from my boot:

 ronnie@Ubuntu2:~$ ls -la /boot[COLOR=#ff0000]**total 24035**[/COLOR]
drwxr-xr-x  5 root root     5120 Sep  7 14:31 .
drwxr-xr-x 23 root root     4096 Sep  7 14:31 ..
-rw-r--r--  1 root root   861648 Aug 24 02:21 abi-3.5.0-40-generic
-rw-r--r--  1 root root   154713 Aug 24 02:21 config-3.5.0-40-generic
drwxr-xr-x  3 root root     7168 Sep  9 08:02 grub
-rw-r--r--  1 root root 15547026 Sep  7 12:06 initrd.img-3.5.0-40-generic
drwx------  2 root root    12288 Mar 18 09:49 lost+found
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2421348 Aug 24 02:21 System.map-3.5.0-40-generic
drwx------  4 root root     1024 Mar 18 11:52 .Trash-0
-rw-------  1 root root  5236048 Aug 24 02:21 vmlinuz-3.5.0-40-generic
ronnie@Ubuntu2:~$ 


Can you see anything that I can delete from here? Thanks again.

How do you all post your terminal outputs on here? I used copy and paste, but I don't think that's the right way.

---

### Post by deadflowr on 2013-09-08
What's in the Trash-0 directory?

---

### Post by Bashing-om on 2013-09-08
VirginiaDrifter;
+1 on deadflowr's question .. I too jumped to that also.
And also take a look in " lost+found" directory ... make sure there is nothing in there needed and one may delete that directory. That directory generally hold bits and pieces that the "fsck" utility did not or could not clean up that you might have a requirement to reclaim.

As to copy and paste for input to the forum...in the tool bars at the top of the post is "#" ..(wrap code text) .. a number of ways one can do this,
click on "#" and then generally one can right click with the mouse and choose paste .. to paste the contents of the clipboard (from copy - right click).

To do so manually type the phrase "[code]" , insert your text, and then finish with that phrase putting a forward slash before the "c".

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by VirginiaDrifter on 2013-09-09
OK, there is a lot of stuff in the trash-O file,

```
ronnie@Ubuntu2:~$ sudo ls -la /boot/.Trash-0[sudo] password for ronnie: 
total 13
drwx------ 4 root root 1024 Mar 18 11:52 .
drwxr-xr-x 5 root root 5120 Sep  7 14:31 ..
drwx------ 2 root root 3072 Sep  7 13:46 files
drwx------ 2 root root 4096 Sep  7 13:46 info
ronnie@Ubuntu2:~$
```

Lost+found folder is empty.

I think the Trash-0 file is the one because it has a lot of the files I deleted before. Can you give me a good way to delete the ones I don't need or can I just delete them all?

Again, Thanks!!

---

### Post by VirginiaDrifter on 2013-09-09
Sorry, guess this is what you wanted:

```
ronnie@Ubuntu2:~$ sudo ls -la /boot/.Trash-0/filestotal 212612
drwx------ 2 root   root       3072 Sep  7 13:46 .
drwx------ 4 root   root       1024 Mar 18 11:52 ..
-rw-r--r-- 1 root   root     858541 Mar 12 06:41 abi-3.5.0-26-generic
-rw-r--r-- 1 root   root     860818 Mar 27 03:58 abi-3.5.0-27-generic
-rw-r--r-- 1 root   root     860943 Apr 25 06:08 abi-3.5.0-28-generic
-rw-r--r-- 1 root   root     860943 May 15 17:12 abi-3.5.0-30-generic
-rw-r--r-- 1 root   root     860983 May 17 23:52 abi-3.5.0-31-generic
-rw-r--r-- 1 root   root     860983 May 30 04:57 abi-3.5.0-32-generic
-rw-r--r-- 1 root   root     861067 Jun  8 00:53 abi-3.5.0-34-generic
-rw-r--r-- 1 root   root     860873 Jun 20 23:44 abi-3.5.0-36-generic
-rw-r--r-- 1 root   root     861363 Jul 11 02:13 abi-3.5.0-37-generic
-rw-r--r-- 1 root   root     154509 Mar 12 06:41 config-3.5.0-26-generic
-rw-r--r-- 1 root   root     154661 Mar 27 03:58 config-3.5.0-27-generic
-rw-r--r-- 1 root   root     154661 Apr 25 06:08 config-3.5.0-28-generic
-rw-r--r-- 1 root   root     154661 May 15 17:12 config-3.5.0-30-generic
-rw-r--r-- 1 root   root     154698 May 17 23:52 config-3.5.0-31-generic
-rw-r--r-- 1 root   root     154698 May 30 04:57 config-3.5.0-32-generic
-rw-r--r-- 1 root   root     154698 Jun  8 00:53 config-3.5.0-34-generic
-rw-r--r-- 1 root   root     154698 Jun 20 23:44 config-3.5.0-36-generic
-rw-r--r-- 1 root   root     154713 Jul 11 02:13 config-3.5.0-37-generic
-rw-r--r-- 1 root   root   15446530 Mar 29 07:29 initrd.img-3.5.0-26-generic
-rw-r--r-- 1 root   root   15481745 Apr 11 07:58 initrd.img-3.5.0-27-generic
-rw-r--r-- 1 root   root   15483913 May  3 09:05 initrd.img-3.5.0-28-generic
-rw-r--r-- 1 root   root   15483650 May 17 15:54 initrd.img-3.5.0-30-generic
-rw-r--r-- 1 root   root   15483970 May 27 09:43 initrd.img-3.5.0-31-generic
-rw-r--r-- 1 root   root   15483706 May 31 09:49 initrd.img-3.5.0-32-generic
-rw-r--r-- 1 root   root   15484470 Jun 17 07:55 initrd.img-3.5.0-34-generic
-rw-r--r-- 1 root   root   15485293 Jul  8 09:19 initrd.img-3.5.0-36-generic
-rw-r--r-- 1 root   root   15542639 Aug 22 14:29 initrd.img-3.5.0-37-generic
-rwxrwxrwx 1 ronnie ronnie   321548 Feb 14  2013 rons.png
-rw------- 1 root   root    2417136 Mar 12 06:41 System.map-3.5.0-26-generic
-rw------- 1 root   root    2418535 Mar 27 03:58 System.map-3.5.0-27-generic
-rw------- 1 root   root    2419138 Apr 25 06:08 System.map-3.5.0-28-generic
-rw------- 1 root   root    2419138 May 15 17:12 System.map-3.5.0-30-generic
-rw------- 1 root   root    2419134 May 17 23:52 System.map-3.5.0-31-generic
-rw------- 1 root   root    2419134 May 30 04:57 System.map-3.5.0-32-generic
-rw------- 1 root   root    2419656 Jun  8 00:53 System.map-3.5.0-34-generic
-rw------- 1 root   root    2419775 Jun 20 23:44 System.map-3.5.0-36-generic
-rw------- 1 root   root    2420011 Jul 11 02:13 System.map-3.5.0-37-generic
-rw------- 1 root   root    5227184 Mar 12 06:41 vmlinuz-3.5.0-26-generic
-rw------- 1 root   root    5229872 Mar 27 03:58 vmlinuz-3.5.0-27-generic
-rw------- 1 root   root    5231440 Apr 25 06:08 vmlinuz-3.5.0-28-generic
-rw------- 1 root   root    5231440 May 15 17:12 vmlinuz-3.5.0-30-generic
-rw------- 1 root   root    5230128 May 17 23:52 vmlinuz-3.5.0-31-generic
-rw------- 1 root   root    5230128 May 30 04:57 vmlinuz-3.5.0-32-generic
-rw------- 1 root   root    5231600 Jun  8 00:53 vmlinuz-3.5.0-34-generic
-rw------- 1 root   root    5233296 Jun 20 23:44 vmlinuz-3.5.0-36-generic
-rw------- 1 root   root    5231920 Jul 11 02:13 vmlinuz-3.5.0-37-generic
ronnie@Ubuntu2:~$ sudo ls -la /boot/.Trash-0/info
total 51
drwx------ 2 root root 4096 Sep  7 13:46 .
drwx------ 4 root root 1024 Mar 18 11:52 ..
-rw-r--r-- 1 root root   72 Sep  7 13:44 abi-3.5.0-26-generic.trashinfo
-rw-r--r-- 1 root root   72 Sep  7 13:44 abi-3.5.0-27-generic.trashinfo
-rw-r--r-- 1 root root   72 Sep  7 13:44 abi-3.5.0-28-generic.trashinfo
-rw-r--r-- 1 root root   72 Sep  7 13:44 abi-3.5.0-30-generic.trashinfo
-rw-r--r-- 1 root root   72 Sep  7 13:44 abi-3.5.0-31-generic.trashinfo
-rw-r--r-- 1 root root   72 Sep  7 13:44 abi-3.5.0-32-generic.trashinfo
-rw-r--r-- 1 root root   72 Sep  7 13:44 abi-3.5.0-34-generic.trashinfo
-rw-r--r-- 1 root root   72 Sep  7 13:44 abi-3.5.0-36-generic.trashinfo
-rw-r--r-- 1 root root   72 Sep  7 13:44 abi-3.5.0-37-generic.trashinfo
-rw-r--r-- 1 root root   75 Sep  7 13:45 config-3.5.0-26-generic.trashinfo
-rw-r--r-- 1 root root   75 Sep  7 13:45 config-3.5.0-27-generic.trashinfo
-rw-r--r-- 1 root root   75 Sep  7 13:45 config-3.5.0-28-generic.trashinfo
-rw-r--r-- 1 root root   75 Sep  7 13:45 config-3.5.0-30-generic.trashinfo
-rw-r--r-- 1 root root   75 Sep  7 13:45 config-3.5.0-31-generic.trashinfo
-rw-r--r-- 1 root root   75 Sep  7 13:45 config-3.5.0-32-generic.trashinfo
-rw-r--r-- 1 root root   75 Sep  7 13:45 config-3.5.0-34-generic.trashinfo
-rw-r--r-- 1 root root   75 Sep  7 13:45 config-3.5.0-36-generic.trashinfo
-rw-r--r-- 1 root root   75 Sep  7 13:45 config-3.5.0-37-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:45 initrd.img-3.5.0-26-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:45 initrd.img-3.5.0-27-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:45 initrd.img-3.5.0-28-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:45 initrd.img-3.5.0-30-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:45 initrd.img-3.5.0-31-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:45 initrd.img-3.5.0-32-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:45 initrd.img-3.5.0-34-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:45 initrd.img-3.5.0-36-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:45 initrd.img-3.5.0-37-generic.trashinfo
-rw-r--r-- 1 root root   65 Mar 18 11:52 rons.png.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:46 System.map-3.5.0-26-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:46 System.map-3.5.0-27-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:46 System.map-3.5.0-28-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:46 System.map-3.5.0-30-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:46 System.map-3.5.0-31-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:46 System.map-3.5.0-32-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:46 System.map-3.5.0-34-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:46 System.map-3.5.0-36-generic.trashinfo
-rw-r--r-- 1 root root   79 Sep  7 13:46 System.map-3.5.0-37-generic.trashinfo
-rw-r--r-- 1 root root   76 Sep  7 13:46 vmlinuz-3.5.0-26-generic.trashinfo
-rw-r--r-- 1 root root   76 Sep  7 13:46 vmlinuz-3.5.0-27-generic.trashinfo
-rw-r--r-- 1 root root   76 Sep  7 13:46 vmlinuz-3.5.0-28-generic.trashinfo
-rw-r--r-- 1 root root   76 Sep  7 13:46 vmlinuz-3.5.0-30-generic.trashinfo
-rw-r--r-- 1 root root   76 Sep  7 13:46 vmlinuz-3.5.0-31-generic.trashinfo
-rw-r--r-- 1 root root   76 Sep  7 13:46 vmlinuz-3.5.0-32-generic.trashinfo
-rw-r--r-- 1 root root   76 Sep  7 13:46 vmlinuz-3.5.0-34-generic.trashinfo
-rw-r--r-- 1 root root   76 Sep  7 13:46 vmlinuz-3.5.0-36-generic.trashinfo
-rw-r--r-- 1 root root   76 Sep  7 13:46 vmlinuz-3.5.0-37-generic.trashinfo
ronnie@Ubuntu2:~$
```

---

### Post by deadflowr on 2013-09-09
```
sudo rm -rf /boot/.Trash-0/files/*
```

Should clear all the files from the files folder.
Replacing files with info will do the same there.

---

### Post by Elfy on 2013-09-09
Next time you want to remove kernels - try uninstalling them instead

---

### Post by Impavidus on 2013-09-09
+1 to Elfy

Your package manager probably still thinks the old kernels are installed, although broken. If they are still reported as installed, uninstall them. You may also have some linux-headers packages belonging to old kernels, you can clean these up too.

---

### Post by VirginiaDrifter on 2013-09-09
> **deadflowr said:**
> ```
sudo rm -rf /boot/.Trash-0/files/*
```

Should clear all the files from the files folder.
Replacing files with info will do the same there.

Tried this command but the files are still there. What did I do wrong? Thanks for your all's patience with me. ;)

---

### Post by Bashing-om on 2013-09-09
VirginiaDrifter; Hi !
The command "sudo rm -rf /boot/.Trash-0/files/*" appears valid to me ..did you copy and paste that command - to preclude typos ??
Remember linux is always case sensitive such that "T" does not equal "t", and that "." is required for that directory name.

[INDENT][INDENT]it's a thought
[/INDENT][/INDENT]

---

### Post by VirginiaDrifter on 2013-09-09
Hi,
Yea I copy and pasted. I just now tried it again with no results. Here is what I'm getting, is it supposed to show files getting deleted? Because it's not.

```
ronnie@Ubuntu2:~$ sudo rm -rf /boot/.Trash-0/files/*[sudo] password for ronnie: 
ronnie@Ubuntu2:~$ 
```

Seems nothing ever works for me :mad:

---

### Post by Bashing-om on 2013-09-09
VirginiaDrifter; UUhhh..
Take a look and I bet you will see those directories and files are history.
On the command line, in executing a command successfully there is no response. The system just does what you tell it to do .. a response is a bad thing in that the system is advising you on why it could not comply or that there was a problem doing so.
Linux assumes that you know what you are doing ... and just does as told to do.

Now if you want it to tell you what it is doing .. and be interactive .. there are options one may add to a command, as in the "V" for verbose output, or "i/I" for interactive - ask before doing.
see:
```

man rm

```

[INDENT][INDENT]now if I could just get my dogs (and children) to do that
[/INDENT][/INDENT]

---

### Post by VirginiaDrifter on 2013-09-09
Just now checked and they're still there. and I'm still showing 89% usage for boot.

---

### Post by Bashing-om on 2013-09-09
VirginiaDrifter; Humm ...I am flabbergasted..

Ok what results:
```

cd /boot/.Trash-0/files/
ls -la

```

[INDENT][INDENT]this could get interesting
[/INDENT][/INDENT]

---

### Post by VirginiaDrifter on 2013-09-09
```
ronnie@Ubuntu2:~$ cd /boot/.Trash-0/files/bash: cd: /boot/.Trash-0/files/: Permission denied
ronnie@Ubuntu2:~$ cd /boot/.Trash-0/files/
bash: cd: /boot/.Trash-0/files/: Permission denied
ronnie@Ubuntu2:~$ ls -la 
```

---

### Post by Bashing-om on 2013-09-09
VirginiaDrifter; sheesshh 
OK
```

sudo cd /boot/.Trash-0/files/
ls -la

```
surely then we can at lest look at them (ls) !
This might be a 1st for me to make dpkg remove those files in a non-standard directory ??

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by deadflowr on 2013-09-09
You might try running sudo interactively, to keep you in root so you don't have keep adding sudo to everything
```
sudo -i
```
Which will place you in root, simply typing exit will leave root.
Buyer beware though
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Several questions though, if you replace the * with an actual filename, like abi.3.5.iforgettherest, does it delete the file?
Also, to follow up in a way to what Elfy stated, how did you remove the old kernels? I know it's a day late, but...

---

### Post by VirginiaDrifter on 2013-09-09
> **Bashing-om said:**
> VirginiaDrifter; sheesshh 
OK
```

sudo cd /boot/.Trash-0/files/
ls -la

```
surely then we can at lest look at them (ls) !
This might be a 1st for me to make dpkg remove those files in a non-standard directory ??
[INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]


```
ronnie@Ubuntu2:~$ sudo cd /boot/.Trash-0/files/[sudo] password for ronnie: 
Sorry, try again.
[sudo] password for ronnie: 
sudo: cd: command not found
ronnie@Ubuntu2:~$ 



```

> **deadflowr said:**
> You might try running sudo interactively, to keep you in root so you don't have keep adding sudo to everything
```
sudo -i
```
Which will place you in root, simply typing exit will leave root.
Buyer beware though
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Several questions though, if you replace the * with an actual filename, like abi.3.5.iforgettherest, does it delete the file?
Also, to follow up in a way to what Elfy stated, how did you remove the old kernels? I know it's a day late, but...

Ok thanks for the tip on root :). As far as how I deleted them, I guess I messed up. I just went into the /boot folder and deleted (right click/delete) the old kernals one by one except the one I'm using now. Give me a couple of minutes and let me see if I can delete 1 file as you suggested.

And I thought I was starting to get the hang of Linux..... Yea,.....Right.:confused:

---

### Post by VirginiaDrifter on 2013-09-09
> **deadflowr said:**
> 
Several questions though,** if you replace the * with an actual filename, like abi.3.5.iforgettherest, does it delete the file?**
Also, to follow up in a way to what Elfy stated, how did you remove the old kernels? I know it's a day late, but...

[SIZE=4][B]Bingo,
[/B][/SIZE]
I just now deleted 3 files like this  \\:D/ , so at least we're getting somewhere now. OK, so now that we know the '*' is the culprit, any suggestions on what to try next? Do I need to delete them 1 by 1?, or is there something besides the '*' to try?

---

### Post by Bashing-om on 2013-09-09
VirginiaDrifter; Hey,
I still fail to understand why you can not cd to the target directory.. How about trying to get to that target in steps and see where it fails ?
```

cd /boot
cd .Trash

```
And the command "cd" alone takes you back to your home directory.

[INDENT][INDENT]has got interesting
[/INDENT][/INDENT]

---

### Post by VirginiaDrifter on 2013-09-09
```
ronnie@Ubuntu2:~$ cd /bootronnie@Ubuntu2:/boot$ cd .Trash
bash: cd: .Trash: No such file or directory
ronnie@Ubuntu2:/boot$ 
```

:confused:

---

### Post by VirginiaDrifter on 2013-09-09
```
ronnie@Ubuntu2:~$ sudo -i[sudo] password for ronnie: 
root@Ubuntu2:~# cd /boot
root@Ubuntu2:/boot# cd .Trash-0
root@Ubuntu2:/boot/.Trash-0# 
```

Forgot the sudo. Ok, now it seams like I'm into the trash, so what would be the command to delete.
This?

```
rm -rf /files/* 
```

---

### Post by Bashing-om on 2013-09-09
VirginiaDrifter;

My bad forgetting the '-0'...
Your last should work to remove the kernels , however, I am concerned about also purging the related config files to those kernels.
How about Changing Directory into the files directory and issuing a command similar to this for each image file ?
```

sudo apt-get --purge remove linux-image3.2.0-31-generic

``` change the version '3.2-31'string to what is present in that files directory ?
If apt-get sees these files will be a much cleaner method to remove them.
And need to confirm that there is no duplicate files in the "/boot" directory ... Do not want the only booting kernel removed !

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by VirginiaDrifter on 2013-09-09
OK, I will do that for each old kernel. 

And my problem all along seemed to be I wasn't in root.
I reverted back to my home directory while still in root and re-did the original command 

```
rm -rf /boot/.Trash-0/files/*
```

and it erased everything. I'm down to 13% on my boot partition now  :D.

I do have one last question though:
In the future, when I want to get rid of the old kernels, what are the proper steps I should be taking?

Thanks again for everybody's help, I really appreciate it !!

Ron

---

### Post by Bashing-om on 2013-09-09
VirginiaDrifter; Well.

For good or bad. there we are .. time will tell. 
As to how I remove the old no longer wanted kernels I use the command line with these terminal codes:
```

sudo apt-get --purge remove linux-image-3.2.0-31-generic
sudo apt-get --purge remove linux-headers-3.2.0-31-generic

``` for each kernel installed.
then:
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package with the following command.
```

dpkg -l | grep '^rc' | awk '{print $2}' | xargs dpkg --purge

```

There is a much more user friendly method to remove those kernels via synaptic. But, synaptic is no longer installed by default. 

[INDENT][INDENT]ubuntu, many ways to one end
[/INDENT][/INDENT]

---

### Post by 1clue on 2013-09-10
Is /boot mounted?  type **mount** and see if /boot is mentioned.

It's typical for some of the distros I use to unmount /boot after / is started.  Not sure which way Ubuntu is supposed to be because I mess with that sometimes.

Anyway I ran into this before, seeing files in the /boot directory but the file sizes not adding up to the size in the dialog box.  But **sudo mount /boot** will get you the correct files in there if it's not mounted already.

And if that's the problem, then once you get it cleared out again you could **sudo umount /boot** and then remove all the CONTENTS of /boot.  DANGER!  Don't just blindly do this, if you don't understand what's going on you could make your system unbootable!  If you're going to do this then make sure your system is USING the separate filesystem AND that there are files in the directory when the /boot partition is not mounted.

---

### Post by deadflowr on 2013-09-10
For removing old kernels and other unwanted packages, I almost always use synaptic.
As Bashing-Om pointed out you look for both linux-image and linux-headers.
With synaptic, I go to status>installed and then search the package name.
I then get the list of installed linux-image or headers and review them.
I like it also because it gives you one last chance to review the changes you are going to make before you make them.
It's always nice to double check(or even triple check) before going forward.

---

### Post by oldos2er on 2013-09-10
> **Bashing-om said:**
> VirginiaDrifter; sheesshh 
OK
```

sudo cd /boot/.Trash-0/files/
ls -la

```


When calling a shell command like *cd*, just sticking *sudo* in front of it won't work (see [here]("http://askubuntu.com/questions/20953/sudo-source-command-not-found") for an explanation). As deadflowr suggested, you need to run *sudo -i* first, then *cd foo*. Just FYI.

---

### Post by Bashing-om on 2013-09-10
@ oldos2er; Thanks for the instruction !

It is always amazing to me what I do not know about this wonderful operating system.

[INDENT][INDENT]still learning even after all these years
[/INDENT][/INDENT]

---

