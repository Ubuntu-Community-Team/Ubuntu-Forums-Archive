---
title: "konsole -e &quot;blah blah blah&quot; doesn't work"
date: 2008-03-20
forum: General Help
---

### Post by phillips321 on 2008-03-20
Hi guys,

For some reason the following does not work:
```
konsole -e 'ifconfig eth0'
```

but this does:
```
xterm -e 'ifconfig eth0'
```

it's due to the space inbetween ifconfig and eth0 that prevents it, i.e.```
konsole -e 'ifconfig'
``` works just fine.

Any ideas guys????

---

### Post by doorknob60 on 2008-03-20
```
konsole -e 'ifconfig\ eth0'
```
Might work not sure though.

---

### Post by phillips321 on 2008-03-21
nope, doesn't work, tried that.

Any one got any other ideas?

Is this a bug??

Can someone else try to replicate the fault for me please :)

---

