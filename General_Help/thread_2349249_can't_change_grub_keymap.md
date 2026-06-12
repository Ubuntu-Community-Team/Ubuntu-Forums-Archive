---
title: "can't change grub keymap"
date: 2017-01-12
forum: General Help
---

### Post by Ed_B on 2017-01-12
Hi, I am trying to change grub keymap, but I get stuck at
```
grub-kbdcomp -o test fr
Unknown keyboard scan code 0x54
Unknown keyboard scan code 0x65
Unknown keyboard scan code 0x7f

```
and the file "test" contains
```

GRUBLAYO






<




```
Actually grub-kbdcomp is just a wrapper script for ckbcomp and grub-mklayout, and ckbcomp is working fine.  If I run grub-mklayout with stdout as output,
then I get
```
Unknown keyboard scan code 0x54
Unknown keyboard scan code 0x65
Unknown keyboard scan code 0x7f
GRUBLAYO
qbcdefghijkl,noparstuvzxyw&&#65533;"'(-&#65533;_&#65533;&#65533;
        ^$*m&#65533;&#65533;;:!;&#65533;<&#65533;=&#65533;>&#65533;?&#65533;@&#65533;A&#65533;B&#65533;C&#65533;D&#65533;W&#65533;X&#65533;R&#65533;G&#65533;I&#65533;S&#65533;O&#65533;Q&#65533;M&#65533;K&#65533;P&#65533;H&#65533;/*-+
O&#65533;P&#65533;Q&#65533;K&#65533;L&#65533;M&#65533;G&#65533;H&#65533;I&#65533;S&#65533;<S&#65533;QBCDEFGHIJKL?NOPARSTUVZXYW1234567890
        +"&#65533;&#65533;M%~./&#65533;;&#65533;<&#65533;=&#65533;>&#65533;?&#65533;@&#65533;A&#65533;B&#65533;C&#65533;D&#65533;W&#65533;X&#65533;R&#65533;G&#65533;S&#65533;O&#65533;M&#65533;K&#65533;P&#65533;H&#65533;/*-+
123456789.>.@ &#65533;&#65533;&#65533; K'&#65533;!  8B'n&#65533;&#65533;&#65533;&#65533;&#65533;g&#65533;! &#65533;&#65533;&#65533;!B&#65533;~#{[|`\^@
        }"&#65533;`&#65533;^&#65533;%&#65533;#;&#65533;<&#65533;=&#65533;>&#65533;?&#65533;@&#65533;A&#65533;B&#65533;C&#65533;D&#65533;W&#65533;X&#65533;R&#65533;G&#65533;I&#65533;S&#65533;O&#65533;Q&#65533;M&#65533;K&#65533;P&#65533;H&#65533;S&#65533;|S&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;J&1N&#65533;&#65533;&#65533;&#65533;&#65533;f&#65533;! <>&#65533;A&#65533;[!&#65533;$\!]!^!"!&#65533;&#65533;
        &#65533;_&#65533;&#65533;&#65533;&#65533;.;&#65533;<&#65533;=&#65533;>&#65533;?&#65533;@&#65533;A&#65533;B&#65533;C&#65533;D&#65533;W&#65533;X&#65533;R&#65533;G&#65533;I&#65533;S&#65533;O&#65533;Q&#65533;M&#65533;K&#65533;P&#65533;H&#65533;/*-+
123456789.&#65533;.

```
(Unreadable characters are due to some problem of copy-pasting of the clipboard, I get normal characters on the terminal).

I use ubuntu 16.04.1 LTS 64bit, and the version of grub-mklayout is   2.02~beta2-36ubuntu3.6.  Would there be any way to get around this?

---

