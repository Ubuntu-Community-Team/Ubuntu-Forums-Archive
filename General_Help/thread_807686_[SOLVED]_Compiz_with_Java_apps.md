---
title: "[SOLVED] Compiz with Java apps"
date: 2008-05-26
forum: General Help
---

### Post by dysonsphere23 on 2008-05-26
Hi,

I have been trying to get Cmap tools to work with desktop effects enabled, but when cmap opens there is only an empty window.

I then tried to run the open source mind mapping tool "free mind". With this I get a visual window but cannot resize it or scroll anywhere that was not seen in the original window frame.

I am assuming this is some problem with java interacting with compiz as when I open these apps without desktop effects enabled there is no problem.

Running Ubuntu 7.10

Thanks in advance to anyone who thinks up a solution.

---

### Post by CameO73 on 2008-05-26
I've had similar problems (especially using Java applets in FF). My solution was to use the latest Sun beta JVM ([Java SE 6 Update 10 beta]("http://java.sun.com/javase/downloads/ea/6u10/6u10beta.jsp")). You have to know what you're doing, though! Since I'm only using this beta for applets, I just created a link manually to  libjavaplugin_oji.so in ~/.mozilla/plugins.

You could force the application to use the installed beta version; usually by changing a configuration option or changing the startup script.

Not all Java applications have these problems, btw. Azureus and Eclipse work fine in Compiz ... it has probably something to do with the interface components used (both Azureus and Eclipse use SWT, my problematic applets use Swing).

---

### Post by dysonsphere23 on 2008-05-27
Thanks for the tips.  Don't think I quite know enough to dive into that right now.  If anyone can give a step by step that would be great.  For now I will live with it until such time that I can afford to "mess" with my system or the beta fix becomes the next Java release.

---

### Post by dysonsphere23 on 2008-05-27
Well it would seem that I now know enough:

I:

1. downloaded the .bin file for the Java SE 6 Update 10 beta
2. extracted the file
3. moved the resulting folder into the cmaptools folder
4. deleted the "jre" folder in cmaptools and renamed the beta one "jre"

So far cmap tools works great as do my other java apps that worked before.

Thanks again CameO73 for getting me on track.

---

### Post by yacine on 2008-11-08
Great! Thanks for your post! It worked for me.

---

### Post by leoperbo on 2009-01-26
> **dysonsphere23 said:**
> Well it would seem that I now know enough:

I:

1. downloaded the .bin file for the Java SE 6 Update 10 beta
2. extracted the file
3. moved the resulting folder into the cmaptools folder
4. deleted the "jre" folder in cmaptools and renamed the beta one "jre"

So far cmap tools works great as do my other java apps that worked before.

Thanks again CameO73 for getting me on track.

I was looking for that tip since one year ago, THANK YOU!

---

### Post by khughitt on 2009-09-23
Anyone else run into problems with Swing applications in Jaunty?

I have one machine where Swing application windows are completely grayed out if desktop effects are enabled when the application is launched. It looks like the issue has been closed on Sun's end ([http://bugs.sun.com/view_bug.do?bug_id=6632124](http://bugs.sun.com/view_bug.do?bug_id=6632124)), however, the JRE on the machine is completely up to date (1.6.0_16), and the problem still persists.

It's easy enough to disable compiz, but this isn't the most desirable solution.

---

