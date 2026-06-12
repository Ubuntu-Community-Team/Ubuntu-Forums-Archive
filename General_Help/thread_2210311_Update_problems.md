---
title: "Update problems"
date: 2014-03-10
forum: General Help
---

### Post by Alibdo on 2014-03-10
Hi,

i have a Compaq Presario notebook whit Ubuntu 12.04 LTD  installed on, it's about 1 week that i try to update my sistem with the  default updating window (I'm italian, i don't know the specific name in  english for that) actually i have 773 updates waiting, cause it doesn't  work.

It open itself and show me the list of avalaible upgrades, when i confirme it, after a bit the program crashes and teels me:
```

installArchives() failed: (Reading database ...
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%dpkg: unrecoverable fatal error, aborting:
reading files list for package 'libglib2.0-doc': Input/output error


```
I had tried to force the updates from terminal as below
```

sudo apt-get updates

```
at the end of the screen it tells:
```

W: Failed to fetch [http://ppa.launchpad.net/psyke83/ppa...source/Sources]("http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/precise/main/source/Sources") 404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/psyke83/ppa...-i386/Packages]("http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/precise/main/binary-i386/Packages") 404 Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I  know that "404 Not Found" code error means a problem whit the server  connection, i have alredy chosen in the setting pannel "main servers" as  source......... it still doesn't works

I have checked the EOL of my version it is supported until April 2017

Now I really have not others ideas...........please i need some help


Thanks in advance

---

### Post by claracc on 2014-03-10
Try to disable these two ppas from your /etc/apt/sources.list file, edit it with gedit: 
```
gksudo gedit /etc/apt/sources.list
```

and then write a # sign (comment) in the begining of the two lines wich addresses two these two ppas: 

```
http://ppa.launchpad.net/psyke83/ppa...source/Sources 

 http://ppa.launchpad.net/psyke83/ppa...-i386/Packages 

```

save and close the file and try again ```
sudo apt-get update
```

---

### Post by raja.genupula on 2014-03-10
Else from Software Sources uncheck those PPA's .Then try again .

---

### Post by ibjsb4 on 2014-03-10
Hi Raja :)

@Alibdo
Welcome to the forums

This is a reference to software sources that may help.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by Alibdo on 2014-03-10
Hi everyone 

and thanks to try to helping me, i really appreciate it


@ claracc

i have opened the source list as you show me, but i'm not really fitted into code language so i coudn't find the exact lines for the apps so I coudn't put # at the begining of these, so i decided to check the link posted by    ibjsb4     and i tickeded off the apps lines from the software sources pannel.......it still doesn't working


Actually something is changed but i don't know what this change means, if i ask to get update from terminal (whit these apps tickeded off) it runs without probs and at the end tells Reading packages........done

But from software centre it shows no changes, i still got 

[COLOR=DarkGreen]installArchives() failed: (Reading database ...
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%dpkg: unrecoverable fatal error, aborting:
reading files list for package 'libglib2.0-doc': Input/output error


[/COLOR]and the updates on waiting list are still 773

What it means?  Do I mess up anything? Do I get something wrong?

---

### Post by grahammechanical on 2014-03-10
There are two parts to updating the system.

1) we update the sources lists and determine what software packages are available to be updated. We do this in the terminal with this command:

```
sudo apt-get update
```

then we need to actually update (upgrade) the packages. We do this with the command:

```
sudo apt-get upgrade
```

The Software Centre and the Upgrade Manager will do this for us. When we instruct the Update Manager to check for updates it will run apt-get update. When we confirm we want the updates the Update manager will run apt-get upgrade.

You have removed those references to the PPA from your sources list. Next you run apt-get update. That was fine. Now you need to update/upgrade the packages needing to be updated/upgraded. You can do that with the apt-get upgrade command or through the Software Centre of the Upgrade manager. It is your choice.

It is fine to use a Lauchpad PPA to install software but once it is installed we should disable the PPA in Software Sources. Then we will not get this error.

Regards.

---

### Post by Alibdo on 2014-03-10
:confused: i got a new problem 
ubuntu runs into a fatal error : Error to open the cache (E:Read error - read (5: input/output error), E:The package lists or status file could not be parsed or opened.).


@[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")
ok i will try to upgrade it right now from terminal, but i run in the fatal error before read your post......

i upgrade it and then will see if i got the fatal error again? or it's better if i try to fix it first?

---

### Post by claracc on 2014-03-10
I have found this interesting thread: [http://ubuntuforums.org/newreply.php?p=12952725&noquote=1](http://ubuntuforums.org/newreply.php?p=12952725&noquote=1), you also seem to have a package lists corrupted but the offending package in your case seems to be libglib2.0-doc.

---

### Post by Alibdo on 2014-03-11
@claracc

I think you posted a wrong link, when i click on it i've been redirected on my own thread

i looked for "corrupted package" and i found 2 threads about packages probs......... first one "Sub-process /usr/bin/dpkg exited unexpectedly", second one "dpkg: error processing duplicity (--configure)".....
 
i'm not sure these cases are the same as me, but my problem is about [COLOR=DarkGreen] 'libglib2.0-doc' [/COLOR]package, isn't it? 

Is it possible to disinstall and install again a single package?

actually when i try to upgrade the system it tells me (I translate in english the parts that it shows me in Italian I hope you can identify the code)

```
(Reading database... 95%dpkg: unrecoverable fatal error, exit:
 list packages file "libglib2.0-doc": input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
 
```

[FONT=arial narrow]

[/FONT]

---

### Post by claracc on 2014-03-11
Yes, sorry, you are right, I posted the wrong thread, the good one is: [http://ubuntuforums.org/showthread.php?t=2112029](http://ubuntuforums.org/showthread.php?t=2112029)

Please, see particularly post 8 in the thread, and replace all said for libgnome-keyring-common with libglib2.0-doc, which seems to be the corrupted package in your case.

---

### Post by Impavidus on 2014-03-11
As you noticed, LTS means that the official repositories are maintained until 2017, but PPAs are not bound by this. Many PPA providers will have the courtesy to support the PPA at least until the next LTS is released though.

Also note that in the thread linked by claracc the error message was 'Is a directory'. In your case it is 'input/output error'. This is a bit worrying, as it might indicate a bad sector on your hard drive. Have you checked the hard drive's smart status, just to be sure?

---

### Post by Alibdo on 2014-03-11
@claracc

Thanks i'm working on it, I need a bit of time to be sure to change the typing of the code to fit it on my problem (i'm not really comfortable with codes) and i don't want to mess up something else and create other conflicts


@impavidus

HI, how can i check my hard drive status?

Maybe it's better to check it before try to fix the corruption....

Thanks to everyone for your support

---

### Post by Impavidus on 2014-03-11
Check the disks utility, it should mention the smart status.

---

### Post by Alibdo on 2014-03-12
ok actually I can't check it through utility system it crash itself every time i try to open it

can you give me instructions to do it by terminal?

my system start to run worse everyday, i really need to find the problem and fix it or i will can't be able to use my pc soon

How can i backup my system? i never done that before

Thanks for helping me, i hope to not to be a frustrating friend with system problems :D ...

---

### Post by Impavidus on 2014-03-12
There is **smartctl** (part of the **smartmontools** package) that can be run from the command line, but you may have to install it first, which may not be an option.

As your computer runs worse every day, I think it has a serious problem of which the original update problem was just a symptom. It's best to make backups before you get problems, so make them at once. I make backups every week, even though I never needed them. It's just a matter of copying your (irreplacable) files to an external drive of some sort. If you only have few irreplaceble files you're done in a few minutes. Alternatively, boot from a live disk and create a disk image on an external drive. You can also use the live disk to check the smart status of your hard disk. If the hard disk is the problem, booting from a live disk should give you a stable system to investigate and create backups.

---

### Post by Alibdo on 2014-03-12
ok i have an external drive i will copy all the important files on that......
But it is possible to check the hard drive through terminal? or i have to install smartctl for doing that (it was not really clear for me......sorry)
actually i can't install anything, so there's any possible way for trying to fix my status?

In your opinion if i try to follow the instructions in the thread posted by claracc, the situation can became worse?

---

### Post by Impavidus on 2014-03-12
First create your backups, then nothing bad can happen. Then try any suggestions you got. It may help, but I think your problem is larger.

smartctl is a command line tool (which I never used myself) to check the smart status of the disk. It's not installed by default, so it may not be on your system, so would have to install it, which doesn't seem to work. Do you have a live disk at hand? If you boot from a live disk you should get a stable system. The fact that you can't open the disks utility, which has nothing to do with the package manager, is a strong indication that the package manager isn't the only thing that's broken.

---

### Post by Alibdo on 2014-03-12
:-k okkk i always thought it has more than 1 problem, basically it is quite old and had passed through many hands over years, i don't have the live disk, Ubuntu was installed on it by a friend of mine more than 2 years ago, i can't reach him to ask for it i'm in Australia and he is in Italy........

ok, anyway, i need to think about a bit, this is the only computer that i have here and even if it has problem i can contact my family and do my stuff, and actually i can't afford to buy a new one, so i have to decide what to do about it...........

Theoretically formatting and reinstalling ubuntu could be a solution, couldn't it? Otherwise, the problem could be a physical damage in the hard drive, right?

It doesn't make noises, someone times ago told me that noises are signals of physical damages on hard drive.....
Anyway, thanks for your help, i will think about it several days and then i will decide what to do

---

### Post by claracc on 2014-03-13
Well, I also think that you best bet is to backup your /home folder and reinstall ubuntu, as your system is going more and more unstable each day.

Please, see this link in order to reinstall ubuntu: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation), note they recommend clonezilla live: [http://clonezilla.org/clonezilla-live.php](http://clonezilla.org/clonezilla-live.php) in order to do the backup. Also, you have more alternatives to do the backup through command line: [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR) or you can use the default software for backing up in ubuntu, deja dup: [http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/](http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/)

I hope it helps, good luck.

---

### Post by Alibdo on 2014-03-13
ok guys i think i have all the informations i need for now......... i starting to study all that links in order to backup my files and after i will try to reinstall it.

This process maybe will takes some time..... do you think i have to mark the thread as solved?

Thanks to all of you guys.........i will let you know when i have done :KS ...

---

