---
title: "OpenOffice died after I installed a new version of Java"
date: 2008-04-09
forum: General Help
---

### Post by wheremyarm on 2008-04-09
In order to get Frostwire to work, I downloaded the newest version of Java from java.com and installed it by using the self-extracting file to /usr/bin/java.  Now Frostwire works fine, but OpenOffice just shows the splash screen indefinately.  I've tried uninstalling and reinstalling all of OO via Synaptic, and the problem persists.  How'd I broke it?

---

### Post by jken146 on 2008-04-09
You shouldn't get Java from java.com -- use the packages in the Ubuntu repositories.  Install the packages **sun-java6-bin** and **sun-java6-jre** in Synaptic.

---

### Post by wheremyarm on 2008-04-09
Alright, tried that with no sucess.  I removed the folder that extracted when I used the .bin I got from java.com, and isntalled the packages you specified with Synaptic, and now neither Frostwire or OpenOffice work. :(  If this helps, there's a file in /usr/lib/frostwire called runFrostwire.sh that when run outputs this:

```
Starting FrostWire...
Java exec found in PATH. Verifying...
```

And from there it never does anything more.  I can't find a way to tell if OO is finding the JRE or not, but it looks like Frostwire is and it's just not working for some reason.  What else could be wrong?

---

### Post by FuturePilot on 2008-04-09
Try making sure you have Java6 set as the system default JRE
```
sudo update-alternatives --config java 
```
Select Java6 from the list.

---

### Post by wheremyarm on 2008-04-09
Aha!  That fixed Forstwire, but OO still does the exact same thing.  However, I do have new information.  When I'm watching the System Monitor while OO is trying to start, it spawns a process called 'javaldx'.  If I force end this process, OO starts and operates normally, but it won't until I end javaldx.

---

### Post by FuturePilot on 2008-04-09
Hmmm. Maybe it's a setting in OO somewhere. Let's try this
```
mv .openoffice.org2 .openoffice.org2_old
```
That will rename your OO profile folder to .openoffice.org2_old and will force OO to create a new one when you start it.

---

### Post by wheremyarm on 2008-04-09
No effect. :( Any other suggestions?

(By the way, I appreciate the fast responses I've gotten so far, thanks alot! :) )

---

