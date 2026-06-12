---
title: "Weird command line behavior"
date: 2007-05-15
forum: General Help
---

### Post by rob1n on 2007-05-15
I have a VPS running a clean install of Ubuntu, straight from the CD, but when I SSH in, my command line prompt is limited to about 2/3 the way across the screen, then it wraps over the same line, over the text that was previously there. The commands still work, but it's impossible to tell what they are because they're all overwritten.

This only happens on my (regular) user. The root prompt (through ```
su
```) works fine, which makes me think that this is some weird setting that I need to set up.

---

### Post by rob1n on 2007-05-19
*Bump*?

---

### Post by mbradlcu on 2007-05-20
what term are you using to ssh? the shotgun approach I'd use would be to try alternative terminals, then maybe mess with xterm like 'xterm +ai'

---

### Post by rob1n on 2007-05-20
I'm using Mac OS X's terminal. I'll try the xterm one.

Thanks.

---

