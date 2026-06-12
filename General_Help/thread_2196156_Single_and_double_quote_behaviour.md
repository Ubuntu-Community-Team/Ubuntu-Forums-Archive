---
title: "Single and double quote behaviour"
date: 2013-12-28
forum: General Help
---

### Post by Macamba on 2013-12-28
In my new Ubuntu installation I suddenly have behaviour I know from Windows, and absolutely detest. When I press a (double) quote the system waits for the next character to decide what needs to be done. A single quote and a becomes a
```

á

```

A double quote and a becomes a
```

ä

```

I circumvent this in Windows by choosing the American English keyboard. What should I do in Ubuntu?

=====
I read [something]("http://ubuntuforums.org/showthread.php?t=982761") about 
```

sudo dpkg-reconfigure console-setup

```
This resulted in a 'Package configuration' window where 'UTF-8' was selected. When I press Enter I get a 'Configuring console-setup' window, with the following line selected:
```

. Combined - Latin; Slavic Cyrillic; Greek 

```

But I'm unclear what I need to do.

---

### Post by jim_deadlock on 2013-12-28
If you go into Settings -> Region & Language then you can choose your language and keyboard settings. Seems like you've got a foreign keyboard layout there.

---

### Post by Impavidus on 2013-12-28
Check your keyboard configuration. You want a keyboard without dead keys. The dead keys are what generates the accented characters after typing `, ', ^ or ".

---

### Post by Macamba on 2013-12-29
Thanks. That helped. I finally clicked on the En icon in the top bar. In it there is a 'Text entry settings' menu item. There where two entries, 'English (US)' and 'English (US, with dead letters)' (or something like that). I removed the dead letter entry (select it, and press the minus sign). Now the (former) dead characters are displayed immediately on pressing.

(FWIW, running 13.10)

---

