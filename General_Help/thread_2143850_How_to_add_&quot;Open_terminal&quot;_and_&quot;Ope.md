---
title: "How to add &quot;Open terminal&quot; and &quot;Open As Root&quot; in Nautilus (AKA Files)"
date: 2013-05-10
forum: General Help
---

### Post by _sluimers_ on 2013-05-10
[EDIT]

Thanks to georgelappies ¨Open terminal¨ is simply solved by:
```
sudo apt-get install nautilus-open-terminal && nautilus -q
```

I guess the second one needs Nautillus-Actions Configuration Tool.

Add in the Action tab the following:

Context label:
```
Open as root
```

Then go to tab Command tab and add:

Label:
```
Open as root
```
Path:
```
gksudo 
```
Parameters:
```
"nautilus --browser %U"
```

After building it you have to restarting nautilus by typing ```
nautilus -q
```
in the terminal.

I&#7743; still not done yet as I would like to add a red backround after an "open as root" to distuinguish it from normal nautilus, but I don know how,
does anyone?
[/EDIT]

---

### Post by georgelappies on 2013-05-10
To have the option 'Open Terminal' you have to first run:

```

sudo apt-get install nautilus-open-terminal

```

Then reboot the machine.

---

### Post by _sluimers_ on 2013-05-10
Reboot!? Since when does Ubuntu need rebooting?

---

