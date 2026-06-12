---
title: "cpu requirement for chromium pepperflash"
date: 2014-08-28
forum: General Help
---

### Post by jdefed on 2014-08-28
Does anyone know the cpu requirements for chromium pepperflash. I have an old computer with a Socket "A" Athlon cpu. I had a problem awhile back with Adobe flash and it turned out that my cpu lacked some architecture needed to run flash. I'm considering 14.04 lts, but like chromium better than Firefox.

---

### Post by Dennis N on 2014-08-28
There is a problem of older cpus with either brand of flash as I understand it - both come from Adobe.

There is a test you can make described here:

[http://ubuntuforums.org/showthread.php?t=2239025&p=13095752#post13095752](http://ubuntuforums.org/showthread.php?t=2239025&p=13095752#post13095752)

Also see:

[https://productforums.google.com/forum/#!topic/chrome/m_WiLfCpTZE](https://productforums.google.com/forum/#!topic/chrome/m_WiLfCpTZE)

or google "pepperflash sse2" for more links.

---

### Post by mörgæs on 2014-08-28
What the Socket A processors lack is the SSE2 instruction set. 

Best is to use HTML 5 if possible, but you can download an old Flash package which does not depend on SSE2. More info in the link in my signature.

---

