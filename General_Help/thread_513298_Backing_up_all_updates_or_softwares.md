---
title: "Backing up all updates or softwares"
date: 2007-07-30
forum: General Help
---

### Post by designwiz on 2007-07-30
Hmm heres my problem i have been thinkin a way out since some time...

Every time i reinstall ubuntu.. i need to do the updates (approx 192MB) and install alot of other programs xine,vlc, codecs etc 

Now the problem i cannot get the net connection to work in linux do to some problems wit the authentication client( [www.powersurfer.net](www.powersurfer.net)) thats my provider.

So was wondering would there be anyways where i could download all these files including beryl nvidia drivers, gdesklets on a windows machine and then copy it onto my pendrive and late apply the same to linux!
Its quite painful to download all these files everytime my os crashes! Thought of using Sbackup(i hope i got the name rite) bt i would prefer getting the deb files or the installation files onto a CD...Any suggestion help?

---

### Post by dreadlord_chris on 2007-07-30
> **designwiz said:**
> Hmm heres my problem i have been thinkin a way out since some time...

Every time i reinstall ubuntu.. i need to do the updates (approx 192MB) and install alot of other programs xine,vlc, codecs etc 

Now the problem i cannot get the net connection to work in linux do to some problems wit the authentication client( [www.powersurfer.net](www.powersurfer.net)) thats my provider.

So was wondering would there be anyways where i could download all these files including beryl nvidia drivers, gdesklets on a windows machine and then copy it onto my pendrive and late apply the same to linux!
Its quite painful to download all these files everytime my os crashes! Thought of using Sbackup(i hope i got the name rite) bt i would prefer getting the deb files or the installation files onto a CD...Any suggestion help?

Take a look at [APTonCD]("http://aptoncd.sourceforge.net/")

---

### Post by designwiz on 2007-07-30
I think that was just the software i was looking for.. thanks a ton! 
p.s has any1 tried this one out?

---

### Post by dreadlord_chris on 2007-07-30
> **designwiz said:**
> I think that was just the software i was looking for.. thanks a ton! 
p.s has any1 tried this one out?

Yup, works just as advertised....

---

### Post by ugm6hr on 2007-07-30
All your downloaded / installed .deb files are in var/cache/apt - you can just copy them directly (either CD or different partition), then copy back when reinstalling (with sudo).

---

