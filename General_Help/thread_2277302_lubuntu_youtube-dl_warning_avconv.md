---
title: "lubuntu youtube-dl warning avconv"
date: 2015-05-07
forum: General Help
---

### Post by Portaro on 2015-05-07
I have a problem with youtube-dl -
 youtube-dl apear a message like warning avconv is outdated, update your avconv to 10...

When I search for avconv on my Lubuntu synaptic cant find nothing.

My version is 14.04, any help?

---

### Post by mc4man on 2015-05-08
avconv is in the libav-tools package, 14.04 uses 6.9
Generally speaking it's just a warning & shouldn't affect use. If you want to build your own static libav then that would take care of the warning & any possible effects.

Otherwise a recent ffmpeg can be either built or installed from various ppa's  but note that youtube-dl defaults to using avconv so if a newer ffmpeg is available it won't use it if avconv is installed. 
Solution there is to either remove libav-tools or pass an option to youtube-dl - 
 youtube-dl --prefer-ffmpeg blah, blah

Note: if a newer ffmpeg is present & libav-tools is installed & wanting to use ffmpeg then one could also just set an alias - 
In ~/.bash_aliases  (create if not there
```
alias youtube-dl='youtube-dl --prefer-ffmpeg'
```

---

### Post by Bucky Ball on 2015-05-08
*Thread closed.*

Even though youtube-dl is available in Ubuntu, we do not provide support for it here, and this is why, from the forum Code of Conduct:

> We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings. 

Also, see [this]("http://ubuntuforums.org/showthread.php?t=1850955").

---

