---
title: "[SOLVED] Removing Ubuntu Partition"
date: 2007-11-25
forum: General Help
---

### Post by tennisisgood on 2007-11-25
I currently have 2 partitions on my hard disc, windows vista and ubuntu feisty fawn.  However, I encountered some serious problems w/ wireless in ubuntu and changed too many system settings  :(  .   Id like to completely remove the ubuntu partition from my hard disc so that i can redownload ubuntu "factory fresh".  I want all data removed so that theres no trace that ubuntu existed (i dont have any important docs on my ubuntu partition), w/o changing anything in my vista partition (i do have important docs there).  How can this be done?

Thanks in advance!!

---

### Post by erfahren on 2007-11-25
you can just reinstall Ubuntu to the partition(s) that it was previously on. The partition tool will have an option to format the partition ext3. Do that.

You don't need to remove Ubuntu first. (don't make it so darned complicated -lol ! - just kidding.)

anyway, if you using the Desktop CD (Live CD) use the manual partition option. see: [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
particularly this: [http://img216.imageshack.us/my.php?image=feistydual12tj0.png](http://img216.imageshack.us/my.php?image=feistydual12tj0.png)
> 
You have to decide which partitions to use or reformat and then use, and where to mount these partitions. You can also resize partitions here, too. If these last couple screenshots confuse you, you clearly need to use either the first or second option.

you'll see your Ubuntu and swap partition there (no need to format swap, just designate it as swap again). 

btw: in case you don't have this bookmarked, here's another excellent guide that deals with using the Alternate CD (text based) to install Ubuntu dual boot. It also has tons of other information (about GRUB, etc.) 
[most everything you need to know about dual-booting Windows and Ubuntu](http://users.bigpond.net.au/hermanzone/)

---

### Post by erfahren on 2007-11-25
btw: don't feel bad about needing to reinstall. I think I ended up reinstalling Ubuntu twice the first week I had it.

One thing you can do (if you can) is try getting your internet working while using the Live CD before installing. You'd be able to get the updates you need while installing.

- just a thought.

good luck!

---

### Post by erfahren on 2007-11-25
> 
(from PM)
how exactly will reinstalling ubuntu help me uninstall it?

I guess when you said that you changed too many settings (I've been there, done that - lol), and wanted to redownload Ubuntu "factory fresh" you were talking about reinstalling it.

Do you want to remove it completely and not reinstall it at all?

---

### Post by tennisisgood on 2007-11-25
well i want to install gutsy gibbon and i currently have feisty fawn...
i assume that a normal switch from feisty to gutsy will keep most system files unchanged...however given the "screwed upness" of my system, i want to completely get rid of all feisty fawn stuff first
thx

---

### Post by erfahren on 2007-11-25
oh, ok. What I said before still goes then.

See, when you go to install Gutsy you have the option to reformat the partition Feisty was on. When you reformat it, Feisty will be completely removed. You'd just be using the partition *space* that was previously created when you installed Feisty.

I assume that when you went through the installation procedure the first time you used the first option,  "Ubuntu will guide you through shrinking your Windows partition and creating a new Ubuntu partition out of the free space." 
as mentioned in that tutorial [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

You'd just be reformatting and reusing that partition (I guess I already said that - lol !). 

Anyway, as far as step-by-step instructions, I really can't do better than that guide. Do you think you'll have any problems?

---

### Post by tennisisgood on 2007-11-25
aha!!! i understand!!!
thx a million!

---

### Post by erfahren on 2007-11-25
no problem

good luck! :)

---

### Post by erfahren on 2007-11-25
I forgot to mention...

once you get everything up and running you can mark this thread as "Solved" by going to the "Thread Tools" above the first post.

---

### Post by tennisisgood on 2007-11-26
ok...i have downloaded the live cd for gutsy gibbon
however, when i went in to install gutsy, i encountered a small question
for the hard drive partition i was given a choice between two guided options and one manual option.  Initially, i went with the manual option, chose my former feisty drive, and checked the format box.  However, when i clicked next, it would work citing some problem with the former feisty drive not being in root (or something like that).  i then thot that maybe i should have selected the first guided option...so wen i tried that, i selected 100 percent (for size of former partition to use).  I was then given a prompt that if i continued, then everything will be erased and it is not undoable.  For this reason, before i select the guided option, i just want to make sure that the guided option is the correct one (and not manual).  Also, erfahren talked about a format option in the installation...i didnt see this in the guided option

thx

---

### Post by erfahren on 2007-11-26
no, you definitely don't want to go with the guided option.

The manual one is the one you want.

when you got to this screen: [http://img379.imageshack.us/my.php?image=feistydual10ea7.png](http://img379.imageshack.us/my.php?image=feistydual10ea7.png)
I think you just checked "Format" and went forward.

I think that maybe you should right-click the partition (it'll be the "ext3" one) and select to edit it. Then you should get this: [http://img216.imageshack.us/my.php?image=feistydual12tj0.png](http://img216.imageshack.us/my.php?image=feistydual12tj0.png)

you don't need to do anything with the size, just set the mount point / and keep the format with ext3 option.

I guess you may need to check the swap and redesignate it as swap as well (It'll be a small partition, about 1000MB or so). - (On that first screenshot it looks like it would be the 509MB one.)

---

### Post by erfahren on 2007-11-26
EDIT: I said right-click on the partition to edit it 
I take that back.
When you highlight the partition that "Edit partition" button should come up.

you can see it in this shot: [http://img216.imageshack.us/my.php?image=feistydual12tj0.png](http://img216.imageshack.us/my.php?image=feistydual12tj0.png)

---

