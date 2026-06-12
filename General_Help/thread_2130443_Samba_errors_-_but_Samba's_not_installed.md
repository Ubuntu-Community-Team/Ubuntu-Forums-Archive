---
title: "Samba errors - but Samba's not installed"
date: 2013-03-29
forum: General Help
---

### Post by meatychunks on 2013-03-29
Hi,

Whilst using Nautilus I've recently been faced with a popup message telling me "net usershare returned error 255" - something about no access to /var/lib/samba/usershare.

I don't have Samba installed on this machine - can anyone shed any light..?

Thanks.

---

### Post by Jay_E on 2013-03-29
I had same error a few days ago. Have forgotten what I was doing at the time - but making
 the directory solved the symptom.

cd /var/lib/samba
 sudo   mkdir  usershare

if there  are problems, check permissions.

Jay

---

### Post by meatychunks on 2013-03-29
Thanks Jay,

May well give it a go, but I'm still curious as to what's caused it. I've been running this installation of 12.04 for the past 9 months without issue; this just started occuring in the last couple of weeks.

If anyone else can shed some light I'd be grateful...

---

### Post by Jay_E on 2013-03-29
Hi there.

lsof may identify what is using that directory - IF a file is open for any length of time.

sudo  lsof | grep  samba

another approach is to try to remember what has been installed/reinstalled/upgraded
or, remember what was running when you saw the pop-up.

:-)  If it were me, I sure don't remember..

for grins try running your favorite programs, and run the lsof at the same time..

Just shots in the dark.

I agree, it is much better to find the cause - rather than mask the symptom.

Jay

---

### Post by Jay_E on 2013-03-29
also may look at
/var/log/dpkg.log
 to get list of package changes.
Might be a big list...
Jay

---

### Post by meatychunks on 2013-03-30
Cheers Jay,

I'll give lsof a go next time this occurs.

---

