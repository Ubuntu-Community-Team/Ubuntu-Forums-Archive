---
title: "Back at Ubuntu! Guess what? MORE Problems!"
date: 2007-09-20
forum: General Help
---

### Post by kris2pe on 2007-09-20
Problems:
Internet is SLOOW! 
I don't why but I will admit in XP the internet is way faster! 
Any solutions to this?
Looking for drivers of 8600gt!
Look like Ubuntu can't enable this driver?

Hmm Lemme Guess ppl will ignore until I do **** fit! Right?
Don't make me!

---

### Post by angryfirelord on 2007-09-20
Ok first, calm down. People will be less likely to help you if you're flipping out.

Now, when you say the internet is slow, what part of it is slow? Is it web pages, downloading files, or both? How are you connected to the internet?

As for your drivers, the 8600GT is too new for the 9755 drivers. Before I tell you (or someone else) how to set up the nvidia drivers, are you using 32-bit or 64-bit Ubuntu?

---

### Post by Zero Prime on 2007-09-20
The reason people may not be answering is because not everyone has this problem.  Internet is way faster for me on Ubuntu than it was on XP, and that was after all the network tweaks I had to do to get XP to use my broadband connection to it's best potential.  As for the video problem, Nvidia just released a new driver that should help with your problem.

---

### Post by mikewhatever on 2007-09-20
Frustrated as you may be, there are good and bad ways of asking questions. At some stage, do yourself a favour, read the following --> [http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/](http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/)

I have no idea what you mean by 'slow internet'. Do sites load slowly? Is it an issue with torrents? Does it take ages to connect?

Assuming 8600gt is your nvidia graphics card, I think the driver for it is not included because it may be too new. Get the appropriate driver from nvidia and manually install it.

---

### Post by kris2pe on 2007-09-20
> **angryfirelord said:**
> Ok first, calm down. People will be less likely to help you if you're flipping out.
Well I'm not actually flipping out! I'm very infamous for flipping! But right now I'm flipping out! YET!
> **angryfirelord said:**
> 
Now, when you say the internet is slow, what part of it is slow? Is it web pages, downloading files, or both? How are you connected to the internet?
Download wise! YES! Compared to xp I'm dling from 70-100+ KBPS while here well its just obnoxious! Its a time waster! Linux could do better! Well it never does based on personal experience! 
> **angryfirelord said:**
> 
As for your drivers, the 8600GT is too new for the 9755 drivers. Before I tell you (or someone else) how to set up the nvidia drivers, are you using 32-bit or 64-bit Ubuntu?
32bit! SO you mean to say I've purchase this so that I can't use it? True power of LINUX? 
> **Zero Prime said:**
> The reason people may not be answering is because not everyone has this problem.
W/ Linux there's always a problem! Well not to say that XP isn't plague w/ it. Its just that there's so many resource & well made solutions to it! Unlike in Ubuntu where problems vary & too different & sometimes unsolvable! Don't get offended its the truth serum talking! 

> **angryfirelord said:**
> 
 As for the video problem, Nvidia just released a new driver that should help with your problem.
How? Do I have to dl it? Mind you I've never compiled a driver! 

> **mikewhatever said:**
> Frustrated as you may be,
Isn't everybody? 
> **mikewhatever said:**
> 
 there are good and bad ways of asking questions. At some stage, do yourself a favour, read the following --> [http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/](http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/)

R U insinuating that I'm LAZY? Tell u what first Ubuntu has fix some of old issues b4 even release new once. I'm sorry the problems in Edgy still plagues Feisty. Although there are barely noticeable improvements, in a neophyte perspective. It would be nice not to do anything that I usually do! But lets face it! Its plague w/ problems! That so many user are suffering w/! Its got potential but the developer always seems to fall on deafs ear! Thank GOD for dual boot & XP! So while I wait for another 24 hrs for you to figure things out I will zip my way to productivity if you don't mind! 
BACK TO XP !  

> **angryfirelord said:**
> 
As for your drivers, the 8600GT is too new for the 9755 drivers. Before I tell you (or someone else) how to set up the nvidia drivers, are you using 32-bit or 64-bit Ubuntu?
32bit! SO you mean to say I've purchase this so that I wouldn't! 
> **Zero Prime said:**
> The reason people may not be answering is because not everyone has this problem.
W/ Linux there's always a problem! Well not to say that XP isn't plague w/ it. Its just that there's so many resource & well made solutions to it! Unlike in Ubuntu where problems vary & too different & sometimes unsolvable! Don't get offended its the truth serum talking! 

> **angryfirelord said:**
> 
 As for the video problem, Nvidia just released a new driver that should help with your problem.
How? Do I have to dl it? Mind you I've never compiled a driver! 

> **mikewhatever said:**
> 
I have no idea what you mean by 'slow internet'. Do sites load slowly? Is it an issue with torrents? Does it take ages to connect?
Downloading like a turtle! It  will be an issue of torrents in the future believe me! It takes ages to download! 
> **mikewhatever said:**
> 
Assuming 8600gt is your nvidia graphics card, I think the driver for it is not included because it may be too new. Get the appropriate driver from nvidia and manually install it.
How do I  manually install it?

**[COLOR="DarkOrange"]UPDATE:[/COLOR]**
I downloaded the driver in Linux! 
double clicked it
But it gives me the error 
Could not open the file /home/kris2pe/Desktop/NV&#8230;ux-x86-100.14.19-pkg1.run.
I wonder why they can't just make simple & install procedure! I just don't get that! Why does everything Linux have to be so damn hard!

---

### Post by jviscosi on 2007-09-20
> **kris2pe said:**
> Internet is SLOOW!

Could be a lot of things.  Try going to Broadband Reports and running the speed test and see what it reports as your speed ([http://www.dslreports.com/stest](http://www.dslreports.com/stest)).  NOTE:  Java or Flash required.

I always like to run a traceroute when looking at connectivity issues.  You may need to install the traceroute package first (**sudo apt-get install traceroute** from a terminal).  Once installed, you can just do **traceroute <TARGET>** from a terminal, e.g., **traceroute ubuntuforums.org**, and you will see the path your packets are taking and if there are any delays or timeouts along the way.  It would be interesting to compare the results to a traceroute run to the same target from Windows (**tracert <TARGET>**) and see if the paths are different.

> **kris2pe said:**
> How do I  manually install it?

I used to download the nVidia drivers from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) and compile them, but lately I've just been using envy, which does all the work itself.  It looks up your graphics card, obtains the driver, downloads any necessary packages, and then compiles and installs.  You can get envy here:  [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html).

If you decide to use envy, and you previously installed the nVidia driver from the repositories, I'd suggest removing that driver first.  Otherwise it seems like every kernel upgrade hoses the driver and you have to run envy again.  That was my experience, anyway.

---

### Post by dpar on 2007-09-20
> R U insinuating that I'm LAZY? Tell u what first Ubuntu has fix some of old issues b4 even release new once. I'm sorry the problems in Edgy still plagues Feisty. Although there are barely noticeable improvements, in a neophyte perspective. It would be nice not to do anything that I usually do! But lets face it! Its plague w/ problems! That so many user are suffering w/! Its got potential but the developer always seems to fall on deafs ear! Thank GOD for dual boot & XP! So while I wait for another 24 hrs for you to figure things out I will zip my way to productivity if you don't mind!
BACK TO XP !


Why are you even using Linux?
If you want to see 'improvements' in a new distro, try Vista:lolflag:

Then go to microsoft and complain. They will just fall all over themselves to try to help you.

---

### Post by rsambuca on 2007-09-20
Sometimes in order to help people, they have to first want to receive help, and be willing to help themselves.  

Frankly, I have no patience for this sort of abrasive, pompous attitude.  Good luck with those problems, by the way.

---

### Post by kris2pe on 2007-09-20
Ok I tried going here: 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Got lost & ended up here
[http://albertomilone.com/latest_nvidia_udsf_feisty.html](http://albertomilone.com/latest_nvidia_udsf_feisty.html)
after following the step all I saw was a black screen after restart! 
> **dpar said:**
> Why are you even using Linux?
If you want to see 'improvements' in a new distro, try Vista:lolflag:
Then go to microsoft and complain. They will just fall all over themselves to try to help you.
I have agree on that one
But I do get better help on other website on XP problems that here!
That for sure! 
> **rsambuca said:**
> Sometimes in order to help people, they have to first want to receive help, and be willing to help themselves.  

Frankly, I have no patience for this sort of abrasive, pompous attitude.  Good luck with those problems, by the way.
Oh did I hurt wittle feelings! :lolflag:
I will! Even if I were nice or not it doesn't change one bit! In fact your weren't the least bit interested in helping anyways! Ur just power tripping at this point in time! OHH Look at me I'm so powerful!

---

### Post by jviscosi on 2007-09-20
> **kris2pe said:**
> Ok I tried going here: 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Got lost & ended up here
[http://albertomilone.com/latest_nvidia_udsf_feisty.html](http://albertomilone.com/latest_nvidia_udsf_feisty.html)
after following the step all I saw was a black screen after restart! 


The direct link to download the current version of envy is [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu11_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu11_all.deb).  It's on the [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) page.  I'm not sure how you ended up on the nVidia driver page but that seems to be for doing it manually, which as I understand it is not what you want to do.

---

### Post by kris2pe on 2007-09-20
Well as you can see I'm not good at this!
But anyways is there a way for me to get the latest updated or make slip stream of ubuntu?
Where I can download all the updates & just burn them up? 
I hate  redownload updates!

---

### Post by bapoumba on 2007-09-20
@ kris2pe: please adjust your posting style. You are getting help, many thanks to the ones who chimed in positively. Calm down and stop being harsh on your comments. People at best will ignore your problems, at worse will pick on them and the thread will turn on flames. Then staff will be back.
Cheers!

---

### Post by angryfirelord on 2007-09-20
Write down the following:

Uninstall the nvidia-glx package:
```
sudo apt-get remove nvidia-glx
```
Or if you use the nvidia-glx-new package:
```
sudo apt-get remove nvidia-glx-new
```
Download the nvidia driver to your $HOME directory (that would be /home/your_name)
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run")
Log out and press Ctrl+Alt+F1.
Log in at the prompt.
Type:
```
/etc/init.d/gdm stop
```
Then type:
```
sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run
```
Now run:
```
sudo dpkg-reconfigure xserver-xorg
```
Select nvidia as your driver. You can keep the default settings unless you know what you're doing. This handy curses application will allow you to generate a new xorg file without having to dive into your xorg.conf. It also backs up your old one if something goes wrong.

---

### Post by mikewhatever on 2007-09-20
> R U insinuating that I'm LAZY? Tell u what first Ubuntu has fix some of old issues b4 even release new once. I'm sorry the problems in Edgy still plagues Feisty. Although there are barely noticeable improvements, in a neophyte perspective. It would be nice not to do anything that I usually do! But lets face it! Its plague w/ problems! That so many user are suffering w/! Its got potential but the developer always seems to fall on deafs ear!

No, you are not lazy, you are rude ignorant and ridiculously demanding. Nobody's forced you to use Ubuntu, you also have XP, so stick with it.

> Thank GOD for dual boot & XP! So while I wait for another 24 hrs for you to figure things out I will zip my way to productivity if you don't mind!
BACK TO XP ! 

All or most of the members are not the developers. Once again, XP is a very good OS. Good Luck.

---

### Post by Ripfox on 2007-09-20
Troll

---

### Post by angryfirelord on 2007-09-20
> I wonder why they can't just make simple & install procedure! I just don't get that! Why does everything Linux have to be so damn hard!
Because it's not Windows, simple as that. If you want the idiot-proof, point & click, wizards until your eyes fall out way of computing, use Windows. But don't expect Vista to play nicely with your computer when XP gets the ax.

Be a little more patient and open to other ways of managing your computer. Once you do that, you'll find Ubuntu a dream to use.

---

### Post by dpar on 2007-09-20
> I have agree on that one
But I do get better help on other website on XP problems that here!
That for sure! 

Of course......this is a LINUX forum.

> Troll

I'd have to agree

---

### Post by tlacuache on 2007-09-20
I had the same problem with the internet being slow. I ended up disabling the IPV6 module and it fixed the problem for me.

You might want to give it a try.

See: 

[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

-SG

---

### Post by kris2pe on 2007-09-20
Ok I reformat my ubuntu & executed the envy.deb file.
But after restart it says that my xserve or gui is not functioning well!

---

### Post by Rasitiln on 2007-09-20
> **rsambuca said:**
> Sometimes in order to help people, they have to first want to receive help, and be willing to help themselves.  

Frankly, I have no patience for this sort of abrasive, pompous attitude.  Good luck with those problems, by the way.

QFT go back to windows, they are paid to help you we are not.

---

### Post by strabes on 2007-09-20
This guy is obviously a troll. Anyway, he should try installing windows on a laptop and see what works out of the box. (Hint: The answer is "nothing.") People think that linux has bad hardware support but in reality windows supports **nothing** out of the box.

---

### Post by g2g591 on 2007-09-20
!!troll Alert!! see [http://ubuntuforums.org/showthread.php?t=179139&highlight=anatomy+of+troll](http://ubuntuforums.org/showthread.php?t=179139&highlight=anatomy+of+troll)
edit:darn someone still beat me too it

---

### Post by kris2pe on 2007-09-21
Ah that so sweet of you guys! 
Believe it or not! I got these problems & they are real! 
Show you! How things are on Ubuntuforums!

---

### Post by kris2pe on 2007-09-21
> **strabes said:**
> This guy is obviously a troll. Anyway, he should try installing windows on a laptop and see what works out of the box. (Hint: The answer is "nothing.") People think that linux has bad hardware support but in reality windows supports **nothing** out of the box.

Well I did! Work well if you slip stream everything! Guess what try doing w/ Ubuntu! See if all the features like energy saving works on it!

---

### Post by bapoumba on 2007-09-21
Okay, closing the thread.

---

