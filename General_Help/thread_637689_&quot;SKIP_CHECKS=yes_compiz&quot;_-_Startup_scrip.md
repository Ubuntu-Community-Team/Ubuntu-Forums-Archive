---
title: "&quot;SKIP_CHECKS=yes compiz&quot; - Startup script"
date: 2007-12-11
forum: General Help
---

### Post by drobles on 2007-12-11
Hello, I've been looking a lot to make my laptop (Sony Vaio VGN-FZ140E) run Compiz Fusion, after looking for about a week in the Ubuntu Forums I found a way to run Compiz and it works!

I run the following command:

```
SKIP_CHECKS=yes compiz
```

After Ubuntu starts I  run that command and then I have Compiz Fusion working fine. Does anyone knows where is the compiz configuration file, so I won't have to be running this every time...

Thanks

---

### Post by pointone on 2007-12-11
You can run it using the "Run Application" dialog; simply press Alt+F2.

A better solution, though, would be to create ~/.config/compiz/compiz-manager containing SKIP_CHECKS=yes.

---

### Post by drobles on 2007-12-11
I tried with the ALT F2 running this and didnt work:

```
SKIP_CHECKS=yes compiz
```

I also edited the ~/.config/compiz/compizconfig/config configuration file and added the same command at the end withouth 'compiz' at the end:

```
SKIP_CHECKS=yes
```

do I have to manually start compiz fusion?

---

### Post by myddewji13 on 2008-02-05
ok...i have no idea what im doing...but according to:
[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

u need to modify:
 ~/.config/compiz/compiz-manager

---

### Post by sceo on 2008-02-08
According to [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

You can also store this value, where it is depends on your distribution, usually it is a matter of putting

SKIP_CHECKS=yes

in ~/.config/compiz/compiz-manager .

---

### Post by PCSmasher on 2008-02-28
When I run this command, either from the command line or with a script, my computer locks up and shuts down.  Flashes a screen up that it is stopping apache2 because it is out of memory.  I'm kinda stuck now.  everything works fine until I invoke this command.

---

### Post by Foreman on 2008-05-29
On Hardy, the compiz settings files is located at
```
/.config/compiz/compizconfig/config
```

---

