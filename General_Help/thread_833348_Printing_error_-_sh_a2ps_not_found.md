---
title: "Printing error - sh: a2ps: not found"
date: 2008-06-18
forum: General Help
---

### Post by MountainX on 2008-06-18
I started getting this error recently when I try to print from my text editor. I'm using SciTE. SciTE was printing just fine for a long time and then this error popped up. (I presume it is related to some Ubuntu updates.)

Can anyone give me a clue as to what the issue might be? Thanks.

---

### Post by prshah on 2008-06-18
> **MountainX said:**
> I started getting this error recently when I try to print from my text editor.

You can try re-installing a2ps incase it's broken```
sudo apt-get install --reinstall a2ps psutils
```

---

### Post by MountainX on 2008-06-18
Thanks. I reinstalled a2ps via Synaptic. My test document to print is called "2008.06.17.txt". When I try to print it, I get the error shown below. The a2ps docs are making my head spin. Surely there should be an easier way to set a default printer... I need some help. Thanks.

>a2ps "2008.06.17.txt"
[2008.06.17.txt (plain): 1 page on 1 sheet]
/usr/bin/lp: Error - no default destination available.
[Total: 1 page on 1 sheet] sent to the default printer
[7 lines wrapped]
>Exit code: 0

---

