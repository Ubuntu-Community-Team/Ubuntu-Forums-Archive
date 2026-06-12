---
title: "How to replace ifupdown.sh"
date: 2007-10-20
forum: General Help
---

### Post by JSander on 2007-10-20
I must have fat-fingered the removal of /etc/wpa_supplicant/ifupdown.sh

I issued the "dpkg -S ifupdown.sh" command which returned:
wpasupplicant: /etc/wpa_supplicant/ifupdown.sh

I used Synaptic to reinstall that package (three times, plus once asking to download the files, then installing the package manually). Every attempt said that the install was successful, however, the /etc/wpa_supplicant directory is still empty. I did two 'restarts' but this made no difference.

How can I recover this file?

Thank you,
Joe:confused:

---

### Post by DagMan on 2007-10-21
I've attached what I have inside the /etc/wpa_supplicant folder.  For some reason, I do not have wpa_supplicant in my apt-cache so I can't see what other files are installed with it.
Both files go in /etc/wpa_supplicant.  Make sure of the permissions of them being 755 with root:root but they should already be.

Okay looking now, in addition and not icluding documentation you will need /sbin/wpa_supplicant I'll upload it as well.

---

### Post by JSander on 2007-10-21
Thank you for the files, I appreciate it.

Joe

---

