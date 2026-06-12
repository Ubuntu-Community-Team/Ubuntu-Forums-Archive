---
title: "[SOLVED] Unable to &amp;quot;Accept this certificate permanently&amp;quot;"
date: 2008-05-12
forum: General Help
---

### Post by danduq on 2008-05-12
Hi,

I have posted this in Mozillazine as well, but have not had any help. Not sure which category to post under here either, so sorry if it's in the wrong place!

I am running FF2.0.0.14 on Ubuntu 8.04 (after completely removing FF3 beta). If I go to a self-signed site (E.G. our company Intranet) I am unable to accept the SSL certificate permanently. The pop-up appears asking if I want to accept the cert permanently, just for the session or not at all. If I select permanently and click OK the dialogue box reappears after a second and just keeps on looping until I choose "this session only".

This is the same version of FF as I have used successfully on Windows. I think it's permissions related, I.E. I'm allowed to accept certs for my session, but perhaps only root has write access to global session data? The problem is, I'm not sure where this is.

Any pointers gratefully received!

---

### Post by DJ_Peng on 2008-05-12
Not sure why this is happening. I run Firefox 2 on Hardy (although not with Ubuntu's Fx2, so that may be an important difference for some odd reason) and have no problems permanently accepting certificates. Is this the same profile you were using on Firefox 3 or are you using a Firefox 2-specific profile?

---

### Post by danduq on 2008-05-12
Thanks DJ_Peng.

I did this;
1) Performed a complete purge of FF3 
2) made sure there was no profile hanging around in ~/.mozilla/firefox
3) Did "sudo apt-get install firefox-2"
4) Ran FF2 to create the profile
5) Did a "sudo chown -R me:me ~/.mozilla/firefox" to make sure I had full perms on profile.

I suspect it's something in the /usr/lib/firefox directory somewhere as these are all owned by root, but I'm not sure what!  :confused:

---

### Post by DJ_Peng on 2008-05-12
No problem. Hopefully someone who uses Ubuntu's Firefox 2 will be able to help with that.

---

### Post by danduq on 2008-05-13
OK, fixed it by renaming the cert8.db file in my firefox profile directory and restarting FF2.  :KS

---

