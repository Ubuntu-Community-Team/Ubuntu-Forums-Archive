---
title: "On Chromebook... Uhhhh!"
date: 2013-08-31
forum: General Help
---

### Post by arnold2 on 2013-08-31
On the day I bought my Chromebook I soon realised that only thing it can really offer is Google Chrome and some useless apps from the Google Store, which was hugely disappointing (shame on me for not doing my research! ](*,)#-o). Shortly after that I decided to look for an alternative operating system and as you've might have guessed by now I ended up with ubuntu. :lol:

I used the following video as a guide

[http://www.youtube.com/watch?v=vpDtD4eKBB4](http://www.youtube.com/watch?v=vpDtD4eKBB4)

This worked, but I'm experiencing some major problems...

First of all I would like to add that I have looked everywhere for solutions but nothing has worked and I'm getting a bit frustrated. I read lots of good stuff about ubuntu so I'm willing to give it one more try before moving on, and ask for help directly from you guys in hope of finding solutions to the following problems.

Here it goes...

I can't install anything... ANYTHING. For example, I've been trying to get hold of flash player. Now, on the Adobe Install website it says I'm running on 32-bit Linux, but believe me I've tried both 32 and 64-bit,and downloaded every file available (APT for ubuntu/ .tar.gz / .rpm / YUM) and still the same problem keeps popping up  Error: Wrong architecture 'i386'. This obviously wouldn't be an issue if flash player was present somewhere, but even using terminal commands it can't be found. Almost forgot... for some reason I sometimes can't download files on Chromium, so I got Firefox temporarily. The following message is shown after I'm asked to launch an external application    Failed to open URI "apt:adobe-flashplugin?channel=$distro-partner".     and     The specified location is not supported. The main reason why I want to get flash is so that I can view videos on YouTube. Luckily I found a substitute in Synaptic called Minitube, but guess what... it won't play videos! Instead, the video's description is shown and no sound is produced. 

That's it for now. But don't worry, there is more  :P     

Thanks

---

### Post by mdurham on 2013-08-31
It's nothing to do with Ubuntu. I think there is no Flash Player for ARM.

---

### Post by kaldor on 2013-08-31
> **mdurham said:**
> It's nothing to do with Ubuntu. I think there is no Flash Player for ARM.

This is correct. The Chromebook you have does not use an x86 processor, but instead an ARM processor. Remember back when Macs had major compatibility issues? It was because they were using PowerPC instead of x86. See here for more details: [https://en.wikipedia.org/wiki/ARM_architecture](https://en.wikipedia.org/wiki/ARM_architecture)

For all of your software needs, view the Ubuntu Software Centre. Luckily, Flash is being phased out and will hopefully rot soon. 

There may be some workarounds. Hopefully the following will work on an ARM machine:

1) Open a terminal (easier for you to just paste commands)

2) Run this command (this will install a bunch of codecs and useful extras that are patent-encumbered or proprietary):
```
sudo apt-get install ubuntu-restricted-extras -y
``` 

3) Visit youtube.com/html5 and "join the HTML5 trial" if you haven't already. Maybe now you can view more videos.

Good luck.

---

### Post by aysiu on 2013-08-31
I don't know what the YouTube video is, but your best bet would be to use Crouton:
[http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/](http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/)

It uses *chroot* to have both ChromeOS and Ubuntu on your Chromebook but without dual-booting. You can switch between the two environments seamlessly, so if you need a web browser and Flash, you can use ChromeOS, and if you need GIMP or some random other desktop application, you can switch to Ubuntu.

---

