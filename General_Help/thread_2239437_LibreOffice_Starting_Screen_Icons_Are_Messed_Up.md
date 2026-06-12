---
title: "LibreOffice Starting Screen Icons Are Messed Up?"
date: 2014-08-13
forum: General Help
---

### Post by JosephBeck on 2014-08-13
Ubuntu 14.04.1 (Unity)

[ATTACH=CONFIG]255455[/ATTACH]

As you can see here, the icons on the left side are off. I am unsure why. I upgraded to 4.3, had some issues so purged it and reinstalled 4.3 via PPA. Installing it from the .deb doesn't help any. I tried on LinuxMint and the icons stayed blacked. Anyone else having this issue or know how to fix it? I included this issue in a bug report when it happened on mint but they simply suggested I turn off high contrast. My icons are not set to high contrast and these are the only icons with a problem. Minor gripe I know but I just want to know whats going on with it.

---

### Post by fantab on 2014-08-14
That looks like 'high-contrast' is automatically being detected. What gtk-theme do you have?
Open any office app like Libreoffice Writer and navigate to: Tools -> Options -> Libreoffice -> Accessiblity and check/uncheck "automatically detect high contrast mode of operating system". Restart Libreoffice.

---

### Post by JosephBeck on 2014-08-14
> **fantab said:**
> That looks like 'high-contrast' is automatically being detected. What gtk-theme do you have?
Open any office app like Libreoffice Writer and navigate to: Tools -> Options -> Libreoffice -> Accessiblity and check/uncheck "automatically detect high contrast mode of operating system". Restart Libreoffice.

It was unchecked by default, and that screen is the only one with that icon problem. The actual programs are working with the icons I have set. I checked automatically detect high contrast, closed, reopened, then unchecked it off and reopened again. No go sadly.

---

### Post by JosephBeck on 2014-08-15
Bump.

---

