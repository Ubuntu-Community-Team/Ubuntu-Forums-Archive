---
title: "trying to connect to kindle"
date: 2018-02-01
forum: General Help
---

### Post by jgw on 2018-02-01
I am running with ubuntu 16.04.3
calibre version 2.55

I just tried to connect my kindle paperwhite to my computer. I plugged it in and nothing. Then I ran disks and get something that says:
drive
internal storage

Then, about 2 seconds later it goes away! At the same time I am watching to files list of connected stuff and it acts like something was going to be added but it goes away before I can see what it is.  The strange thing is that this continues to happen.  It gets connected, goes away, connect, goes away, etc.  I am not touching anything when this happens and the thing is connected according to lsusb.

lsusb gets me:
Bus 001 Device 075: ID 1949:0004 Lab126, Inc. Amazon Kindle 3/4/Paperwhite

I cannot access this thing and I always used to. My kindle firmware is ver 5.8.11

in my research I saw I should have the following installed so I installed them;
mtpfs
jmtpfs
and restarted - no help there. I have also swapped out the usb cables a couple of times

If I had a clue as to what log to look at I would have done that.

Any thoughts would be appreciated. I have never seen disks connecting and disconnecting for no reason before. I have also tried this on two other kindles with the same results.

---

### Post by #&amp;thj^% on 2018-02-01
Looks to me like Kindel is getting unmounted automatically, and I have no clue why.
Some folks with certain Lenovo laptops have reported this behavior also.
I find Life much easier to avoid DRM devices. ;)

Just some friendly suggestions:

Make Use  of "Send to Kindle" email service
If you have a good Internet connection and the ebook is not over 25MB (not too big for email attachment) you could use this method. Using this method has some advantages such as your ebook will be kept in the cloud and Amazon can convert the ebook if you want to.

I myself just send the ebook as a attachment to a cloud service.

I also had good luck with **ES File Explorer** on the Kindle, I was then able to access the files I was transferring to the Kindle.

The last time I used a Kindle was with 14.04 and my notes show that I had installed "gmtp" to get mine to show.
Anyway Good Luck jgw :)

---

### Post by jgw on 2018-02-02
Almost two hours ago I decided to try again - same pc, same usb cable, etc.  I plugged it in and - IT CONNECTED!  This just is strange.  I can now access the kindle from my pc with no problem.  Basically everything is dandy.  nothing in the phone has changed either (firmware is the same, etc).   I am going to disconnect (pull the usb) and wait and try the same thing tomorrow and see what happens <G>

---

### Post by jgw on 2018-02-27
thanks for the reply!

I tried it again and, this time, it hooked right up (with calibre).  I have no idea why or how but I am going to mark this as solved.

---

