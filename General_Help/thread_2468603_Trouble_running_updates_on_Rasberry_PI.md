---
title: "Trouble running updates on Rasberry PI"
date: 2021-11-04
forum: General Help
---

### Post by taspenwall on 2021-11-04
[COLOR=#1A1A1B][FONT=&quot]I have a rasberry pi running 21.10 and I'm having some trouble running updates. When I log on it says I have 7 update to apply. When I run apt-get upgarde it says 0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded. The 3 kept back are[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]linux-headers-raspi linux-image-raspi linux-raspi[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]What else do I need to run to make sure I'm running all the updates that I can? Thanks I'm still learning[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]Edit It's a headless server running ubuntu server so no gui.[/FONT][/COLOR]

---

### Post by TheFu on 2021-11-05
Please show the exact commands and exact output - wrapped in 'code tags' in these forums.  Often, when people are new, they misinterpret what is actually happening and leave out critical details.
  [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) - code tags how-to.

---

### Post by grahammechanical on 2021-11-05
I do not think that you have a problem. On my desktop Ubuntu install I often see that there are updates but there can also be some packages kept back. There are reasons for this. The packages that are kept back may also depend on other packages that have not yet been upgraded and are not yet put in the repositories. This situation may rectify itself over the next few days.

You are about to get a kernel upgrade but all the parts to the kernel must be upgraded at the same time otherwise the OS will break.

Regards

---

