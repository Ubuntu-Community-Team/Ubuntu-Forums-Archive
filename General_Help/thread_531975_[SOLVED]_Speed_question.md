---
title: "[SOLVED] Speed question"
date: 2007-08-22
forum: General Help
---

### Post by Old Duffers on 2007-08-22
Old Duffer has a question.  I run xp on one computer and Ubuntu on the other. kvm switch.
When I run a speed test on speakeasy.net, the download speed on the xp computer is 
1870 kbps.  On the Ubuntu computer, it's 8700 kbps.  I use the Kansas City site.  Why is this???

---

### Post by MeneM on 2007-08-22
Hard to answer based on this alone.

My heart immediatly yells: Because Linux is better!!! But I would need to look at some sniffer output from the two computers to tell you what's actually happening here.

You can use Packetyzer on windows and wireshark on ubuntu to "capture" the data flowing between your computers and the website. From those "capture-logs" we could see what is going on.

---

### Post by Old Duffers on 2007-08-22
I like to think it's UBUNTU also.  :-)

---

### Post by ebash on 2007-08-22
Maybe windows is not running in Full-duplex. Try to follow this tutorial [http://ots.iit.edu/network/windowsxp_fullduplex.php]("http://ots.iit.edu/network/windowsxp_fullduplex.php") iin order to check your windows settings.

---

### Post by Old Duffers on 2007-08-22
Thanks EBASH!  That worked.  xp wasn't set at "full duplex".  Now both computers are downloading at about the same rate.  Thanks for the quick replys.

---

### Post by ebash on 2007-08-22
Your welcome Old Duffers. Don't forget to mark the thread as solved.

---

