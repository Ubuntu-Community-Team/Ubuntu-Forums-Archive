---
title: "Good practice for Ubuntu setup"
date: 2016-09-11
forum: General Help
---

### Post by petenoob on 2016-09-11
I have a dual partition, one with Windows 8 and the other Ubuntu 16.04.

I want help in creating the best setup and good practice so if anything happens like I accidentally delete system files by mistake, I can restore the partition from image or clone.

First, for the Ubuntu OS, I have 2 partitions 100GB each. I plan one for the OS and other to move the Home folder in. Question, how big should the OS partition be? What is the minimum to run Ubuntu smoothly?

Second, I think it would be good practice to make a backup of the freshly installed Ubuntu. I have two options, cloning or imaging. Question, is there much difference between the 2 ways? If I want to restore everything back to the freshly installed Ubuntu OS, without all the fuss, would a clone be better or would an image suffice? (not sure if imaging would screw up booting!?)

Thanks!

---

### Post by DuckHook on 2016-09-12
> **petenoob said:**
> I have a dual partition, one with Windows 8 and the other Ubuntu 16.04.I can't help you with the Windows stuff because I stopped dual booting it years ago. I should warn you that there are some complexities involved in dual booting with Windows, but others will have to advise you about the specifics.> I want help in creating the best setup and good practice so if anything happens like I accidentally delete system files by mistake, I can restore the partition from image or clone.In all my years using Linux and Ubuntu, I've never bothered to image or clone my system. Whenever I've done something so stupid as to make the OS unrecoverable, I just reinstall the OS from scratch. It takes only 20 minutes on my main box and a slightly longer 25 minutes on even my old underpowered laptops. It's so easy that I just don't see the benefit of cloning or imaging with all of the attendant risk (doing it wrong could hose your Windows install), or obsolescence (you are taking a snapshot that is bound to quickly age and become outdated with Ubuntu's almost daily upgrades).

The whole cloning thing was originally required (and made valuable) because of the limitations of proprietary software. A lot of such software use up a license each time you install it. So, in the event of a disk crash, it makes sense to just restore a clone onto a new disk. But that consideration is nonexistent in Linux, so the value of cloning lies only in the convenience. Since your intent is to clone or image a system right after a pristine install, even the convenience aspect is of very limited value and I just don't see the point. Unlike proprietary handcuffware, installing a new Linux system&#8213;along with all of the apps you are likely to want&#8213;doesn't cost you anything in either money or extra time.> First, for the Ubuntu OS, I have 2 partitions 100GB each. I plan one for the OS and other to move the Home folder in. Question, how big should the OS partition be? What is the minimum to run Ubuntu smoothly?My system partition is 30 GB of which I use only 7.5 GB. Granted, I don't have huge apps like games loaded, but even with games, the app tends to be reasonable: the disk hog is all of the data, and that usually resides on /home. So, you generally don't need a large system partition, but you can never have enough data. It is important to remember that /home doesn't have to be especially large either. On my system, /home is actually left in my system partition and I have created another partition only for data. I offload *all* of my important data onto this partition and then symlink them all back to each proper /home directory. I only have to backup this /data partition and don't even bother with anything else.> Second, I think it would be good practice to make a backup of the freshly installed Ubuntu. I have two options, cloning or imaging. Question, is there much difference between the 2 ways? If I want to restore everything back to the freshly installed Ubuntu OS, without all the fuss, would a clone be better or would an image suffice? (not sure if imaging would screw up booting!?)

Thanks!Others can help you if you are intent on cloning or imaging. I don't want you to think that my suggestions are the only way to go. I know that may Linux gurus are sold on cloning and imaging, so they can advise you on the various benefits and pitfalls to watch out for.

---

### Post by ian-weisser on 2016-09-12
> **petenoob said:**
> I want help in creating the best setup and good practice so if anything happens like I accidentally delete system files by mistake, I can restore the partition from image or clone.

Agree with DuckHook.

Three good habits are* Versioned Backups* of your data, creating a system that is *Easy to Reproduce* on bare metal, and learning you own *Good Security Habits*. 

Ubuntu includes excellent tools for versioned backups. Add to your plan a method of backing regularly to an external (and/or offsite) device that won't be destroyed by the same fire/flood/pet. 

Easy to Reproduce can use images, can use clones...or can simply use a set of written notes. Ubuntu is *easy* to reinstall. Complex imaged/cloned systems can be difficult to upgrade. I backup only data. On the rare occasions hardware needs to be repaired or reinstalled, a fresh LiveUSB installer takes only a few minutes.

Good Security Habits has many excellent threads in this forum already.

Limiting yourself to 'image or clone' closes the door on some very good, simple, robust, easily-supported options.

---

### Post by petenoob on 2016-09-12
Thanks for your posts. Cloning or imaging, to me, is just simple straight forward no nonsense type of backing up. I don't like typing things in and directing, moving and point to files and folders by code, it is just annoying and even more annoying when I get it wrong. I just got familiar what clonezilla and now very comfortable reading and saving images of my Ubunut OS. I am very surprised by how short the process takes, about 10 minutes for a 10gb system file. 

Yes, I am cloning a fresh install but also a fresh install of all the other programs I prefer too, like image editor, media player, file manager etc ... Also, I have install a webserver with a CMS/LMS setup, and I not familiar with it and has screwed it up many times already. In a nutshell, I do not have to mess around and install everything again from a new Ubuntu install. So I imaged all that in one neat package and can restore everything if anything goes wrong. I don't know if it is the best way but it works.

Thanks guys, I really appreciate your input.

---

### Post by petenoob on 2016-09-12
Anyway how to tag this thread as solved?

---

### Post by DuckHook on 2016-09-12
Great to hear that you've arrived at a solution that works for you. Linux is all about choice.

You can mark threads *SOLVED* using the *Thread Tools* option in the menu bar at the top of this thread.

Good Luck and Happy Ubuntuing!

---

### Post by carl4926 on 2016-09-13
I have read many times of those who 'Image/Clone' their entire HDD/SSD 
Only later do they find it doesn't restore properly.
The entire process is time consuming and unwieldy for a regular backup situation

Personally I have made entire copies of drives using DD. though this has been with rescue in play on drives that are failing
And recently for customers who want to transfer from a HDD to SSD
You have to be careful with DD!
But it's worked 100% for me so far, where other clone tools have not.

My own system is just backed up by copying files from source to backup drive and I too would reinstall should that be required.

---

### Post by petenoob on 2016-09-13
So I was trying out ways of backup files and folders and this is what I got from the end of the Ubuntu Backup. Looks like a failure!

[https://s18.postimg.io/wnak62f1l/Screenshot_from_2016_09_13_16_17_09.png](https://s18.postimg.io/wnak62f1l/Screenshot_from_2016_09_13_16_17_09.png)

I am starting to get nervous about backups in general!

---

### Post by petenoob on 2016-09-13
> **carl4926 said:**
> I have read many times of those who 'Image/Clone' their entire HDD/SSD 
Only later do they find it doesn't restore properly.
The entire process is time consuming and unwieldy for a regular backup situation

Personally I have made entire copies of drives using DD. though this has been with rescue in play on drives that are failing
And recently for customers who want to transfer from a HDD to SSD
You have to be careful with DD!
But it's worked 100% for me so far, where other clone tools have not.

My own system is just backed up by copying files from source to backup drive and I too would reinstall should that be required.

I have terrible fat fingers. I like Ubuntu (haven't played with Windows for 2 weeks now) but definitely a steep learning curve. To me, playing with DD in terminal is playing with fire! :D

---

### Post by sudodus on 2016-09-13
Yes, ***dd*** is a very powerful but also dangerous tool, because it does what you tell it to do without questions. So if you tell it to wipe your family pictures ...  and it can be one single typing error away. dd deserves the nicknames 'disk destroyer' and 'data destroyer'. I made ***mkusb*** to put a safety belt around it. mkusb can be used to backup whole drives too, but it is much better to use ***Clonezilla*** for that purpose.

I agree with the previous posters, that there are many other alternatives to backup a system. I make complete cloned copies once in a great while, but on a regular schedule I sync my data partition with ***Unison*** and backup my home partition with a simple ***rsync*** script.

Finally, it is very important to ***test your backup*** to a 'third drive'. You should only rely on a backup system, that you have tested.

---

### Post by RobGoss on 2016-09-13
A lot of good Information about backing up ones Linux system I have to say keeping things simple sure helps. 

I do use clonezilla because I found it to be easy to use and restore a broken system or one who fails to load for some reason

I'm more the kind of person that keeps very little to no documents on my machines just a few pictures and not many programs 

There are a number of good programs to help you backup your system I'm sure this topic will be worth book mark

---

### Post by petenoob on 2016-09-14
> **sudodus said:**
>  ....it is very important to ***test your backup*** to a 'third drive'. You should only rely on a backup system, that you have tested.

Hey friend, how do you test a backup? Do you mean checksum?

---

### Post by sudodus on 2016-09-14
You get new drive of at least the same size as the original drive and restore from the backup to the new drive. You must ***know***, that you can do it, that you have all the data, knowledge and hardware for it.

---

