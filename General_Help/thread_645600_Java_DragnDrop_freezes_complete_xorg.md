---
title: "Java DragnDrop freezes complete xorg"
date: 2007-12-20
forum: General Help
---

### Post by heinrich on 2007-12-20
Hi,

I have a very critical problem with java and ubuntu 7.10
Each time i want to use Drag'n Drop in Java applications, the complete xserver is freezing. The music is playing as normal, and the mouse pointer can be moved. But no window can be activated and everything is blocked.
Even the switch to tty1 does not work anymore.
It happens with Java 1.5 Update 13 as well with Java 1.6

The only solution to not reboot the maschine, is to login per ssh and kill the java process. Afterwards everything is like before.
Does anyone have an idea or the same problem? 
The issue is only on my maschine
kernel  2.6.22-14-generic #1 SMP 

I wasn't able to get any usefull stacktrace. strace, gdb etc resulted in no usefull output.

If no one nows it, where can i get support for this?
I don't know if this is a bug in the JVM....

---

### Post by djb61230 on 2008-03-17
We are seeing this same behavior but have a few more things to add to the puzzle, or maybe make the puzzle more puzzling!

We see this freeze but only when running our application in an executable jar.  If we run the same application outside of the executable jar, drag and drop works fine.

The kicker is then after running it outside of the executable jar once and doing at least one drag and drop operation, the executable jar can be run and it will not freeze X.  It will work properly for the duration of that X session.  Log out of X and the executable jar will freeze again.

heinrich, have you solved this problem?

---

### Post by gomar on 2008-04-10
> **djb61230 said:**
> We are seeing this same behavior but have a few more things to add to the puzzle, or maybe make the puzzle more puzzling!

We see this freeze but only when running our application in an executable jar.  If we run the same application outside of the executable jar, drag and drop works fine.

The kicker is then after running it outside of the executable jar once and doing at least one drag and drop operation, the executable jar can be run and it will not freeze X.  It will work properly for the duration of that X session.  Log out of X and the executable jar will freeze again.

heinrich, have you solved this problem?

I can second this observation fully.  We've first come to notice the DND hang issue with Ubunutu running within VMware, then with Windows inside a VMware VM also, and finally with a native SuSE 10 (?) installation.  I don't think the issue is distribution-dependent.  At least the JAR vs. no JAR behavior proves the application's innocence. ;-)

Did you find a solution or work-around?  Otherwise, have you filed a bug report somewhere?

I'm currently thinking about whether it would be possible to run a JAR-less mini-application programmatically performing a DND operation prior to the actual application, but I'm not yet sure whether that's feasible.


Marco

---

### Post by gomar on 2008-04-15
In case anyone is interested, we've found an acceptable work-around in creating a "Runner" class taking the fully-qualified name of the actual application class as an argument (along with any actual arguments of the application) and running that class, passing it any further arguments. If the Runner class is run directly (outside a JAR), this works even if the actual application continues to reside in a JAR. :)

Marco

---

### Post by djb61230 on 2008-04-21
We just realized we can work around the bug also by not using the splash screen.  Our application is a custom one so we stumbled on the fact that if we did not configure a splash screen property in the MANIFEST.MF (SplashScreen-Image) then the freeze does not happen.

For us it simply was generating a jar file without the property.  I wanted to see if I could manually edit a jar if it could be fixed that way for folks who are just using an app.

I tried to edit the META-INF/MANIFEST.MF to take it out with a text editor but was not able to get it to work.  First I extracted it with "jar xf" and then updated with  "jar uf"  But then running the executable jar complained of a corrupted file.  I didn't spend a lot of time on it but I would think there is a way to do it.

Just wanted to let you all know that the splash screen code seems to be the culprit.  Gomar essentially bypassed the splash screen his way since the JVM will not search around for the splash screen in other jars.

---

### Post by gomar on 2008-04-21
> **djb61230 said:**
> Just wanted to let you all know that the splash screen code seems to be the culprit.  Gomar essentially bypassed the splash screen his way since the JVM will not search around for the splash screen in other jars.

Indeed: We're using a splash screen, too.  As it happens, today I noticed an apparent recurrence of the issue even with the workaround which left me with no other option than to operate without an application JAR.  What I had done in between the introduction of the runner class and this recurrence of the issue was to add the splash screen lost by not executing the JAR via the corresponding command line option ("-splash:FILE").

So the splash screen is indeed the culprit, no matter whether by JAR or by command line option.  Have you filed a bug report yet?


Marco

---

### Post by djb61230 on 2008-04-21
No, I didn't file a bug report.  Actually haven't ever done that, is it up at Sun?

---

