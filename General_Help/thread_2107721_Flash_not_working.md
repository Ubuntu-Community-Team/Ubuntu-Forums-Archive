---
title: "Flash not working"
date: 2013-01-22
forum: General Help
---

### Post by mastergunner on 2013-01-22
I have been wrestling with this issue since I first loaded Lubuntu on an old HP Pavilion XE4400. Flash does not work. I know flash is there in my plugins but it doesnt work. Sometimes it states that "Shockwave player not loading" in the browser. I have searched for solutions on this subject but there seems to be very few that ave gotten this to work. Has anyone got Flash to work properly in Lubuntu?

---

### Post by ajgreeny on 2013-01-22
Flash works fine in my Lubuntu 12.04, but only with a version of flash that does not need sse2 enabled in the cpu.

I use flash 11.1.102-63 from [Flash 11.1.102-63]("http://ubuntuforums.org/showthread.php?t=1953796") and that is fine though read and act on the security comments made in that webpage.

You can tell if your cpu is sse2 enabled with the command ```
cat /proc/cpuinfo
``` to see if sse2 appears in the list under **flags**.

You should also make sure you have removed any packages that may be causing conflicts with flash, such as gnash,  sfwdec-mozilla or any other swf packages.

---

### Post by mastergunner on 2013-01-22
ajgreeny thanks for reply. I have checked and my cpu is NOT sse2. What do I do now?

How can I remove all of the swf files you have mentioned easily?

---

### Post by ajgreeny on 2013-01-22
Use synaptic to remove any packages I mentioned and also the flash package you used to install flash, then go to that flash site I linked and follow the instructions there to install 11.1.102-63.

---

### Post by mastergunner on 2013-01-23
ajgreeny just so I understand this will work with cpu's that are not sse2 compliant?

---

### Post by ajgreeny on 2013-01-23
Yes, it will.

Always assuming nothing else is wrong and stopping it doing so.

---

