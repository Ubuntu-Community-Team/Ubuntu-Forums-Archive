---
title: "Im new. A bunch of questions needed to be answered"
date: 2007-10-22
forum: General Help
---

### Post by ashaiba on 2007-10-22
Ok. I have use multiple distributions of Linux and most people I know recomend Ubuntu... I'm not a huge linux user, but my windows has been pisssing me off for too long, so im leaving that s**t for good. I am currecntly using mac and linux..but i cant get the grasp of linux....


Question 1. How do i install my video card?!? and how do i turn on dual moniters on ubuntu. My video card is "nvidia, evga e-GeForce 7600GT 256mb"

Question 2. My ubuntu came with absolutly NO CODECS, I can't play MP3, music, videos, dvd, NOTHING... shouldn't it come with the basics atleast??? can someone help me solve this problem

Question 3. How in the world do i install Beryl!? whats with all the coding just for one program, isnt there a simple exe of some sort??? any help?

I have more questions but can't think of it....

PS. PLease reply, don't betray me like all the other forums where no1 replies to my post and leaves me hanging with a waste of time and no information

-thanks

---

### Post by drs305 on 2007-10-22
First, welcome to ubuntu. You will find that the readers of this forum are extremely helpful if you ask your questions politely and provide the necessary information.

I still consider myself a newbie (less than a year) but I've used edgy, feisty and now gutsy. The answers to your questions will depend on which version of ubuntu you will use. Please provide that information so the experts can help you. (version and processor)

---

### Post by schneider707 on 2007-10-22
Ok, I'm really new too but heres what I've found out so far that might help you.

1. Your video card should just work. Now if you want 3d support or anything advanced (like dual monitors), you need to install the Nvidia drivers. Easiest way is using a program called Envy (click [here]("http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu8_all.deb") for link). It auto detects the card and finds the right drivers for ya, installs them and configures them.

2. Hmmm, not really sure about this since mine was able to do all of that off the bat. The only thing I couldn't do at first was watch videos from YouTube, but that was cause I forgot to install flash. Wait for someone else to answer on that one.

3. You should actually be looking for something called Compiz-Fusion instead. I believe it is the Beryl and Compiz teams pushed together...but thats neither here nor there. Basically, follow this link [here]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty") if you wanna install it using Fiesty. Ill see if I can find another link if you are using Gutsy. Make sure that you follow those instructions to the letter...also the nvidia drivers need to be installed before you install Compiz because a lot of the functions won't work without 3D support. 

Edit. I believe [this]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion") would be the tutorial for setting up Compiz-Fusion on Gutsy Gibbon

---

### Post by MadhavS on 2007-10-22
I can give you a few answers, assuming you are using Ubuntu 7.10 Gutsy Gibbon:

? 1: After logging in for the first time, an icon should pop up in the top right hand corner that says something like "Restricted Drivers in Use". After clicking on that icon and entering your password in the pop-up box, you can check the unchecked box for the driver, and it will install (it takes some time). I'm using the same GeForce 7600GT, so things should work out fine :)

To use two monitors, in the top right corner, System->Administration->Screen and Graphics. You can do it there.

? 3:In Ubuntu, things like installing Beryl are pretty much done from the command line. However, I personally believe that compiz fusion is much better. It comes with Gutsy, but to configure it even more, type this into you terminal:

```
sudo apt-get install compizconfig-settings-manager
```

After typing that in, press enter, type in your password, and press enter again. Once this is done, you should have a new item in your System -> Preferences called "Advance Desktop Effects Settings". Play around with that and adjust to your whim.

Also, .exe files cannot run in Ubuntu unless you are using different kind of program to run it.

Hope that helped!:)

---

### Post by upfwnv03 on 2007-10-22
Question 1 - Try the Multimedia & Video forum. I noticed a sticky post HOWTO on Nvidia cards.

Question 2 - Might I suggest this link [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)
I understand it's for Feisty but I used it with Gutsy without a problem.

Question 3 - Sorry no help here, not using it myself. Although some Desktop effects are enabled by default in Gutsy.

What version of Ubuntu are you using ?

---

### Post by pashashome on 2007-10-22
You asked: > Question 2. My ubuntu came with absolutly NO CODECS, I can't play MP3, music, videos, dvd, NOTHING... shouldn't it come with the basics atleast??? can someone help me solve this problem


If you are using 7.10 go to System/Administration/Synaptic Package Manager: click on search and search for ubuntu-restricted-extras. Install that for your codec needs. If you are using some other version of ubuntu or some other distro then use the search engine of your choice and look for the information for that version or distro. 

Hope that is what you are looking for.

---

