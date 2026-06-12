---
title: "Weird Chinese Characters on the Address Bar | MOZILLA"
date: 2013-03-18
forum: General Help
---

### Post by sorc3r3r on 2013-03-18
Well..I came across this accidentally.
Let me explain.
I was connected to the internet and I tried to launch "System Monitor" from the dash. But unfortunately, the SIMPLE SCAN icon popped up and got stuck on the Mouse Pointer. I ended up dragging that Icon to the Address bar of Mozilla Fire Fox. 
Viola. ..there was this weird chinese characters on the address bar. but it was not prefixed with "http"  extension.[while it was on the address bar"]

Just out of curiosity, I copied that chinese text from the mozilla's address bar and pasted it in the Text pad.
When I pasted it in the TEXT PAD  the chinese text had the "http:" prefix.

----------------------------------

To clarify this weird thing I am attaching the Screen shots of the process.[I] [ Yes.I was able to replicate my "accidental discovery". So it is not an Act of God :P]
[/I]
1)Simple Scan is selected

[ATTACH=CONFIG]240309[/ATTACH]

2)Dragged that "SIMPLE SCAN" and dropped it on the address bar of mozilla
                                                                            

[ATTACH=CONFIG]240310[/ATTACH]


3)Address bar showed Weird Chinese characters (?????!!!!!????)

[ATTACH=CONFIG]240311[/ATTACH]
4)Copied the CHINESE TEXT on to the TEXTPAD. It automatically got prefixed with HTTP

[ATTACH=CONFIG]240312[/ATTACH]

=============================

My Question is

1)Isnt the address bar supposed to show the "Application Path"?* [ I havent used MSWindows for quiet a lonnnnnnnnnng time, but I think i have seen something like this in Windows Os,where it shows the application path???!!]*

2)Isnt the MOZILLA supposed to pop out a dialogue box saying  "Sorry, you cannot open that SIMPLE SCAN  using Mozilla!!!" or something.

3)Is this symptom of some kind of VIRUS or MALWARE?



==================================

I am using 

UBUNTU 11.10
Kernel Linux 3.0.0 -32 Generic
GNOME 3.2.1


Mozilla  Firefox for UBUNTU :19.0.2
=================================

I just have a standard installation. I havent installed anything from the software center other than VLC and the codecs.Yeah also GOOGLE TALK plugin for Gmail.

---

### Post by ibjsb4 on 2013-03-18
Can't you just use Google Translator and be good with it?

No not really :) I just couldn't resist.  Thats what my 5AM humor looks like.

MY thought is 11.10 reaches end of life next month.  Why not upgrade to 12o4 and see if you troubles go away?  It can happen.  I say backup your files and go for it.

---

### Post by sorc3r3r on 2013-03-18
> **ibjsb4 said:**
> Can't you just use Google Translator and be good with it?

No not really :) I just couldn't resist.  Thats what my 5AM humor looks like.

MY thought is 11.10 reaches end of life next month.  Why not upgrade to 12o4 and see if you troubles go away?  It can happen.  I say backup your files and go for it.

====

Well..I actually did that translation part too. :D

"Last the King &#12090; the task bar the hunting &#12146; Ben Vitex &#12133; Lan eliminating the transition the Shi Yi Hunting Tuan Hao and eliminate &#11621; Yueyu Lead-free Show Room Tao lights /"

===========


Yes.Iam planning to upgrade..but should I format my linux partition or not that is the question now.

I usually, click  the "Upgrade" button on "Update Manager" to accomplish the task.
but this time...i kinda feel like formatting the linux partition.
Btw..I use dual boot with Windows 7 [I use windows 7 just because of Photoshop and some desktop software testing]

it would be helpful if you could tell me, how i can format the linux partition and upgrade to Ubuntu 12.04.

---

### Post by ibjsb4 on 2013-03-18
There is no need to format a partition for an version upgrade (if I understand the question).

Unless your current install is wubi (not dual boot, but ubuntu inside windows).

---

### Post by mörgæs on 2013-03-18
Yes, go for a clean install.
If you do a live boot you can delete the Buntu partitions using Gparted. After that you can install in the free space.

There are also other ways but this is the safe one.

---

### Post by sorc3r3r on 2013-03-18
> **ibjsb4 said:**
> There is no need to format a partition for an version upgrade (if I understand the question).

Unless your current install is wubi (not dual boot, but ubuntu inside windows).

Yes.I do understand that, about formatting partition.I used to do upgrades from previous versions.
but with that Junk characters as stated in my original question. I dont want to take a chance.

Nope..its not Wubi

---

### Post by sorc3r3r on 2013-03-18
> **mörgæs said:**
> Yes, go for a clean install.
If you do a live boot you can delete the Buntu partitions using Gparted. After that you can install in the free space.

There are also other ways but this is the safe one.

Okay.I will try an install using Live Boot

---

### Post by ibjsb4 on 2013-03-18
I really like this gparted tutorial

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by sorc3r3r on 2013-03-18
> **ibjsb4 said:**
> I really like this gparted tutorial

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

thanks. I am gonna check it out

---

### Post by sorc3r3r on 2013-03-19
Did anybody else have/had the same problem..
or
is it just me?

---

### Post by sorc3r3r on 2013-03-21
> **ibjsb4 said:**
> I really like this gparted tutorial

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

OKay.
 I have a question. I am a bit concerned about the Chinese Characters that popped up.* [ I am not sure if everyone is havin that kinda symptom or i am just overreacting].* So this time I am planning to do a format of my Linux Partition before installing Ubuntu 12.04.


When i download and burn the New Ubunutu 12.04 onto a DVD and then try upgrading my existing Ubuntu 11.10 via that DVD, will it install after formatting my existing Ubuntu 11,10 partition. or will it be just like "Upgrading" via Update Manager.

I believe that Upgrading via update manager doesnt really formats the linux partition. 


I have 3 NTFS partitions 
1 NTFS partition where i have installed Windows 7 and 2 other NTFS partitions where I have stored datas. Then there is Ext4 Partition and 1 swap partition where i have installed linux.
During the install process, I dont want to messs up the partition table and create hell for me. So i want a simple and efficient method to format the Linux partition and Install Ubuntu 12.04.

-

---

### Post by mörgæs on 2013-03-21
See post #5.

You don't need to format, just erase the old contents (=Ubuntu 11.10).

---

