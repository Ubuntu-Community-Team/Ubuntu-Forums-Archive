---
title: "Make own live cd."
date: 2008-01-10
forum: General Help
---

### Post by diwas on 2008-01-10
Well being a dial up modem access, i have to stay in front of the monitor for hours even to fetch a small packgae. So what iam thinking is to make my own live cd so that if the system fails at any point of time, i would have that cd (which is my customized) handy and i can install all the packages i downloaded. 
Is this possible? If not, what can i do to make my software make smthg like backup so that i dont have to re-download it. 
Does sbackup help?
And the last question, when the packages are downloaded where do they reside? And are they deleted after the installation?

---

### Post by overdrank on 2008-01-10
> **diwas said:**
> Well being a dial up modem access, i have to stay in front of the monitor for hours even to fetch a small packgae. So what iam thinking is to make my own live cd so that if the system fails at any point of time, i would have that cd (which is my customized) handy and i can install all the packages i downloaded. 
Is this possible? If not, what can i do to make my software make smthg like backup so that i dont have to re-download it. 
Does sbackup help?
And the last question, when the packages are downloaded where do they reside? And are they deleted after the installation?


Hi and you may find theses interesting 
[http://ubuntuforums.org/showthread.php?t=621673](http://ubuntuforums.org/showthread.php?t=621673)
[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

---

### Post by wolfen69 on 2008-01-10
Reconstructor [http://lifehacker.com/software/featured-linux-download/roll-your-own-ubuntu-live-cd-with-reconstructor-276092.php](http://lifehacker.com/software/featured-linux-download/roll-your-own-ubuntu-live-cd-with-reconstructor-276092.php)

however, the site is down right now. try later.

---

### Post by twright on 2008-01-10
i have actually been thinking of doing the same myself although it might just be simpler to just use aptoncd :)  (it can automatically backup any package you have ever installed to a CD so that if you need to install it again you use the version on the CD)

---

### Post by GavinZac on 2008-01-10
you could just gather the .deb files and keep them on a cd.

packages are downloaded to the apt archive and only deleted from this archive when you tell them to be.

---

### Post by diwas on 2008-01-11
Saving the packages sounds easy. So where is the apt archive?

---

### Post by diwas on 2008-01-11
I mean where are all the packages installed?? Can you gimme the path please. Thank you.

---

### Post by diwas on 2008-01-11
Is it /var/cache/apt/archives?? Well it is i guess!! Thanks a lot for your help!

---

### Post by soxs on 2008-01-11
You're right. Simply copy all packages (only the packages) to some sort of cd/dvd and you just have to copy it back or if you're lucky, gutsy will identfy your cd/dvd as package medium (which doesn't work for me)

---

### Post by diwas on 2008-01-11
Yes, thank you guys!!! I got that.
Goin completely off the topic, i cannot change my mouse theme..i like the glass theme but i dont knw where it was last time. Its in that System>Preference>Mouse isnt it? But i dont have any mouse theme there only 2 tabs : Button and Motion. Where is that theme?

---

### Post by gregcss on 2008-01-11
> **wolfen69 said:**
> Reconstructor [http://lifehacker.com/software/featured-linux-download/roll-your-own-ubuntu-live-cd-with-reconstructor-276092.php](http://lifehacker.com/software/featured-linux-download/roll-your-own-ubuntu-live-cd-with-reconstructor-276092.php)

however, the site is down right now. try later.


I dont think Reconstructor works with x64. I can burn the iso but get check sum error when i boot to it.

---

### Post by twright on 2008-01-11
hi

you can change you mouse theme from system->preferences->appearance, click on customize and the pointer tab

---

### Post by diwas on 2008-01-12
Thank you for the mouse theme, but i have a weird problem. I went to that place and changed the mouse theme. It doesnt change but when i take my mouse to Firefox browser it is what i changed but again when i take to places like desktop, the default mouse theme appears. Whats the problem?

---

### Post by Yookji on 2008-01-12
I think it's in System>Preferences>Appearence then customize theme or something like that.

---

### Post by diwas on 2008-01-13
But what abt the mouse problem?

---

