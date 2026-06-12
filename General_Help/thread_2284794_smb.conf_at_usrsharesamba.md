---
title: "smb.conf at /usr/share/samba"
date: 2015-07-01
forum: General Help
---

### Post by shag00 on 2015-07-01
I have just upgraded to 15.04 and noticed /usr/share/samba/smb.conf. 

I have been using /etc/samba/smb.conf and my system seems to be using it as well.

Any ideas what the /usr version is and why its there?

---

### Post by kerry_s on 2015-07-01
that's the default settings. /etc... is for modifications

---

### Post by bab1 on 2015-07-02
> **shag00 said:**
> I have just upgraded to 15.04 and noticed /usr/share/samba/smb.conf. 

I have been using /etc/samba/smb.conf and my system seems to be using the it as well.

Any ideas what the /usr version is and why its there?

When the smbd daemon (the Samba server) is started it reads the /etc/samba/smb.conf file to get the parameters it uses.  As @kerry_s says the Debian/Ubuntu defaults are listed in the file at /usr/share/samba/smb.conf.   It is a reference file only.

---

### Post by shag00 on 2015-07-02
Thank you gents.

---

