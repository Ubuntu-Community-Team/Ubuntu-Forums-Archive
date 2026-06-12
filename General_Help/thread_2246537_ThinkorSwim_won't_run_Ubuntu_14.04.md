---
title: "ThinkorSwim won't run Ubuntu 14.04"
date: 2014-10-01
forum: General Help
---

### Post by climbermel on 2014-10-01
I have a fresh install of 14.04 LTS 64bit.  Everything has been working except when I installed Thinkorswim.
I got it to install fine (so it seemed) but when I launch it, it goes to the Installing updates... and hangs there forever.

I have the latest java install, which from some posts makes it sound like that may be a problem. (java version "1.8.0_20")

I tried running it from a shell using sudo sh ./thinkorswim

The message: Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=128m; support was removed in 8.0
is displayed while the ToS widow is hung.  If I ctrl c it goes back to the prompt and the app widow is gone.

I could look at switching back to java 7, but was hoping to find someone that has a fix. Could the .sh file be edited or does it just not work with 8.0???

---

### Post by hooverist on 2014-10-07
I am new to Linux - testing out Ubuntu 14.04, Mint 17 and Zorin 9 for  three weeks finally got ThinkorSwim working. From what I have been able  to determine is it worked fine on earlier versions of Ubuntu as a Java  program - TDameritrade has made some changes in the past few years and  this is no longer the case. I have tried the majority of the suggestions  offered on this and other boards with no success. For me - I would get  the installing updates screen and it would hang there (white color) then  starting again same screen, but black color. Never would get to log on  screen. Tried Wine with exe file - it didn't work either . . . BUT THEN  tried PLAYONLINUX it's a little glittchy, but runs pretty good on all  three versions. Best on Ubuntu and plus side Charts on my second monitor  are better resolution than Windows 7 - two days now - I have not fired  up Windows at all.

---

### Post by climbermel on 2014-10-08
So how did you get ThinkorSwim working?  What version of java are you running?

---

### Post by hooverist on 2014-10-23
[QUOTE=climbermel;13138942]So how did you get ThinkorSwim working?  What version of java are you running?

Sorry for the delay in getting back to you - I haven't looked in on this message board until today and I hope your already up and running. I am not really sure which version of Java - PlayonLinux (through) Wine would use or if they might utilize the Java packages installed in Linux. All I can tell you is that I did install several versions of Java 6 and at least one of 7 into Wine using the exe files from adobe - if PlayonLinux is using the Java installed in Wine - I would lean towards, newer is better. It is running for me in all three versions of Linux and I doubt that I tried things like java6u1932.exe and java6u31.exe in all three versions. Sorry - bottom line is I don't know. The PlayonLinux package was available in all three version's Software Center installers.

---

### Post by Oliver_Oberdorf on 2015-01-09
In case anyone is still looking for a solution.  I had the exact symptoms described with ToS on Ubuntu 14.04.  Then I reinstalled it, but this time I selected "for this user only" instead of installing for all users.  This seems to work fine.

I suspect in the "for everyone" case, it is trying to write to the application install folder and does not have permission.  Not my favorite solution, but it works.

---

### Post by Chas S on 2015-01-30
Sadly, I've done this (for various unrelated reasons) a few times now.

First:
Read and Try to use the following install instructions, courtesy of Emmett George:
[http://mediaserver.thinkorswim.com/support/ubuntuhowto.pdf](http://mediaserver.thinkorswim.com/support/ubuntuhowto.pdf)

Best Hints:
1. The Java configuration commands are Very rewarding (middle of the pdf page).
2. Install Oracle Java, NOT the Linux version. I
3.  I have been successful installing version 1.7.0_72 (Java 7)--there WAS a  reported problem using higher versions, though it may since have been  solved.
4. I no longer try to install other Java versions, though  I've updated to version 1.7.0_76 with absolutely no problem; and I  Believe I may once have successfully configured Java 7 without having to  uninstall openjava or java8.

(I spent about a week in Java hell trying to get other Java versions to work, having installed those 3 different versions)

Should  figure on taking about an 30min-hour to sort out the instructions,  depending on how proficient and compulsive-obsessive you are.
If you,  too, have several versions of Java installed, try first just using the  Java configuration commands from the pdf for Java version 7 (not 6)
and see what you get--you might just be done without having to uninstall anything--save yourself some time.
And come to think of it, I DO always select "for this user only" for the install.

BTW,  are you installing onto a HDD or SSD, and do you or ANYONE know Which  Is Preferrable (i.e., would it wear out the SSD prematurely, or safely  make TOS run more efficiently)? I know it's off thread, but thought  someone might just KNOW the answer and reply without having to create a  separate thread--which I'm also happy to do.


Good Luck and let us know how it goes!

---

### Post by enaction on 2015-05-30
I got thinkorswim to run on ubuntu 64bit 14.04 by using the oracle java 7 install instructions found here:  [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html).

---

### Post by quietriotr on 2016-04-22
> **Oliver_Oberdorf said:**
> In case anyone is still looking for a solution.  I had the exact symptoms described with ToS on Ubuntu 14.04.  Then I reinstalled it, but this time I selected "for this user only" instead of installing for all users.  This seems to work fine.

I suspect in the "for everyone" case, it is trying to write to the application install folder and does not have permission.  Not my favorite solution, but it works.

This worked for me after hours of trying many other things.

---

### Post by Bucky Ball on 2016-04-22
Welcome and glad you found a solution. Time for this old thread to go back to sleep.

*Thread closed. *

---

