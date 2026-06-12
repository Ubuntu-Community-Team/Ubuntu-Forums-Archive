---
title: "Stuck, completely irritated, music-less."
date: 2018-08-02
forum: General Help
---

### Post by Amelia_Hayner on 2018-08-02
hello. I have spent the better part of a day this week trying to solve this, and it is beyond me. ( I am 62, I work with museums on 17th and 18th century looms and spinning wheels, educating public. I just can't do this)
the problem is: I LOVE Mate. it fills all our computer needs but ONE- I cannot get to my music being held hostage in itunes. I have looked at forums, other people have issues too! but somehow they solve them. it is not working for me. I used Itunes as the place to store ALL my music. And there it sits.
I have installed Itunes 10 32 bits, so I have that.
I have Rhythmbox. I installed PlayonLinux as some said that might be a fix. nope. 
any other ideas?
I promise to send you a skein of handspun wool if you can help me.
thank you.
Mate 16.04 LTS

---

### Post by HermanAB on 2018-08-03
Hmm, well, at 62, you definitely have the experience to solve anything, especially considering that it is our generation that invented computers and space travel...

Have you tried these two methods? 
[https://www.lifewire.com/how-to-use-itunes-on-linux-1999251](https://www.lifewire.com/how-to-use-itunes-on-linux-1999251)

I would install Virtualbox (from the Oracle web site NOT from the repos) and then install Windows in that.  That way, you can run Windows in a Window, the way the computer gods intended things to be.

BTW, while I do own Macs and is typing on one right now, I always avoided the iTunes lock-in and doesn't use it at all.  What I use instead, is a little app called Radium to play any one of thousands of radio stations on the web - for free.  I am listening to Radio Blanik from Chec Republic now. On Linux I use Streamtuner. 

Many years ago, I encoded all my CDs, with the result that I now have two huge disk drives full of music - lying in my junk box.

---

### Post by QIII on 2018-08-03
Our generation ROCKS!

Ow, ow, ow!  I just threw out my back!


There is the matter of the cost of the Windows license, but a VM might be a good try.  I haven't used VBox for a long time, but I do wonder if audio might be a bit of a challenge.  Video definitely is.

You might also try KVM (kernel-based virtual machine, which is what I use), which is built into the kernel and doesn't require anything more than installing Virtual Machine Manager from the repos if you want a GUI to interact with it.  KVM take a bit of work to learn, but If I can figure it out ...

---

### Post by HermanAB on 2018-08-03
Both audio and video work perfectly fine in Virtualbox.  I use it every day, and so do my 20 odd SW developers.

---

### Post by VMC on 2018-08-03
I have Windows on two separate partitions/drives. Both have licenses. I was considering VB, but doesn't VB running **Windows** need a license also? I haven't use VB since XP days. I think I would rather have VB.
edit: added Windows under VB for clarity

---

### Post by HermanAB on 2018-08-03
Virtualbox is free for personal use and the version provided by Oracle is better than the version in the repos (due to USB patents).

---

### Post by VMC on 2018-08-03
> **HermanAB said:**
> Virtualbox is free for personal use and the version provided by Oracle is better than the version in the repos (due to USB patents).
I worded it wrong.

---

### Post by Amelia_Hayner on 2018-08-10
thank you. I carefully wrote all that down, and now feel brave enough to go in search of the Oracle.
I took a week off, painting walls in our new house, and I swear it was less work.
will let you know if this works.
you did not mention if you want spun wool, alpaca, or mohair.

---

### Post by mc4man on 2018-08-10
Are you able from some computer somewhere to copy your itunes music to an external device, hdd, ssd, thumbdrive, whatever?
If so you may be able to the import the music using banshee which could result in local copies of the tunes. (assuming non drm..

---

### Post by Amelia_Hayner on 2018-08-12
what a great idea. you cannot assume that I have no drm, though. or my music does. if it's a jinx, I am pretty sure it's there.

---

