---
title: "hibernation don't work"
date: 2008-06-12
forum: General Help
---

### Post by yyka on 2008-06-12
hello, my hibernation and suspend mod don't work, my computer restart when I clik on hibernation and my session don't start !, so I need to completly closed my computer to restart ubuntu.

How I can fix this problem?

information config :
ubuntu 8.04
Intel graphic chipset
2Gb of ram
swap of 1gb

I know uswsup, but it don't works -(?)it's my fault?

wait your response :D

---

### Post by perillux on 2008-06-12
This is a big problem for linux in general, not just Ubuntu.  Mainly laptops.

I have the same problem too, and I can't find a solution.
You could try googling your problem, including your computer model in the search.

---

### Post by yyka on 2008-06-13
hello thanks to reply.

In ubuntu 7.10 hibernation works fine, but not in the 8.04 !!?

it's rater astonishing :@

---

### Post by Archmage on 2008-06-13
You need at least tow times your ram as a swap partion to use hibernation.

(In a hibernation your whole ram will be written in the swap partion that obvious can't work if your swap partion is smaller than your ram.)

---

### Post by yyka on 2008-06-13
thank you for your answer, but how I can do to increase my swap partition?

---

### Post by ktechman on 2008-06-13
GParted (Gnome Partition Editor) is in add and remove just download and install it but all of you edits will have to be before x boots in the text mode just follow the instructions and have fun.

      Regards

---

### Post by ubtBaba on 2008-06-13
The problem is that you cannot change the swap size as you do in windows.

In Ubuntu an entire partition is used as the swap, in windows swap is actually pagefile.sys that can be resized.

I usually don't resize my partitiions after I install the OS, but you may be able to with a partition manager.

The reason I don't is because I had some trouble in the past.

---

### Post by ktechman on 2008-06-13
:) It is the only way to accomplish the task.  the only other option is to reinstall Hardy which if you use Apt on CD (and the other back up utilities in apt) should be a snap besides that, you should have created a backup cd in the first place just to eliminate the time and effort it took to tweak your distro in the first place.  Regards  :)

---

### Post by Uchiha_madara on 2008-06-13
I Just have it While Hibernating , But Suspending it Works 
on My Laptop

---

### Post by yyka on 2008-06-13
THanks all for your interesting and response ! :D
I probably use live cd for resize my partition , gparted can't find my partition :( .
Best regards all

---

### Post by yyka on 2008-06-13
> **ktechman said:**
> :) It is the only way to accomplish the task.  the only other option is to reinstall Hardy which if you use Apt on CD (and the other back up utilities in apt) should be a snap besides that, you should have created a backup cd in the first place just to eliminate the time and effort it took to tweak your distro in the first place.  Regards  :)

If I can't do anything, I probably do that...:popcorn:

---

### Post by omrsafetyo on 2008-06-17
Hey - question about all of this.

Is this basically the only use for swap on Linux?
I have yet to see my swap space get used - and I have allocated a 5gig partition for it after reading this article ( I was upgrading to Heron anyway).
I'll probably resize this to 3gigs since it is recommended to have swap twice your physical memory...

I read somewhere else that the Linux Kernal can't use any more than 1 gig of memory anyway - because it can't assign memory addresses beyond 1 gig - this may have been for the kernal fir edgy or dapper - I don't remember exactly.  If this is true, then there wouldn't really be much need for swap - unless of course you were doing a hibernation and copying all of your volatile memory to hard drive.

Has this been fixed in a newer Linux Kernal - I just upgraded to 1.18 - should I be able to use all 1.5 Gigs of memory I have installed?

---

### Post by yyka on 2008-06-18
hello, I have change my swap partition to 1go to up to 2go, but nothing to do it's not work ! so when you see at ubuntu brainstorm the most popular ideas ever, you can see, guess what ?? yeah "fix suspend & hibernate", with 5452 vote!!.You can see here that probleme is very expend. Ubuntu must change all the system hibernation, there is a very big problem here.

have a nice day bye.:)

vote here too !
[http://brainstorm.ubuntu.com/most_popular_ever/]("http://brainstorm.ubuntu.com/most_popular_ever/")

---

### Post by omrsafetyo on 2008-06-18
I would say in your case that when the hibernation goes, anything that is already in swap is going to prevent your entire physical ram from copying.

This is one reason that it is recommended that you use double your physical RAM for swap.  It allows you some spare room.  I would up it to 3GB and try it - if not, try it again at 4GB.

---

