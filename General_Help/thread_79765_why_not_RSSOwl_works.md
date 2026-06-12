---
title: "why not RSSOwl works ?"
date: 2005-10-20
forum: General Help
---

### Post by weixiao.fan on 2005-10-20
I install RSSOwl follow [www.ubuntuguide.org](www.ubuntuguide.org) but when I start it I just can see the splash picture. why not it works ?

---

### Post by weixiao.fan on 2005-10-21
who can help me ...:(

---

### Post by RAOF on 2005-10-21
It would be much easier to help you with some more information.  Specifically, can you run RSSOwl from a terminal (if you followed those instructions, you should be able to just go "runRSSOwl.sh") and see whether there are any errors reported?

Also, it seems that RSSOwl is a java app.  Have you built and installed the Sun Java runtime?  There's a howto for that [here]("http://www.ubuntuforums.org/showthread.php?t=76735&highlight=java+package+howto").

That is probably the problem.  The default java in Breezy is the gnu-classpath, which doesn't quite work for many things.

---

### Post by weixiao.fan on 2005-10-21
I installed the sun-j2se1.5 at first, then install RSSOwl, then I found it doesn't works. This morning I uninstall the j2se1.5 and install j2re1.4, then it works. I don't know why because I know little about Java, hope I can get answer here :-)

---

### Post by djripple on 2007-04-10
Hey, RSS OWL does only give my the splash screen.  If anyone knows how to get it working that would be great.  I hear that going to JRE 1.4 will work.  How do I uninstall the JRE 1.5, or the 5.0 I have and go back to one that will work for RSSOWL.  when i try to run RSSOWL, i get the following error.. 

Exception in thread "main" org.eclipse.swt.SWTException: i/o error (java.util.zi p.ZipException: Deflated stream ends early.)
   at org.eclipse.swt.SWT.error(SWT.java:2942)
   at org.eclipse.swt.SWT.error(SWT.java:2866)
   at org.eclipse.swt.internal.image.GIFFileFormat.readID(GIFFileFormat.java:138 )

:X
Im a newb, so need some special loving care!! thanks

---

