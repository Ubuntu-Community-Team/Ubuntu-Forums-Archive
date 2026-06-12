---
title: "Few things on Ubuntu 13.10"
date: 2013-10-26
forum: General Help
---

### Post by GSilvaPT on 2013-10-26
Hey guys.

So, this is the first time I'm feeling anoyed and sad about Ubuntu, and I really need your help to fix it.

As stated before, I've the blinking mouse problem. I followed the steps on that thread of "known bugs" and it still doesn't work.

Another problem: Every now and then, when I start Ubuntu, I don't have some icons on the upper right place (I know it has a name, but I can't remember it). Right now, I don't have the watch and that settings button which allows me to shut down the computer or other things. 

Can anyone tell me any way to fix this problems permanantly?

---

### Post by fantab on 2013-10-26
What computer do you have laptop/desktop? What architecture, 32bit or 64bit? What graphics card?

Look in the /var/log folder for log-files. Check the logfiles for any reported errors[EE] and warnings[WW]. Sometimes reinstalling can be the best workaround.

You can try resetting unity with [Unity-Tweak-Tool ]("https://apps.ubuntu.com/cat/applications/unity-tweak-tool/")
```
unity-tweak-tool --reset-unity
```

If that doesn't help:
```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by GSilvaPT on 2013-10-26
Hey again!
Thanks for replying!

I'm using a laptop, 64-bit version with a Geforce 310M and with 4GB Ram.
I have log-out and log-in again and it worked...

Oh, I forget that I have no ballons for the actions I do like changing volume and/or brightness... I know this is a known bug, but it didn't worked too

---

### Post by fantab on 2013-10-26
Did you try Unity-tweak-tool? or just regular logout/login worked?

---

### Post by GSilvaPT on 2013-10-27
Just the regular one worked. It does't mean though that tomorrow it will happen again. But I've installed the Tweak tool too. Just in case, you know...

---

### Post by fantab on 2013-10-27
It may or may not recur. I just wanted to know how you fixed it. 
Mark the thread as solved using Thread tools.

---

### Post by richardsdma on 2013-10-27
the issue is not solved yet! sometimes these problems occurs to my end too. my solution is to restart lightdm
> sudo restart lightdm

---

### Post by GSilvaPT on 2013-10-27
Err, I'm not marking the thread as solved. 

I have my mouse blinking, half a dozen of problems that are not fixed.
My mouse keeps blinking, every time I start Ubuntu it crashes by itself and I got a few boxes of "Ubuntu Stopped Working -> Send report problem" and it's not a solution to be restarting everything over and over when it isn't going alright. Oh, and I also have the issue of no warning icons whenever I turn the volume up or down, brightness and all other kind...

Just one more thing: Is it possible to downgrade to Ubuntu 13.04 without formatting my laptop? It's just because this is anoying, I need this to work and I have no minimal conditions to work properly. Also, I have a lot of information here and I lack of time to do everything from the start... Again...

---

### Post by fantab on 2013-10-27
No, you cannot downgrade without formatting. Nor, can you re-install without formatting '/' partition.

Do you have a separate /home partition? If yes, then we can re-install without formatting the /home partition.

---

### Post by GSilvaPT on 2013-10-27
No I only have 2 partitions. One for Ubuntu and another one for Windows (gaming...). I guess I have to hold on with it :\

Thanks though

---

### Post by fantab on 2013-10-27
If you can boot Ubuntu DVD/USB then you can save all the important data to an external storage device. Then you can reformat the partition and re-install.
Also If you have only two partition then, don't you have a SWAP partition? How much RAM do you carry in your machine? Sometimes those problems can be caused by not having a SWAP partition having basic amount of RAM.

If you want to re-install then I suggest you make more than one partition for Ubuntu. Something like this:
xxGB Windows NTFS
30GB Ubuntu EXT4 '/'
4GB SWAP
All the remaining GB EXT4 Data partition (you can either mount it as /home or keep it as simple partition without using any mountpoint).

---

### Post by GSilvaPT on 2013-10-27
Err, I don't know if have that.
I divided my hard disk in two. Installed windows on one of them and Ubuntu on the another one. Whenever I start my PC I choose which OS I want to and I have access to all RAM, independently to which OS I'm chosen. Btw, I have 4 GB of Ram. Is this enough for what you said?

---

### Post by fantab on 2013-10-27
Yes it is enough. But having SWAP partition is recommended, even though it may not be utilized. [More info on SWAP]("https://help.ubuntu.com/community/SwapFaq").

---

### Post by richardsdma on 2013-10-27
you better go for ubuntu 12.04....more mature and stable.

---

