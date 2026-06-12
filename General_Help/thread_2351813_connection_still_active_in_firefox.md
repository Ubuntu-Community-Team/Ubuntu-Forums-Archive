---
title: "connection still active in firefox"
date: 2017-02-07
forum: General Help
---

### Post by Skaperen on 2017-02-07
around a month ago i start getting connections remaining active on many website.  what i see is the blue rotor for that site's tabs keep on rotating forever.  most of these sites display ok, but a few just never load any content.  slashdot.org is one which displays ok but never ends rotating.  this started before christmas.  i am running ubuntu 16.04 lts that i installed on a system 76 laptop and upgrade every few days.  firefox is at version 51.01.  this problem has not appeared in other programs.  anyone seen anything like this?  should i treat it as a network issue?  a kernel issue?  a firefox issee?  something else?  i did netstat -antup and found a number of established connections but i don't know if this is the same issue.  the reverse dns for all of these that do resolve is 1e100.net (google).  [B]could these be ads that the servers pause on sending at the end to track how long people stay on various sites?

[/B]*edit:*

this is also happening here at ubuntuforums.org when i post or saved an edit, but the article does get updated ... i can see this by loading it in another tab.

*edit2:*

after several minutes of waiting for the post/edit to finish at the browser, it loads [https://ubuntuforums.org/editpost.php?do=updatepost&p=13603999](https://ubuntuforums.org/editpost.php?do=updatepost&p=13603999) which says "Ubuntuforums.org is temporarily down at the moment." in a large font.

but at least all my edits do get applied.  weird.

---

### Post by wildmanne39 on 2017-02-07
The issue you were having on the forum is because the forum is actually having issues that come and go and they just stopped again a few minutes ago.

---

### Post by Skaperen on 2017-02-07
ok, i will disregard the forum issues for the general hanging connection issue i have been seeing.  is my system/browser/network doing bad things to the forum server?  i am running on a VPN, but not sure the MTU is set right.

---

### Post by QIII on 2017-02-07
No.  You are not doing anything to the server.  It is acting up all of it's own accord.

---

### Post by wildmanne39 on 2017-02-07
A lot of people leave MTU on auto, but a good setting is usually 1492.

---

