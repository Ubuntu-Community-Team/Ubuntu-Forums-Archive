---
title: "facebook photo uploader java applet font missing?"
date: 2008-07-09
forum: General Help
---

### Post by Mercury821 on 2008-07-09
Hi all.  I'm having trouble getting the facebook photo uploader java applet to work correctly on my Hardy system.  I've installed java-6, and the uploader applet loads, but the font seems to be missing.  Any ideas?  Is there a font package I need to install?

Take a look at the screenshot attached to see what I'm talking about...

---

### Post by arm-c on 2008-07-09
First, I don't use facebook; however, the problem may be the java plugin you are using.

from firefox (i hope that is what you are using), check to see what java plugin you are using.  Place following in the Location Bar (where URL would go)

CODE: about:plugins

Scroll down and see if you are using the:

Java(TM) Plug-in 1.6.0_06-b02

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_06 

Hardy defaults to an opensource java plugin called "Iced Tea" or something to that effect.  I had a terrible time with Java and Firefox initially until I figured that out.

IF you have IcedTea, use synaptic to remove it and install the Java Plug-in.  If it is already installed, the removal of Iced Tea should fix it.

HOPE THAT THIS HELPS!

---

### Post by Mercury821 on 2008-07-13
I don't have Iced Tea, I have the latest java plugin.  Any other ideas?

Thanks!

---

### Post by arm-c on 2008-07-14
You checked the about:plugins and verified it there?  

My problem was I thought I had it installed cause i used synaptic to do it, but when I checked, icetea was still the default for me.  I had to remove it.

I don't have any other sugestions.

---

### Post by Mercury821 on 2008-07-14
I did look at about:plugins, and I see no mention of icedtea.  But, as you can see from this screenshot, firefox is showing some weird fonts on this page too when listing the java-related info.

---

