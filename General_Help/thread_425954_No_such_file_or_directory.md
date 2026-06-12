---
title: "No such file or directory"
date: 2007-04-28
forum: General Help
---

### Post by LaicaNuru on 2007-04-28
Good days.

I have installed several packages, such as GXMame, GR-lida or Grustibus (curious that they all are frontends), but at the moment of executing them returns the mistake to me:

```

~$ gr-lida bash:/usr/bin/gr-lida: Not such file or directory 

```

If I look in the indicated directory I see that the programs are there really. I install also other programs as the Xmame or the DOSbox and these work without problems.

Can it be because I use an AMD64, they are packages for i386 and I install them with - force-architecture?

---

### Post by kidders on 2007-04-29
Hi there,

I'm afraid your suspicion may be correct. It seems silly that Ubuntu would tell you "no such file or directory", when what it *really* means is "I don't understand that binary format" ... but there are times when this can happen.

I'm not familiar with the specific applications you mentioned, so I can only speak in general terms. If there is something you want to use that is only available for 32-bit platforms, you can still make it work, by using a 32-bit chroot-ed environment. They can be a little confusing to set up, but if you _really_ need something to work, it can be worth the effort.

Also, you need to be really careful when forcing installations ... You run the risk of damaging the rest of your system.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

