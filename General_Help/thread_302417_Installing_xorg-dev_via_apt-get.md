---
title: "Installing xorg-dev via apt-get"
date: 2006-11-18
forum: General Help
---

### Post by Fafnr on 2006-11-18
First of all, I'd like to apologize if I'm posting in the wrong forum - I'm new here and I wasn't sure where to ask this question...
Also, if this is a duplicate of some thread, I apologize in advance too - I did a few searches for (what I think is) relevant keywords, but found nothing I could use...

Anyway, I'm trýing to apt-get the xorg-dev package since another program I wan't to compile needs it. (Or at least some of the packages it entails...)

But, when I try to install it, I get the following error:

```

xorg-dev:
 Depends: libdmx-dev but it is not going to be installed
 Depends: libx11-dev but it is not going to be installed
 Depends: libxaw7-dev but it is not going to be installed
 Depends: libxcomposite-dev but it is not going to be installed
 Depends: libxcursor-dev but it is not going to be installed
 Depends: libxdamage-dev but it is not going to be installed
 Depends: libxext-dev but it is not going to be installed
 Depends: libxfixes-dev but it is not going to be installed
 Depends: libxfont-dev but it is not going to be installed
 Depends: libxft-dev but it is not going to be installed
 Depends: libxi-dev but it is not going to be installed
 Depends: libxinerama-dev but it is not going to be installed
 Depends: libxkbfile-dev but it is not going to be installed
 Depends: libxkbui-dev but it is not going to be installed
 Depends: libxmu-dev but it is not going to be installed
 Depends: libxmuu-dev but it is not going to be installed
 Depends: libxpm-dev but it is not going to be installed
 Depends: libxrandr-dev but it is not going to be installed
 Depends: libxrender-dev but it is not going to be installed
 Depends: libxres-dev but it is not going to be installed
 Depends: libxss-dev but it is not going to be installed
 Depends: libxt-dev but it is not going to be installed
 Depends: libxtrap-dev but it is not going to be installed
 Depends: libxtst-dev but it is not going to be installed
 Depends: libxv-dev but it is not going to be installed
 Depends: libxvmc-dev but it is not going to be installed
 Depends: libxxf86dga-dev but it is not going to be installed
 Depends: libxxf86misc-dev but it is not going to be installed
 Depends: libxxf86vm-dev but it is not going to be installed

```

And to be honest, I don't understant *anything* about that. :-)
Mainly, I thought apt-get was meant to resolve these dependencies?
What am I doing wrong?

I'm running Ubuntu 6.10 (should I perhaps have gotten the 6.06 release instead?) and I'm otherwise extremely happy with it. :-)

Regards,

Søren

---

### Post by t1m on 2007-01-04
Hi, I have had the same problem and havn't found the answer. If you try installing xorg-dev in synaptic it seems to say it needs some repository enabled, as to which one, I have no clue!
Hope you find the answer ;)

---

### Post by majoridiot on 2007-01-04
you didn't say if you're running dapper or edgy, but i just tried to install xorg-dev in dapper
using the synaptic package manager (System-->Administration-->Synaptic Package Manager),
searched for xorg-dev, marked it for installation, ok'd the dependencies and applied it.  it
installed with no problem.

dunno what repository it came from, so make sure you have universe and multiverse enabled
(in synaptic Settings-->Repositories... Edit button and check the boxes, ok and then hit the
Reload button to refresh things) and then search for xorg-dev and go from there.

---

### Post by t1m on 2007-01-05
I'm running Dapper.

When I try to install xorg-dev it says "such and such" packages need to be installed, so I said OK, then it says "the following packages have unresolvable dependencies." And that I need to enable whatever repos they're in.
Here's part of what synaptic said:
```
Depends: libxcomposite-dev but it is not going to be installed
Depends: libxss-dev but it is not going to be installed
Depends: xserver-xorg-dev but it is not going to be installed
``` :-k 

Maby someone could post thier sources list for me to see.
Tnx

---

