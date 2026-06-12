---
title: "A grub message I can't read"
date: 2023-01-29
forum: General Help
---

### Post by georgesgiralt on 2023-01-29
Hello Guys,
On a desktop machine made of two disks in software raid, I've Ubuntu 20.04.5 LTS installed. 
My wife started it this morning and tells me there is a line of text showing up before the Grub menu is displayed. 
Upon restart, I can confirm her saying but, as she told me, am unable to read the message because it is displayed for toot short a time. 
As I do not like to have error messages unaccounted for, may I ask a couple questions  : 
1) how do I do to log this error in order to read it and work on it ? 
2) is it possible to have Grub stop after displaying this message and before displaying it's menu ? 
Thanks a lot in advance for your help !
Have a nice day !

---

### Post by yancek on 2023-01-29
Go to the /var/log directory and take a look at the most recent boot.log files to start.  You need root (sudo) privileges to do this.

---

### Post by georgesgiralt on 2023-01-29
Thank you for your answer, but no joy :
```
# ll /var/log/boot*
ls: cannot access '/var/log/boot*': No such file or directory

```

---

### Post by grahammechanical on 2023-01-29
> tells me there is a line of text showing up before the Grub menu is displayed.

This could be a message from the motherboard's UEFI settings utility. Do you get a motherboard splash screen? It might be possible to disable this splash screen in the UEFI settings and you might see other messages.

Also, the message might be from the motherboard reporting problems finding the Grub boot files but the problem is eventually overcome as you do get a Grub menu. People who have smart phones sometimes use them to take a photograph of messages like this so that they can read them.

Regards

---

### Post by georgesgiralt on 2023-01-29
Alas, no. The MOBO has nothing to do with this because the message starts with "grub : "something. It's all I can read before it's replaced by the grub menu display. 
I'll try to use your suggestion about the phone. But I bet I should put it in video mode in order to capture the message. 
Have a nice day !

---

### Post by klundermann on 2023-01-29
I have been wondering about how to read messages that flash on the screen during boot-up and shutdown, and this thread helps.  A few follow-up questions, if I may:

    1. Is there a utility for reading log files?  Good old  less  pretty much does the job, but the escape sequences  boot.log  confuse it a little bit.
    2. Where should I look for the messages appearing during shutdown?  At the tail end of  syslog ?
    3. Does the ".1" appended to a log file simply indicate an older log?

---

### Post by georgesgiralt on 2023-01-30
Hello Guys,
So this morning I've made a short video of the screen when it boots. [Hint] : tape a little image on the screen for the phone to focus on it, otherwise, the message is so blurred one can't read anything because when the camera focus, the message is gone...[/hint]
My message reads : ```
Grub: .boot/grub/x86_64-efi/raid.mod not found
```
So maybe I've got a potential problem here... 
My computer is set up like that : 
A Windows 10 disk with the EFI system partition.
A couple of 2To disks making one software raid md0 
This md is the sole PV of the LVM Volume Group onto which the system is built. 
It has been so since about 12 or 15 years ago. (I used a lot of these set-ups in my work to make high availability systems)
And this message never showed before. 
So all help about it will be gratefully read !
Have a nice and bright day !

---

### Post by georgesgiralt on 2023-01-30
I'll answer my question myself.
In my /etc/default/grub file I had a line :
```
GRUB_PRELOAD_MODULES="part_gpt raid mdraid09 ext2"
```
And as you bet, there is no raid.mod file in /boot/grub/x86_64-efi/ directory... 
So I've removed the "raid" word in the Grub default file and updated grub. And, magically ;-) the message is gone and the computer boots up. 
I bet my Grub default file is very very old (hint : the ext2 module in the above line) and did not get updated during the life of the system and/or grub package... 
I'll tap myself in my back ! 
Well done ;-)

---

