---
title: "Can't install Ubuntu 7.04"
date: 2007-10-05
forum: General Help
---

### Post by hilfer on 2007-10-05
Hi all:

I am completely new to this.

Just trying to install ubuntu 7.04  i always cometo the following error:

"there was an error starting the gnome settings daemon.Some things such as sounds or background settings may not work correctely.The last error message was:
Did not receive a reply.Possible causes include: the remote application did not send a reply.The message bus security policy blocked the reply.The reply timeout  expired or the network connection was broken.
Gnoem will still try to restart the settings daemon next time you login.

And this is the afr i can come !!!!

what can be the problem ???

(My ubuntu CD was burned at a very low speed)

hilfer.

---

### Post by Daveth on 2007-10-05
Hi.
Welcome to the Ubuntu Forum. 
Unfortunately you seem to have bumped into what reads like a recent update bug, though this one seems to have passed me by (fingers still crossed). It is written about at length here

[http://ubuntuforums.org/showthread.php?t=554755&highlight=gnome+settings+daemon](http://ubuntuforums.org/showthread.php?t=554755&highlight=gnome+settings+daemon)

and

[http://ubuntuforums.org/showthread.php?t=553094&page=7](http://ubuntuforums.org/showthread.php?t=553094&page=7)

It seems to have various effects and a number of solutions, the last one (posted by DerSkw) being your easiest by the looks of it. In case you haven't found Synaptic it lives in System/Admin/Synaptic Package manager, then give your password, then use the search option.

---

### Post by hilfer on 2007-10-05
Yes but what's the solution now ???


All my experience with ubuntu is a simple CD where I have burned the program....

What to do now ??

---

### Post by snickers295 on 2007-10-05
my livecd did that when i didn't have enough RAM.
thats why i had to get a alternate CD.
[Ubuntu Download]("http://www.ubuntu.com/getubuntu/download")
there click the option under the download button to get the alternate CD

---

### Post by El Rogueo on 2007-10-05
update everything for good measure through the update program, or through command line

```
sudo apt-get update
``` I think, when you open terminal

that could patch up a bad file

the alternate cd is also a wonderful alternative, very easy, step by step instructions

---

### Post by hilfer on 2007-10-05
Thanks guys.

I will try the alternate CD.

hilfer.

---

### Post by Daveth on 2007-10-05
sorry- having ploughed through that post it looks like you reload the xserver-xorg-input-synaptics!

So, go System/Admin/Synaptic Package Manager, put in your password (your main login one), then in the search box at the top paste in xserver-xorg-input-synaptics
and then right click that package and Mark for Installation or Re-installation, then hit "apply"- big arrow at the top!
Seems to work for everyone in that post.

---

### Post by hilfer on 2007-10-06
Hi guys:

With alternate CD everythings goes fine untill the installation of software.
It tells me there was a mistake and that I can select from the list what to install but then... it fails again.

hifer

---

### Post by Sef on 2007-10-06
Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the iso?

---

### Post by GerryB on 2007-10-06
If everything else fails, try this:
[http://ubuntuforums.org/showthread.php?t=498538&page=4](http://ubuntuforums.org/showthread.php?t=498538&page=4)
Good luck!

---

### Post by hilfer on 2007-10-06
> **Sef said:**
> Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the iso?


No I didnt.How can I do that ??

---

### Post by hilfer on 2007-10-06
Sorry.Now it failled when trying to install the GRUB !!!

hilfer.

---

### Post by snickers295 on 2007-10-06
how old is your hard drive.
maybe its going bad or something.
i tried to install xandros linux one time and it couldn't install and i few days later my bios said "Hard Drive Detects Imminent Failure!".
what hard drive do you have and how old is it?

---

### Post by hilfer on 2007-10-06
The question is I dont know.

I borrowed this disk from my son as I wanted to test ubuntu.

will try later on another HD.

tks.hilfer.

---

### Post by snickers295 on 2007-10-06
> **hilfer said:**
> The question is I dont know.

I borrowed this disk from my son as I wanted to test ubuntu.

will try later on another HD.

tks.hilfer.
good idea.
when i started out with linux i borrowed hard drives from my grandpa and 9 times out of 10 they were messed up.
probably because they were ones he replaced.

---

### Post by hilfer on 2007-10-06
Sucess..... It was a problem with the HD.

This post is made using UBUNTU already.

And now... Oh my god.... such a lot to learn about !!!! where do I start ???

thank you guys for yr kind assistance.

---

### Post by hilfer on 2007-10-06
Well here comes my first problem.
Totem refuses to play my AVI files.!!!

Please explain how to do it.

But the easier way as I read already a lot but didnt understand anything.
Tks.

---

### Post by strabes on 2007-10-06
You need to install the ubuntu-restricted-extras package. You can either use synaptic package manager (System > Administration > Synaptic Package Manager) or use the terminal (Applications > Accessories > Terminal). If you choose the latter, simply run ```
sudo aptitude update && sudo aptitude install ubuntu-restricted-extras
```

---

### Post by hilfer on 2007-10-07
when I run the code , i get a message that  dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. when I enter the dpkg it tells me that operation requires superuser previleges !!!  dont know what to do
!!!!

When I use first option synaptic package  manager i get more or less same error:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

?????

hilfer.

---

### Post by hilfer on 2007-10-07
Another problem.

My internet conection is not working !!! There's a red cross showing on the conection icon. 


Dont know how to fix it !!!

Some help please.

---

### Post by snickers295 on 2007-10-07
your welcome for the help and what type of internet do you have is it wireless or is it wired. if its wireless what card is it.

---

### Post by hilfer on 2007-10-07
I have cable , not wireless.

The pc with unbuntu is connected at my router with normal cable.

It was working this morning.... 


Now it's not.

---

### Post by snickers295 on 2007-10-07
has anything been changed since then to the computer or the modem?
try going into System>Administration>Network and see if you can tinker with that to get it to work.
i will keep thinking about it :)

---

### Post by hilfer on 2007-10-07
Nop I didnt change anything.

I was trying to install the extra packages this morning but I didnt suceed.

Only noticed in the afternoon that I had not internet on that computor !!!

hilfer.

---

### Post by hilfer on 2007-10-08
ok connection started again when booting this morning.

But I still cant open any internet page.

Now I gave up using ubuntu on that PC, as I think it has not the necessary stuff to work correctely.

I am just installing ubuntu on my PC using  innotek virtualbox.

Will come back later with more news or questions.

tks.

---

### Post by snickers295 on 2007-10-08
thats a better idea until you get the hang of linux.
i hope you enjoy using on virtual box.
when i first started linux i had no choice but to stick with it because I'm only 12 years old and i can't afford to buy a new windows cd so i read something about linux and it took a year to get the hang of it but here i am happy and $300-for-an-operating-system free:).
good luck with your computer!

---

### Post by strabes on 2007-10-08
If your internet connection works intermittently, it's a problem with just that: your internet connection. Not ubuntu.

Linux is not windows. Things work differently/better. Your user account does not have write access to system files. This is a security feature. To temporarily gain super user access, you can use the "sudo" command:```
sudo dpkg --configure -a
``` Then run:```
sudo aptitude update && sudo aptitude install ubuntu-restricted-extras
```

---

