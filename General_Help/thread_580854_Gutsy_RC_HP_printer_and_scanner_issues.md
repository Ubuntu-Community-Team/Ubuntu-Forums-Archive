---
title: "Gutsy RC HP printer and scanner issues"
date: 2007-10-19
forum: General Help
---

### Post by Luis_vxd on 2007-10-19
Hi,

I got a HP PSC1215 printer (all-in-one). Everything was fine under Feisty.
This week (monday 14th) I upgrade to Gutsy RC and now got these issues:

1. printer goes pause state and do not print
2. printer needs to be state changed manually and need admin privilege to do it.
After clicking "Edit"and "Become Administrator" window disappears and some times do not come back have to reboot and start again (windows flavour? :))
3. printer prints when ready.
4. printer goes pause by itself again.
5. Xsane do not work with paused printer (device not found).
6. Xsane do not work (device I/O error) when printer is ready.
7. For Xsane to work need to have printer ready, then switch off printer and back on.

Is this normal under Gutsy? or is something wrong?

Thanks

---

### Post by Sef on 2007-10-19
Have you applied the updates and have Gutsy Stable now?

---

### Post by Luis_vxd on 2007-10-19
Hi,

The update went just fine no big issues some re-tune here and there mainly Xserver.
Everything seems fine. 
What you mean by "Gutsy Stable"? anything I need to download ?

---

### Post by Luis_vxd on 2007-10-22
Hi

Thanks for your support.

The problem is sorted out. 
Syslog reported a failure on CUPSEXT. After a search on other Linux distros I found the solution. Copy the (better create a link) 'cupsext.so' file to /usr/share/hplip/ from /usr/lib/python2.5/site-packages/. Now printers are steady and Xsane Happy.

---

