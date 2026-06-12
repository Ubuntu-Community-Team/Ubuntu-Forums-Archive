---
title: "â””â”€&gt; ssh character display problems"
date: 2004-12-06
forum: General Help
---

### Post by MarkHoward on 2004-12-06
When using by ubuntu system over ssh, I get strange characters printed by apps such as debconf and mutt. Everything looks fine when using the machine itself (i.e. sitting in front of it rather than over ssh).  I'm using ssh client from cygwin, on the rxvt shell (ms windows unfortunately)
I've tried changing LANG, but this doesn't seem to help.  Does anyone have any ideas how to fix this?

Example of mutt display over ssh:
1376     12/03 Santiago Erquic (0.5K) gnome-user-share (apache) and open ports
1377     12/05 Jeff Waugh      (1.1K) â”œâ”€>
1378     12/03 Jerry Haltom    (0.7K) â”œâ”€>
1379     12/03 Jorge Bernal Ko (1.4K) â”‚ â””â”€>
1380     12/03 Jerry Haltom    (1.3K) â”‚   ”â”€>
1381     12/03 Thom May        (1.8K) â”‚   â””â”€xserver restart                                                                              1382     12/03 Jerry Haltom    (0.9K) â”‚   â””â”€>                                                                                             383         3 Matt Zimmerman  (0.9K) â””â”€>

---

