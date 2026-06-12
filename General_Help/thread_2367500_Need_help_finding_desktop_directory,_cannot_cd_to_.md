---
title: "Need help finding desktop directory, cannot cd to user directory"
date: 2017-07-31
forum: General Help
---

### Post by neurotrauma on 2017-07-31
I am brand new to ubuntu so please bare with me, I literally just got this about 3 days ago so I'm very green.

I've got updatedb setup and I am able to locate my file but not sure how to point it to the directory

I've tried using cd to home then my username but it gives me the following issues:


```
root@NOEL-PC:/# locate "sample.php"
/mnt/c/Users/Administrator/Desktop/Downloads/bot/cryptopia-api-php-master/cryptopia-api-php-master/samp
root@NOEL-PC:~# cd /
root@NOEL-PC:/# ls -r
var  tmp  srv   run   proc  mnt    lost+found  lib   home  dev   cache  bin
usr  sys  sbin  root  opt   media  lib64       init  etc   data  boot   acct
root@NOEL-PC:/# cd home
root@NOEL-PC:/home# ls -r
Neuro
root@NOEL-PC:/home# cd /Neuro/
-bash: cd: /Neuro/: No such file or directory
root@NOEL-PC:/home# cd /neuro
-bash: cd: /neuro: No such file or directory
root@NOEL-PC:/home# cd /Neuro
-bash: cd: /Neuro: No such file or directory
```

how do I go about getting to this directory?

---

### Post by Habitual on 2017-07-31
> **neurotrauma said:**
> I am brand new to ubuntu so please bare with me, I literally just got this about 3 days ago so I'm very green.

I've got updatedb setup and I am able to locate my file but not sure how to point it to the directory

I've tried using cd to home then my username but it gives me the following issues:


root@NOEL-PC:/# locate "sample.php"
/mnt/c/Users/Administrator/Desktop/Downloads/bot/cryptopia-api-php-master/cryptopia-api-php-master/samp
root@NOEL-PC:~# cd /
root@NOEL-PC:/# ls -r
var  tmp  srv   run   proc  mnt    lost+found  lib   home  dev   cache  bin
usr  sys  sbin  root  opt   media  lib64       init  etc   data  boot   acct
root@NOEL-PC:/# cd home
root@NOEL-PC:/home# ls -r
Neuro
root@NOEL-PC:/home# cd /Neuro/
-bash: cd: /Neuro/: No such file or directory
root@NOEL-PC:/home# cd /neuro
-bash: cd: /neuro: No such file or directory
root@NOEL-PC:/home# cd /Neuro
-bash: cd: /Neuro: No such file or directory

how do I go about getting to this directory?
```
find . -name Neuro -type d
``` will help you locate it without "locate" or updatedb being necessary.

---

### Post by steeldriver on 2017-07-31
You need to understand the difference between an absolute and a relative path - see for example [Absolute and relative paths](https://en.wikipedia.org/wiki/Path_(computing)#Absolute_and_relative_paths)

In your case specifically if you are in directory /home and want to go to /home/Neuro then you can use

```

cd Neuro

```

(relative) or

```

cd /home/Neuro

```

(absolute) but NOT cd /Neuro (since that would be a directory called Neuro in the filesystem root directory, /)

---

### Post by springshades on 2017-07-31
Since you are new, a couple additional tips that you may find useful in the future.

First, simply typing "cd" and hitting enter will take you to your home by default. You don't have to type in the path to home or anything else.

Second, by default there is a variable called "HOME" which contains the path to your home directory. So if you have a file called "nachos.txt" on your desktop, you could use a command like:

```
cp $HOME/Desktop/nachos.txt .
```

Which would "copy" (the cp command) your file from your Desktop in your "home" (you access variables at the prompt by putting a dollar sign in front of them like $HOME) to your current directory (using a period is a shortcut which means "here").

---

### Post by oldos2er on 2017-07-31
> **springshades said:**
> First, simply typing "cd" and hitting enter will take you to your home by default. You don't have to type in the path to home or anything else.


True, but neurotrauma would need to exit out of their root shell first, or "cd" will simply take them to /root (root's home).

@neurotrauma see [http://linuxcommand.org/lc3_learning_the_shell.php](http://linuxcommand.org/lc3_learning_the_shell.php) for an excellent tutorial for learning the shell.

---

### Post by neurotrauma on 2017-08-05
Thank you that tutorial was helpful.

What I was looking for was not actually found in the home directory, but the mnt directory allowing me to access my drives. I have still not found my desktop through home, but by moving my file from desktop to C: i was able to locate it using mnt.

---

### Post by vocx on 2017-08-06
This is probably the most important advice for a new user:
> **steeldriver said:**
> You need to understand the difference between an absolute and a relative path - see for example [Absolute and relative paths]("https://en.wikipedia.org/wiki/Path_(computing)#Absolute_and_relative_paths")
In your case specifically if you are in directory /home and want to go to /home/Neuro then you can use
```

cd Neuro

```
(relative) or
```

cd /home/Neuro

```


> **neurotrauma said:**
> Thank you that tutorial was helpful.
What I was looking for was not actually found in the home directory, but the mnt directory allowing me to access my drives. I have still not found my desktop through home, but by moving my file from desktop to C: i was able to locate it using mnt.
It seems like you found the file that you wanted, however you are still not entirely sure how Linux works.

Upon looking at your first post again it seems like you are mounting your Windows partition in Linux, and searching files in that partition.

> **neurotrauma said:**
> I am brand new to ubuntu so please bare with me, I literally just got this about 3 days ago so I'm very green.
```

**root@NOEL-PC:/#** locate "sample.php"
/mnt/c/**Users/Administrator**/Desktop/Downloads/bot/cryptopia-api-php-master/cryptopia-api-php-master/samp

```
...


Please be extra careful in what you are doing. You are using the "root" account in Linux, and then you are accessing the files of the Administrator account in Windows. In Linux, the "root" account should not be used in every day usage, only when you need to do modifications to your system, such as installing or removing packages, or making small modifications to system configuration files. If you are following a guide to set up things, mount your other partitions, etc., I suggest you go back a few steps, and learn to use "sudo" properly in Ubuntu. The command "sudo" gives you temporary elevated privileges in the terminal to do system modifications, basically edit and delete files.

The problem with using "root" all the time is that if you make a small mistake, such as removing a file, or changing the permissions of a file, you may render a part of your system unusable. Moreover, you are operating on files of the Windows Administrator. This means that if you accidentally delete some files there, you may render Windows unusable as well.

My main concern is that you don't even know how to navigate the directories in Linux. So, if a guide asks you to remove a file, you need to know exactly where you currently are in the system, so you don't accidentally delete a file you did not want.
```

# Be very careful when running a remove command
rm file

```

---

### Post by Cavsfan on 2017-08-06
> **neurotrauma said:**
> Thank you that tutorial was helpful.

What I was looking for was not actually found in the home directory, but the mnt directory allowing me to access my drives. I have still not found my desktop through home, but by moving my file from desktop to C: i was able to locate it using mnt.

neurotrauma, another way to get to your home directory, guessing you have exited the root shell as [COLOR=#000000]oldos2er pointed out. 

```
cd ~/
```

You really do not want to be in a root shell often. Entering **sudo** before a command requiring root access is the proper thing to do.
Enter **gksudo** if it's to be used with anything graphical. If it says that is not installed, it will tell you what to do to install it.

Also you mention moving a file to C:, Windows does not like having other operating systems like Ubuntu writing to it. It can cause problems.
Trust me as one person that personally experienced that problem.

I mount my C: windows drive _read only_. First you have to make sure [/COLOR]**ntfs-3g** is installed.
This will show if it is:
```
cavsfan@cavsfan-Le-Beast:~$ apt-cache policy ntfs-3g
ntfs-3g:
  Installed: 1:2015.3.14AR.1-1ubuntu0.1
  Candidate: 1:2015.3.14AR.1-1ubuntu0.1
  Version table:
 *** 1:2015.3.14AR.1-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:2015.3.14AR.1-1build1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

If it shows not installed enter **sudo apt install ntfs-3g**

Then you would enter the command **sudo mkdir /media/windows** in terminal to create the mount point. This just needs to be done once.

Then you *could* enter **sudo mount -t ntfs-3g -o ro /dev/sda1 /media/windows**

That's if your windows directory is on the 1st partition of disk 1 (sda1). 
If it is on another drive replace /dev/sd**a1** with what the output of **sudo blkid** says:
```
cavsfan@cavsfan-Le-Beast:~$ sudo blkid
[sudo] password for cavsfan: 
[COLOR=#FF0000]/dev/sda1[/COLOR]: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" PARTUUID="a55f55ec-01"
/dev/sda2: LABEL="Arch-Linux" UUID="97ce09d6-b701-499e-b838-93762e3b005c" TYPE="ext4" PARTUUID="a55f55ec-02"
/dev/sda4: LABEL="Xenial" UUID="09320a63-c5e5-4e47-afab-dfa5f9a5d8dc" TYPE="ext4" PTTYPE="dos" PARTUUID="a55f55ec-04"
/dev/sda5: UUID="3e98ebb1-3a5e-46d2-9302-6e4a811e644b" TYPE="swap" PARTUUID="a55f55ec-05"
/dev/sda6: LABEL="Zesty" UUID="c1549566-ed28-48f2-a546-b8a5b39729d6" TYPE="ext4" PARTUUID="a55f55ec-06"
/dev/sda7: LABEL="Artful" UUID="1426326a-e0a8-4e19-86a2-0019148b3ac9" TYPE="ext4" PARTUUID="a55f55ec-07"
/dev/sdb1: LABEL="Fantom" UUID="B266B4B166B47825" TYPE="ntfs" PARTUUID="f87b4c9a-01"

```

Adding the labels to the partitions is explained in section 1.2 of the wiki in the green link in my signature.

But, instead of typing that command and having to remember it, just enter an alias for it in .bashrc which can be edited with any text editor: gedit, mousepad, etc.
The period indicates that it is a hidden file.

Put this in the .bashrc file: (# means that line is a comment)
> #Mount C: drive
alias mountc='sudo mount -t ntfs-3g -o ro /dev/sda1 /media/windows'

#Unmount C: drive
alias umountc='sudo umount /dev/sda1'

Then enter mountc and enter the root password to mount it and umountc to unmount it.

I use a USB drive to write to from either Windows or Linux systems.

Welcome to the forum. There are many knowledgeable people here that can help you solve pretty much any problem you may encounter.
Just be sure and see if you can google the answer first to save time.

Cheers

---

