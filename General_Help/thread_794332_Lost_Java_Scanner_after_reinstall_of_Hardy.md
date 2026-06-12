---
title: "Lost Java Scanner after reinstall of Hardy"
date: 2008-05-14
forum: General Help
---

### Post by Guest_Jim_* on 2008-05-14
I had to reinstall Hardy today but previously I had upgraded from Gutsy. Eclipse had no problem with using the Scanner class in Gutsy or after I upgraded, but now that I've reinstalled it won't work. It is acting like I don't have a JDK that has Scanner in it but I have version 6.0 which should have Scanner.
Any ideas?

---

### Post by Guest_Jim_* on 2008-05-15
Not sure if this is related or not, but I also have Stellarium and Celestia installed and neither of them want to work either. They startup but shutdown after about ten seconds or so.

---

### Post by ludovicc on 2008-05-17
Check that you are actually using Java 6. I had an issue where gij (the GNU version of Java, still at version 1.5) was installed by some other program, and became the default Java for the system.

java -version should return java version "1.6.0_06"

If it does not, then you need to reconfigure your defaults:

sudo update-java-alternatives -s java-6-sun

Hope this helps,
Ludovic

---

### Post by Guest_Jim_* on 2008-05-17
I saw that update-alternatives command in another thread yesterday and it didn't help, but I will check on the version as soon as I can. My desktop has both XP and Ubuntu on it and currently I'm doing something in XP.
I figured out what was wrong with Stellarium, but not Celestia. It would seem that Stellarium doesn't like something about the Compiz effects. I tried going through and just turning ones off to find the specific problem, but Stellarium would only consistently work with the no effects options.

---

### Post by jcwmoore on 2008-05-17
It looks like you are using the GNU version of java. I have worked with it a little before and I remember that there is no scanner class.  The GNU version of java does not have scanner implemented in its libraries.  Try what is suggested above and you should be fine.

---

### Post by Guest_Jim_* on 2008-05-17
It says I have java version 1.6.0_06 but still no Scanner.
I figured it out. In Eclipse you can tell it which compiler to use and which JRE's are installed. The only JRE it saw installed was 1.5, so I added the 1.6.0.06 to the list and that took care of it. Not I've just got Celestia to figure out. Thank you both.

---

