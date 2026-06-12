---
title: "New install slow and unresponsive"
date: 2013-02-02
forum: General Help
---

### Post by roger06 on 2013-02-02
Hi all,

I'm new to this forum so hello.

I've recently dug out an old ish PC, P4 2.8mhz / 512 RAM. It runs XP fine and has 16GB disk space.

Using wubi I installed 12.10 but it's unusable.  The desktop doesn't respond, when clicking on the home folder for example it might take 2 minutes to open and no apps respond. I deleted 12.10 and installed 12.04 instead but exactly the same problem.

There seems to be constant hard drive activity, which is odd.

Any help appreciated!

Thanks

---

### Post by Thee on 2013-02-02
Well 512 MB of RAM is not really a lot, so I suggest trying some light weighted Ubuntu distribution like Lubuntu or Xubuntu.
Secondly, 16 GB of disk space is also not a lot, especially if you have XP and other software installed there too.
And third, even tho you have "installed" Ubuntu using WUBI, it is still running from a Windows partition. So that will have some impact on the performance.

Some or all of the above might be causing the lag that you are experiencing.

---

### Post by DeMus on 2013-02-02
I don't know how Wubi works but I can imagine it is installing Ubuntu inside Windows meaning you now have 2 operating systems running.
When you want to use the computer for Ubuntu, install it from a CD (DVD),erase the whole disk (including Windows) and have a clean install. Let's see if it is still that slow.

---

### Post by howefield on 2013-02-02
It will have very little to do with Wubi although there will be a performance hit, you are not running 2 systems as the previous poster imagines.

Most likely the combination of low RAM and graphics card is the issue. The machine may well be using llvmpipe to draw the screen rather than using the graphics card which means the cpu will be heavily taxed simply trying to give you an image on screen let alone anything else, do you what graphics card is in the machine ? 

As Thee, try another lighter version such as Xubuntu. Lubuntu should be lighter still but it has always been such a poor distro for me I'd be reluctant to recommend it but may work well enough for your machine.

Then there are other distributions altogether, such as puppy.

---

### Post by roger06 on 2013-02-02
Thanks guys, that's really useful advice.

Wubi did install different boot options so I didn't think it was running Windows as well.

I think the answer is more RAM  - but I'll try a lighter version for the fun of it!

Thanks again...

---

### Post by Topsiho on 2013-02-02
I think you should add some RAM if you want to use a modern Ubuntu, at least to 1 GB. 512 Kb is too little, and then probably the graphics card uses a part of it.
And of course you'll need a clean install of Ubuntu on this machine. And Windows, and Ubuntu, is a little too much, so drop Windows from it.

As proposed you could also try Lubuntu or Xubuntu, of which I like Lubuntu the most, but both can not be compared to the real thing, which is Ubuntu, with Unity or something else (I have learned to love Unity, and view the older Ubuntu's as rather obsolete. Miss the applications in the panels though. The weather indicator doesn't work well).

Topsiho

---

### Post by sudodus on 2013-02-02
> **Topsiho said:**
> I think you should add some RAM if you want to use a modern Ubuntu, at least to 1 GB. 512 Kb is too little, and then probably the graphics card uses a part of it.
And of course you'll need a clean install of Ubuntu on this machine. And Windows, and Ubuntu, is a little too much, so drop Windows from it.

As proposed you could also try Lubuntu or Xubuntu, of which I like Lubuntu the most, but both can not be compared to the real thing, which is Ubuntu, with Unity or something else (I have learned to love Unity, and view the older Ubuntu's as rather obsolete. Miss the applications in the panels though. The weather indicator doesn't work well).

Topsiho
+1 for a clean install of Lubuntu. There is really not room for both Windows XP and Lubuntu on 16 GB total. (But if you have 16 GB free, you can give 10 GB to Lubuntu, and leave 6 GB free space for WinXP.)

If you want to try Lubuntu with 512 MB RAM, install it from the Lubuntu alternate iso file. With 1 GB or more use the standard Lubuntu iso file.

---

### Post by roger06 on 2013-02-09
Here's an update.

I removed the Wubi install and did a 'proper' install from an ISO on DVD.

On successful installation it was still a bit slow (still with 512Mmb RAM), but usable, not like the Wubi install.

I've subsequently upgraded the machine to 2GB RAM and it's now great!

Thanks for all your help!

(I'm now trying to work out how to launch apps that aren't in the launch bar!)

---

### Post by 3rdalbum on 2013-02-09
Right-click the Ubuntu logo on the Launcher bar, and choose Applications.

Or you can click the Ubuntu logo or tap the Windows key on the keyboard and start typing the program's name.

---

### Post by Topsiho on 2013-02-09
> **roger06 said:**
> 
I've subsequently upgraded the machine to 2GB RAM and it's now great!



Great. Congratulations to you :)
I recently upgraded RAM in my ACER ASPIRE ONE netbook, from 512 MB to the max of 1,5 GB, and it now runs Ubuntu 12.10 real splendidly. Adding RAM is very often the way to go for improving the performance of the computer.
Swap now is not, or almost not, used, and that makes a difference ...

Good luck,

Topsiho

---

### Post by roger06 on 2013-02-09
Thanks guys - I'm motoring on now I've found the apps!

Next challenge - get Plex to find my NAS...

---

