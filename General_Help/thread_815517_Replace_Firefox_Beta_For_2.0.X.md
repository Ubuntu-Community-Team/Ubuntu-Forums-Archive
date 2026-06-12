---
title: "Replace Firefox Beta For 2.0.X?"
date: 2008-06-01
forum: General Help
---

### Post by CarlosinFL on 2008-06-01
I find Firefox 3 too Beta for production use. Is it possible to remove Firefox 3 Beta 5 and install an official stable release of Mozilla Firefox on Ubuntu 8.04?

---

### Post by quelx on 2008-06-01
search **synpatic** for **firefox-2** or ```
sudo apt-get install firefox-2 firefox-2-gnome-support
```

---

### Post by Zorael on 2008-06-01
Yep.
```
$ sudo aptitude purge ~nfirefox-3.0 firefox-2+
```
Clean browser cache first, and prepare yourself for some extension issues. They'll be flagged as 'incompatible' and you can have a hard time getting them to work again. I've seen several threads about this, so it's just a matter of hunting one down. I solved it by going to [http://addons.mozilla.org](http://addons.mozilla.org), installing one (1) addon, then restarting Firefox. That unlocked all installed extensions and I could remove those that didn't work.


I recommend Swiftweasel though, it's compiled and optimized for linux. [http://swiftweasel.tuxfamily.org/](http://swiftweasel.tuxfamily.org/)
> [SIZE="4"]Optimization[/SIZE]

Swiftweasel is optimized using the following methods:

**Binary code optimization**
[list]
    [*] Compiled with options that optimize for speed rather than binary size.[list]
          [*] Swiftweasel is compiled -O3, (the highest level)[list]
                [*] The resulting Swiftweasel binary is larger than Firefox.[/list]
          [*] Firefox is compiled -Os (which is for binary size).[/list]
    [*] Binaries incorporate additional instruction sets.[list]
          [*] Intel and AMD: SSE, SSE2, SSE3, and MMX.
          [*] AMD only: 3DNow![/list]
    [*] Optimization specific to the build microprocessor architecture.[list]
          [*] Intel 32bit: Pentium 4, Pentium 3, Pentium M, Pentium 3M, Pentium 2, Prescott.
          [*] Intel 64bit: Nocona
          [*] AMD: Athlon XP, Athlon, K6-2, Athlon.
          [*] AMD64: Athlon64, Opteron[/list]
    [*] Compiled with newer version of GCC (Firefox 2.0 uses 3.3.2, Swiftweasel 2.0 uses 4.0.3).[/list]

**Increased Security**[list]
    [*] Better protection from Buffer overflow attacks (Swiftweasel 2.0 uses -D_FORTIFY_SOURCE=2; Firefox 2.0 uses gcc 3.x, which does not support this).[/list]

**Simplify**[list]
    [*] IPv6 DNS lookups are disabled, preventing slowdowns 
    [*] HTTP pipelining is enabled by default. Note that Fasterfox provides a GUI to adjust these settings.
    [*] For full details, users can download source packages with all changes listed.[/list]

---

