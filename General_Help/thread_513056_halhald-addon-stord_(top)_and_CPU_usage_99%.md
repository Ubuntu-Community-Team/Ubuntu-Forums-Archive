---
title: "halhald-addon-stord (top) and CPU usage: 99%"
date: 2007-07-30
forum: General Help
---

### Post by eeried on 2007-07-30
Hello,

I've been reading post on HAL, and some problems but haven't found any solutions.

Set up is Xubuntu Feisty on PIII (400MHZ, 380MB RAM). Newly-bought  DVD burner Samsung works fine it seems.

All worked fine until I think I thought it might a bright idea to upgrade the kernel from   2.6.20-15 to 2.6.20-16-generic through Synaptic. Usually I upgrade through the command line which is faster I find, and which reported lately that some packages were kept back: linux-headers and Hal stuff.

However I used k3b, k9copy since I upgraded, without any problems.

Last night, I wanted to rip one of my CD. I launched k3b which runs fine on this computer. The CPU usage was full, and the mouse hardly responded at all. So I ran top, and saw that hald-addon-stor was taking up 99%. so I killed it. The Cd couldn't mount after that. All in all I made a few experiments, sometimes the CD mounted with haldaemon-addon-storage killed but of course then K3b took up the whole CPU usage.

Just before all that I ran a DVD with no problem.

I know how to go back to the former kernel but woulfd the Hal version used be the former one? Is that the right solution?

Why is  HAL causing problems?

Your help would be very much appreciated.

---

### Post by Paul S on 2007-07-30
I think you expect too much for P3 400 mhz.  When cpu is loaded, you should just wait until it finishes.

regards,

---

### Post by eeried on 2007-07-31
Thanks for your reply Paul. I don't think I'm expecting too much because Xubuntu is supposed to work on older machines, and i've been using a **PII (400MHZ) **for 4 years with Linux.

Now the **PIII** had been workiing fine until a couple of days ago. K3b ran smoothly. I managed to rip one of my DVDs  with k9copy and then other software (DVDrip, acidrip) as experiment, I also ripped a couple of CDs and burned them without a hitch.

I tried booting the older kernel. Same result. That hald-addon-stor takes up the whole CUP usage, whether I'm using K3b or VLC: I can no longer listen to a CD!!

Waiting is no good. I have to kill hald-addon-stor. After that K3b or VLC take up the whole CPU -- I suppose they're trying to read the CD on their own, and this is mission impossible. So I kill k3b, and all's well... in a manner of speaking.

What can be the cause of this sudden problem? It isn't the new kernel since I booted the former kernel with the same result.. Does the former kernel use the latest version of HAL? And how could I install the former version of HAL?

Could the problem come from a friend's camera ( Konica-Minolta digital reflex) that we plugged in (USB) in order to have a look at the pictures. This worked very well,. Later on I made a copy a CD (Creative Common music), This worked though the burned CD didn't sound  perfect. Later, I tried to rip on of my CDS and that's when the HAL problem started.

I don't think not being able to listen to a CD with VLC is a natural thing...

Waiting until the haldaemon has finished is no use -- it doesn't finish whatever it's trying to do. Even moving the mouse takes ages.

There's enough space on the system  and on the /home partitions: free space: /=1,9G - /home=11G.  RAM: 385MB.

Perhaps I'll have to install Dapper instead but I don't understand why Feisty worked  fine until one day when it stopped being able to deal with the CD drive.

---

### Post by eeried on 2007-08-08
Please help!!

Funnily enough I've been helping some people with their HAL problem but I'm unable to solve mine. I'm totally stuck and can't use my DVD/CD player/burner which is brand new and worked fine up to a certain day.
A HAL problem which has been solved through downgrading HAL.
[http://ubuntuforums.org/showthread.php?p=3152805&posted=1#post3152805](http://ubuntuforums.org/showthread.php?p=3152805&posted=1#post3152805)

Of course I've done that. This worked once for me just after downgrading and rebooting. I tried tio rip another of my CDS and I got the same Hal CPU hog, killed it and K3b took the stand in CPU usage (probably because it needs HAL to deal with the CD).

What can I do?

---

### Post by eeried on 2007-08-13
Some news: 
I plugged the DVD-drive on the 1st IDE channel, as slave to the HDD, and everything worked fine again. then I tried to rip a certain CD, and then the same problem occurred again.

The culprit is one of my CDs which I bought over 8 years ago. The company is Warner Music. it doen't say anything about copy control. Do you think there's some kind of prehistoric DRM??

---

### Post by eeried on 2007-11-12
> I think you expect too much for P3 400 mhz

Good news: the problem seems to have been solved by Gutsy: either the kernel version or a new version of K3b did the trick. My 2 culprit CDs can be ripped without any problem now. I can even use firefox while k3b's working.

I think you should expect a lot with Linux on a reasonably old machine  :-)

---

### Post by eeried on 2007-11-30
Problem solved with Xubuntu Gutsy! :-)

---

### Post by gavintlgold on 2008-03-19
Hmm... I just had this problem again in Gutsy :( At least I'm not alone.

Same thing: trying to burn a dvd in k3b.

Well, I won't try again tonight, but I will on thursday.

---

