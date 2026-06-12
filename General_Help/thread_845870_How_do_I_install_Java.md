---
title: "How do I install Java?"
date: 2008-07-01
forum: General Help
---

### Post by YMS_1975 on 2008-07-01
Hi,

I'm having nothing but problems installing Java. I've done a search through the forums and nothing I've tried is working.

Here's what I've done to install Java : 

1) Through "Add/Remove..." I did a search for "Sun Java".
2) "Sun Java 6 Runtime was the first hit.
3) I installed this.
4) I went to [http://www.javatester.org](http://www.javatester.org) to see if my Java was working.
5) After it failed the test, it offered me 4 options to install a plugin
   to help with the problem. Those 4 options were :

a. GCJ Web Browser Plugin
b. The Java(TM) Plug-in, Java SE 6
c. The Java(TM) Plug-in, Java SE 5.0
d. The GCJ Web Browser Plugin (using OpenJDK)

6) I clicked on option "B" -- The Java(TM) Plug-in, Java SE 6. When I tested it, it still wouldn't work.

Any ideas on how I can get my Java working?

---

### Post by kessaris on 2008-07-01
You might have to also install the java plugin for Mozilla..

it's under sun-java6-plugin in Synaptic..

---

### Post by jamesstansell on 2008-07-01
Are you by chance running Firefox 2?  If so then search for posts tagged with both java and firefox 2.  There was a packaging bug that affected hardy when it was first released.  It's been worked on but I'm not sure if the update is available yet.  Until then you have to manually add a symbolic link to the java plugin.  Your other option would be to move to firefox 3.

The other time people see problems similar to yours is when running from the live CD, but I assume you're not, or you would have mentioned it.

---

### Post by Sef on 2008-07-01
Are you using a 32 or 64-bit system?

---

### Post by kessaris on 2008-07-01
Ah! I didn't realize there was a difference between 32 and 64 bit systems!

---

### Post by soccerboy on 2008-07-01
follow java pertaining instructions here: [http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)
mine works from its instructions.

---

### Post by YMS_1975 on 2008-07-01
I got it to work.

I went through the Synaptic Package Manager, and everything that had "Sun Java 6" in it, I just marked it for installation.

Then I tried it, and it worked.  :guitar:

---

