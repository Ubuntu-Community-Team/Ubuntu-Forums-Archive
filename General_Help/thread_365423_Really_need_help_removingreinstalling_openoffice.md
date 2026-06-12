---
title: "Really need help removing/reinstalling openoffice"
date: 2007-02-19
forum: General Help
---

### Post by rwhillman on 2007-02-19
I am a novice and really need some help after hitting a stone wall.  I am trying to remove openoffice 2.0.4 and update with 2.1 (not part of the ubuntu package).  I just can't get 2.04 removed because of broken packages synaptic can't (won't) fix.  Would much appreciate novice-type help walking me through the removal process.

I think I can handle the update/reinstall if I can just clear the old version.

---

### Post by Rippey on 2007-02-19
try reinstalling the broken packages with sudo apt-get install --reinstall before removing them,
that worked for me a couple of times.

---

### Post by rwhillman on 2007-02-19
Thanks, but does not work.  After reinstall I still have 41 broken packages that synaptic won't touch.

---

### Post by Maestro23 on 2007-02-19
> **rwhillman said:**
> I am a novice and really need some help after hitting a stone wall.  I am trying to remove openoffice 2.0.4 and update with 2.1 (not part of the ubuntu package).  I just can't get 2.04 removed because of broken packages synaptic can't (won't) fix.  Would much appreciate novice-type help walking me through the removal process.

I think I can handle the update/reinstall if I can just clear the old version.

Follow the post by [COLOR="Red"]sgla1[/COLOR] and you should not have any problems.  Did this myself a couple of weeks ago.

[http://www.ubuntuforums.org/showthread.php?t=318865&page=3&highlight=Install+OpenOffice](http://www.ubuntuforums.org/showthread.php?t=318865&page=3&highlight=Install+OpenOffice)

Good luck.:)

---

### Post by rwhillman on 2007-02-19
Thanks for the help, and I am up and running with the updated openoffice.  If anybody else has the problem I did in removing openoffice with broken links, my problems were with language files that were installed, so I removed them individually in synaptic and things went smoothly from there.

---

### Post by Maestro23 on 2007-02-19
> **rwhillman said:**
> Thanks for the help, and I am up and running with the updated openoffice.  If anybody else has the problem I did in removing openoffice with broken links, my problems were with language files that were installed, so I removed them individually in synaptic and things went smoothly from there.

Glad it helped.  Where you the guy that was having OO crash when you opened up a template?

---

### Post by rwhillman on 2007-02-20
Yes, I was the template crasher.  Problem gone with 2.1.

---

### Post by Maestro23 on 2007-02-20
> **rwhillman said:**
> Yes, I was the template crasher.  Problem gone with 2.1.

Cool. Glad everything is working for you.:)

---

