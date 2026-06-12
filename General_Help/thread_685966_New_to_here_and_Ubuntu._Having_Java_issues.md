---
title: "New to here and Ubuntu. Having Java issues"
date: 2008-02-02
forum: General Help
---

### Post by jsharptooth91 on 2008-02-02
Hello all!!! I am new here and i have just installed Ubuntu 7.10.  Everything seems to be working fine except my Java. I have it installed (i think). When i go to some sites it will load, and others it will not. Any ideals on what could be going on.  Thanks

---

### Post by ubuntu-freak on 2008-02-02
How did you install it? Use my [how-to](http://ubuntuforums.org/showthread.php?t=661833) and get everything multimedia related working. If you still have problems with java, try removing all the java6 packages in System>Administration>Synaptic (search for sun java) then install java5 jre, plugin and fonts.
 
Nathan

---

### Post by jsharptooth91 on 2008-02-03
I found a guide online. Followed the instructions on java.com. I browsed threw your guide and thier is nothing about java. So i see that you said jre6 should be removed and jre5 should be installed. Why down grade the version to 5? is their issues with 6?

---

### Post by ubuntu-freak on 2008-02-03
You don't need to install it from their site. The ubuntu-restricted-extras package contains java and much more. Also, my how-to mentions java. I wouldn't forget something like java anyway.
 
Some have had problems with java6 yeah. Just experiment. 
 
Enable the medibuntu repo and install all of the essential packages. It's all detailed in my [how-to](http://ubuntuforums.org/showthread.php?t=661833).
 
Nathan

---

### Post by meho_r on 2008-02-03
Alternatively, you could try IcedTea java package. If so, remove sun java prior to install. For me, it works just fine (even on 64bit Ubuntu and 64bit Firefox;))

---

### Post by ubuntu-freak on 2008-02-03
> **meho_r said:**
> Alternatively, you could try IcedTea java package. If so, remove sun java prior to install. For me, it works just fine (even on 64bit Ubuntu and 64bit Firefox;))

 
Really? Might add that to my how-to. So 64-bit users are only missing a 64-bit adobe flash plugin now?
 
I'm gonna look into that IcedTea.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-03
Saying that, 32-bit sun java works fine on a 64-bit system, so long as you have the 32-bit Firefox. Plus sun java 7 will include a 64-bit version.
 
Nathan

---

### Post by jsharptooth91 on 2008-02-03
Im kinda new at this stuff. So how would i unstill java 6?

---

### Post by ubuntu-freak on 2008-02-03
Where did you install it from? We should try and get java6 working. Try installing my essential packages from part 1 of the how-to, or have you already?. Then in the terminal
 
sudo update-alternatives --config java  

Pick the java6 version from /usr/lib.
 
Close your browser and reboot (extras includes a lot of packages).
 
Nathan

---

### Post by jsharptooth91 on 2008-02-03
let me give it a try.. just got off work so i will check it out....

---

### Post by jsharptooth91 on 2008-02-03
So i followed your how to, got all that installed. Then i unstalled the java6u3 that i downloaded off the website. I installed the ice tea version and it looks to be working.

---

### Post by jsharptooth91 on 2008-02-03
When i go to the java site, it says i have the latest version. But when i go to load an app that requires java. at the bottom it says applet not intialized.. what else could i be missing?

---

### Post by ubuntu-freak on 2008-02-04
> **jsharptooth91 said:**
> When i go to the java site, it says i have the latest version. But when i go to load an app that requires java. at the bottom it says applet not intialized.. what else could i be missing?

 
Why did you install IcedTea? Do you have the 64-bit Ubuntu? You have two java's now if you installed the restricted-extras package (contains Sun Java, codecs. MS fonts and lots more). You only need Sun Java. Then try Yahoo! Games as a test site. Always works for me. Remove IcedTea. If java6 doesn't work on other sites you need, remove java6 in Synaptic (search sun java)
and install sun java5 jre, plugin and fonts. Synaptic is in System>Administration. Java6 works with Yahoo! Games, so don't remove it too quick. Use that command I posted earlier and make sure Ubuntu is trying to use java6 in /usr/lib.


Nathan

---

### Post by ubuntu-freak on 2008-02-04
I told you before that the extras package includes Sun Java.

---

### Post by ubuntu-freak on 2008-02-04
Sounded a bit frustrated didn't I? Just want you to get it working. 

Hope it goes well anyway.
 
Nathan

---

