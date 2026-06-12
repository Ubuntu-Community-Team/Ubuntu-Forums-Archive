---
title: "Lost a NTFS partition!"
date: 2008-06-28
forum: General Help
---

### Post by PabloMDiez on 2008-06-28
Hi there! Once I forced mount a NTFS partition because Windows was bad shutdown. Since there I can't access it anymore, Ubuntu doesn't recognize the partition and Windows shows the unit as unformatted!

What can I do?

Excuse my English :)

---

### Post by VMC on 2008-06-28
> **PabloMDiez said:**
> Hi there! Once I forced mount a NTFS partition because Windows was bad shutdown. Since there I can't access it anymore, Ubuntu doesn't recognize the partition and Windows shows the unit as unformatted!

What can I do?

Excuse my English :)

Why not just format it using Windows. What happened with Windows shutdown? Did you just power off the computer?

From ubuntu Terminal type the following.

```
sudo fdisk -l
```

Output the results.

---

### Post by Taxman415a on 2008-06-28
You're going to have to try some file/partition recovery tools. What does the output of 
sudo fdisk -l
show?

Try your favorite package installation method such as apt-get or synaptic to install some of the packages listed here: [http://ubuntu-rescue-remix.org/Software](http://ubuntu-rescue-remix.org/Software)
Particularly testdisk, but maybe also ntfsprogs may be of use to you. The others will become more useful if the partition entry cannot be recovered and you need to try to recover the files anyway.

---

### Post by PabloMDiez on 2008-06-29
Thanks for replying.

> **VMC said:**
> Why not just format it using Windows. What happened with Windows shutdown? Did you just power off the computer?

From ubuntu Terminal type the following.

```
sudo fdisk -l
```

Output the results.

Format it?! Noo! It has my info, docs, music, downloads, everything!
As always, windows hanged, and I had to restart the PC. But instead of opening Windows again, opened Ubuntu. I needed to access to a drive from Ubuntu but I couldn't mount it since it's "in use". So I forced mounted that and voilà! =). After that I well-shutdown my pc and every time I power on it, my unit doens't shows.

> **Taxman415a said:**
> You're going to have to try some file/partition recovery tools. What does the output of 
sudo fdisk -l
show?

Try your favorite package installation method such as apt-get or synaptic to install some of the packages listed here: [http://ubuntu-rescue-remix.org/Software](http://ubuntu-rescue-remix.org/Software)
Particularly testdisk, but maybe also ntfsprogs may be of use to you. The others will become more useful if the partition entry cannot be recovered and you need to try to recover the files anyway.

I'll test that =)

Used GParted, and It shows my unit, but with a exclamation icon.
Fdisk too.

FYI partition is** /dev/sda5**


Thanks!

---

