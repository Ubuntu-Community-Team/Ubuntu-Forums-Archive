---
title: "Java in Feisty Fawn"
date: 2007-04-19
forum: General Help
---

### Post by winter_mute on 2007-04-19
I updated my desktop to Feisty Fawn a couple days back, with RC1, and it's wonderful.  I have a few complaints (Beryl/Compiz support is f'd up) and one major, huge complain - Java.  I'm taking a CS class right now that's programming in Java, and mainly dealing with GUI's.  And for some reason, my edgy laptop and my formly edgy desktop did Java just fine.  But when I try to launch programs that I know run well, and have been tested on Edgy, OS X, and Windows, I keep getting errors in Eclipse.  Is there something special that I need to do for Java 5?  Until I get that fixed, and until some good guides for Beryl come out, I think I'll be sticking with Edgy on my boxes.  Sorry, but I love stability and Java that actually works.  Maybe in a month or two I'll give Feisty another try, but until then I'll just hope for a bugfix.

---

### Post by vionescu on 2007-04-19
Make sure you have sun-java5-jdk installed. You can use the following command to make it the default Java:

$ sudo update-java-alternatives -s java-1.5.0-sun

In eclipse add it to the list of JDKs and make it default: Window->Preferneces->Java->Installed JREs. You can find it in /usr/lib/jvm/java-1.5.0-sun.

Hope this helps.

Edit: update-java-alternatives needs root rights...

---

### Post by Gannin on 2007-04-19
You could also just try downloading and manually installing Java from Sun's website, then make the appropriate symlinks in the /usr/bin directory.  That's what I do.

---

### Post by eyelessfade on 2007-04-19
/etc/eclipse/java_home must also be updated with the right path at the top. To bad this isn't done automatic.

And for some reason eclipse have a hard dependencies on java-gcj. Maybe its the sun-java package which is the problem. It should be a part of the java2-runtime package

---

