---
title: "permission to make new folder"
date: 2020-09-17
forum: General Help
---

### Post by oneleded on 2020-09-17
i finally figured the question i need to ask;
my linux is on an 5.25 drive. i put it in my new computer. the LXTerminal still has the name of my old computer.
''Name@ Name-OptiPlex-GX270'' 
i was trying to right click on the desktop, create a new folder and i get; 

Error creating directory /home/Name/Desktop/  
New: Permission denied

I've never had the pleasure, of this Problem. so
How can i get my my dristo's on the 5.25 HDD, to recognize the newer computer?, maybe is the right question.
i dont know my Name, on this new computer.

---

### Post by oneleded on 2020-09-17
Never-mind;, after i posted this the 1st page i went to; [https://www.lifewire.com/create-directories-linux-mkdir-command-399184](https://www.lifewire.com/create-directories-linux-mkdir-command-399184) '
so that takes care of my permissions problems;
as far as ''Name@Name-OptiPlex-Gx270", i dont think it matters much.

---

### Post by TheFu on 2020-09-17
That link didn't work for me. "Page not found" error from the lifewire.com server. Probably best to seek answers from websites that have "ubuntu" in the domainname somewhere, if you aren't certain about the author.

You can boot from a "Try Ubuntu" desktop flash or optical ISO.  

From there, you can mount the HDD storage. From the mount, you can see the file permissions the owner and group. These will be numbers, probably 1000 and 1000. The fact that they are the same is extremely common, but purely coincidence.  The uid and gid are just 32-bit numbers less than 64K in size. Ubuntu usually begins normal user's (humans) at 1000 and increases +1 for each new account.  Once you have the uid, you can look that up in the /etc/passwd file under the mounted storage, not the currently running system.  Don't get confused.  Every Unix system has an /etc/passwd file, but the system on the HDD isn't being used when we boot from the "Try Ubuntu" installation media.

As for usernames and hostnames, those should be all lower-case for a number of reasons.  In theory, it should never matter, but from time to time, it does and will break something if the exact case isn't used.  Always use lowercase for usernames and always use all lower-case for hostname.  Hopefully, you'll never know about any problem, but when it happens, it really sucks.

BTW, I seriously doubt it is a 5.25inch HDD. Those haven't been made in 30+ yrs.  Perhaps 3.5inch is the size?  Doesn't matter.

Just for completeness.  All Unix-like systems use the exact same permissions models.  In the world of popular OSes today, that is all OSes except 1.  Learning Unix permissions will not be a waste of your time. [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) has a tutorial/explanation. But really just reading it isn't sufficient.  If you really want to learn this stuff, it takes about 45 minutes, 3 userids, 3 groups, and a bunch of playing around mixing and matching permissions for files, directories, using different userids, different groups.  About 25 minutes in, you'll have the "ah ha" moment and just need another 15 minutes to solidify the knowledge.  After then, you'll not have any basic issues with permissions that aren't easily solved on any Unix-like OS again.  It is worth the effort if you expect to live another 5 yrs.

---

### Post by Impavidus on 2020-09-18
That Name-OptiPlex-GX270 is the hostname. When you install Ubuntu, you have to provide a hostname and the installer proposes that name as default. Many just leave it like that. I gave my computer a different name. But after installation that name is just stored in a file and the system will continue to use it until you change it, even if you replace all hardware.

Your permission denied error seems unrelated. What are the permissions on the directory where you want to create something new?```
ls -ld ~/Desktop
```

---

### Post by ajgreeny on 2020-09-18
If you real&#314;y want to change the hostname of your machine it's  just a couple of system files, /etc/host and /etc/hostname that need editing. They are both simple text files so easy to edit.

---

### Post by oneleded on 2020-09-18
@TheFu;
wellll, i just want to make sure i get to terminology right on my HDD, so my thinking stays somewhat straight. the HDD is; 4" wide, and 5 5/8" long. ;~)
i been known to make mistakes.
HaHaHa, on the 5 years, i might make 10 or so. stfl [salty tears from laughing].
?. does it matter if ya show the hostname of your PC, while on line. [thinking of security].
PS, if hostname can have the wrong name, means it dont matter me.

---

### Post by oneleded on 2020-09-18
@Impavidus;
i finally figured that out. thanks all!!!

---

### Post by TheFu on 2020-09-18
[https://en.wikipedia.org/wiki/List_of_disk_drive_form_factors](https://en.wikipedia.org/wiki/List_of_disk_drive_form_factors) about hdd sizes.

hostnames only matter f you use names that have meaning you don't want shared. I use names of stars, hardly a national secret.
hadar regulus romulus icarus posc orion   I used longer names years ago when I wanted to learn to spell the nouns. That got old, fast.

---

### Post by oneleded on 2020-09-20
thanks i'll get back to ya; checked out Wikipedia;
Livewire
How to Use 'mkdir' to Create Linux Directories
guess i need to work on my copy and paste skill's.
think i will change the hostname, just to do it.

---

### Post by TheFu on 2020-09-20
A basic linux reference.  It is worth learning the knowledge and skills in a specific order since prior skills are necessary for almost everything.  mkdir is 1st day stuff.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a no-hassle, free, reference.

---

### Post by oneleded on 2020-09-26
i said i was going to order this in oct., 2016.and never did, finally forgot about it. Just ordered it, from this site  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) . no starch press.

i'm having trouble with checksum and keyserver. i downloaded  lubuntu-20.04-desktop-amd64.iso , sha256sum.txt.gpg ,sha256sum.txt . and thats as far as i can get. cant get the keyserver.
i put lubuntu 20.04 on a disk. the disk-check is 100%, when i run the disk. i dont know if thats enough

---

### Post by oneleded on 2020-10-01
^^^^i've been trying to verify the distro, but must be doing something wrong. i followed the instructions at this site and some other sites, and still cant do it.

---

### Post by tea for one on 2020-10-01
You do not need gpg keys to verify integrity of downloaded ISO images.

Navigate via terminal to the [COLOR="#0000FF"]location of your[/COLOR] ISO image e.g.

```
cd Downloads
```

```
sha256sum lubuntu-20.04-desktop-amd64.iso
```

Result is:-

```
cc18a581d2e4d86f3f29ef44c12a0c42b54cde93db9fc5f7c3f10db1aff3fa9a  lubuntu-20.04-desktop-amd64.iso
```

Here are the sha256sum(s) for the both recent releases of Lubuntu:-

cc18a581d2e4d86f3f29ef44c12a0c42b54cde93db9fc5f7c3f10db1aff3fa9a *lubuntu-20.04-desktop-amd64.iso
0727253098c998c0b7b7963326690419710cdce2479472ca7cfe7adda7a31174 *lubuntu-20.04.1-desktop-amd64.iso

---

### Post by oneleded on 2020-10-02
Navigate via terminal to the location of your ISO image e.g.
that must be where i am messing up. i'm not doing this the right way. thanks

---

### Post by CelticWarrior on 2020-10-02
> **oneleded said:**
> Navigate via terminal to the location of your ISO image e.g.
that must be where i am messing up. i'm not doing this the right way. thanks

Use 'cd' as in the example followed by the path to the actual location where you saved the ISO file if different from the example. Not that the "Downloads" folder exists only in English. If you use any other language for the system then this folder will have a different name.

---

### Post by oneleded on 2020-10-03
i found out some info on this last night, its basic stuff, that i didn't study, and should have in 2016. im surprised i got along this much with limited knowledge. stuff i need to learn, not told. i learn stuff the hard way, the only way. i got a bad habit of taking the translation literal, instead of as an example. i'm working on that. maybe before i'm 70, i'll get the hang of it. ;~}

---

