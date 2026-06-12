---
title: "Direct Rendering on Kubuntu - ATI 9600"
date: 2007-01-23
forum: General Help
---

### Post by klovn on 2007-01-23
I'm trying to get my ati9600 card to work on kubuntu (feisty).

I have followed this tutorial: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
and everything looked good until I executed: 

```

sudo module-assistant build,install fglrx-kernel

```

then I got this error :/ (/var/cache/modass/fglrx-kernel-source.buildlog.2.6.20-5-generic.1169556191)

```

http://pastebin.ca/325609

```

I have no idea what it means :/ What do I do?

---

### Post by Stemp on 2007-01-23
You should try the [Install from Ubuntu repositories]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-02330ccb580b6a9411d32bf617cc5a82116ba6b9") method. Easier and safer.

And BTW the ATI 9600 is working fine with the free ati/radeon driver ;) (with Beryl by example)

---

