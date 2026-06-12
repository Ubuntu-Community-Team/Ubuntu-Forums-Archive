---
title: "Mysterious file on my desktop"
date: 2007-11-13
forum: General Help
---

### Post by 01000111 on 2007-11-13
I'm running Ubuntu 7.10 with the KDE desktop. Since I installed KDE, the file .directory keeps appearing on my desktop. I've tried deleting it, but it reappears at the next reboot.   How do I get rid of this?  Should I?

I'm relatively new to Linux, so answers should be phrased for an advanced newbie. Thx.

Binary-G


File contents:

[Desktop Entry]
Encoding=UTF-8
Type=Directory
BgImage=
Icon=desktop
Name=Desktop
Name[af]=Werkskerm
Name[ar]=&#1587;&#1591;&#1581; &#1575;&#1604;&#1605;&#1603;&#1578;&#1576;
Name[az]=Masa Üstü
Name[be]=&#1055;&#1088;&#1072;&#1094;&#1086;&#1118;&#1085;&#1099; &#1089;&#1090;&#1086;&#1083;
Name[bg]=&#1056;&#1072;&#1073;&#1086;&#1090;&#1077;&#1085; &#1087;&#1083;&#1086;&#1090;
.
. <snip>
.
Name[wa]=Sicribanne
Name[zh_CN]=&#26700;&#38754;
Name[zh_TW]=&#26700;&#38754;

---

### Post by JasonF on 2007-11-13
KDE, or some other software, might be creating it as a method to indicate that it is, in fact, desktop directory (I believe all the the file is just a bunch of translations of the word Desktop).. The '.' in front of the name indicates that it should be a hidden file. So maybe try turning off the view of hidden files in the file manager and enabling it only when required.

---

### Post by 01000111 on 2007-11-13
> **JasonF said:**
> The '.' in front of the name indicates that it should be a hidden file. So maybe try turning off the view of hidden files in the file manager and enabling it only when required.

Thanks, but I've already tried that.  I have both Dolphin and Konqueror set to not show hidden files.  Is there somewhere else where it needs to be set?

G.

---

### Post by JasonF on 2007-11-13
I'm not running KDE, but google says to look for the Desktop Behavior configuration. Maybe on the right-click menu of the desktop, or in the Control Center. And un-select show hidden files there.

---

### Post by 01000111 on 2007-11-13
That did it.  Thanks.

G

---

