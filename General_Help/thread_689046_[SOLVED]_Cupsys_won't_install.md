---
title: "[SOLVED] Cupsys won't install"
date: 2008-02-06
forum: General Help
---

### Post by cybergalvez on 2008-02-06
I uninstalled cupsys (apt-get remove cupsys --pugre) and now it won't reinstall.  Every time I try to reinstall it I get the error on this page [http://paste.ubuntu-nl.org/54961/](http://paste.ubuntu-nl.org/54961/)

Can anyone help me with some pointers on how to reinstall cupsys, at the moment I have absolutely no printing ability,
Jose

---

### Post by kesman on 2008-02-06
```

dpkg - warning: while removing cupsys, directory `/etc/cups/ssl' not empty so not removed.

```
Try removing this directory manually with
```

sudo rm -r /etc/cups/ssl

```

and then try to reinstall.

---

### Post by cybergalvez on 2008-02-06
tried that, still can't install cups

---

### Post by lsavidge on 2008-02-06
Hi,

Is there anything in the logs for cups after trying to reinstall?

/var/log/cups/error_log

Thanks,

Lee

---

### Post by cybergalvez on 2008-02-06
nope the folder is completely empty

---

### Post by lsavidge on 2008-02-06
Hi,

> **cybergalvez said:**
> nope the folder is completely empty

I see the install is trying to download the amd64 files for cups. I assume that this is the correct version? If so, I found that there was an old version of cups that had an inssue with amd64 and I don't know if it was solved. Is there a folder called mime in here: /usr/share/cups/

If not, create it and give it root perms. Then try again.

Cheers,

---

### Post by cybergalvez on 2008-02-06
yes the mime folder is present

---

### Post by cybergalvez on 2008-02-06
> **lsavidge said:**
> Hi,



I see the install is trying to download the amd64 files for cups. I assume that this is the correct version? If so, I found that there was an old version of cups that had an inssue with amd64 and I don't know if it was solved. Is there a folder called mime in here: /usr/share/cups/

If not, create it and give it root perms. Then try again.

Cheers,

Also forgot to mention that yes this is on an amp64
Jose

---

### Post by cybergalvez on 2008-02-06
Problem solved! After a long conversation with albert23 and bdmurray in the irc they pointed out to me that my version of sysv-rc was the wrong one (I have no idea how they cam to this conclusion from the tests we were doing but they did).  I had version 2.86.ds1-38 and it should have been version 2.86.ds1-14.1ubuntu31.  I have no idea how I got the wrong version of sysv-rc on my system but did.  In any event once I did a force install to the correct version everything else fell into place and I was able to update everything!  Thanks albert23 and bdmurray for all your help this afternoon

Jose

---

