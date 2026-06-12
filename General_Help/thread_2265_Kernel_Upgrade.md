---
title: "Kernel Upgrade"
date: 2004-10-26
forum: General Help
---

### Post by SVen2000 on 2004-10-26
As I upgraded from Debian Sarge, how to install ubuntu kernel?

When trying to apt-get install linux-386, i get a lot of errors!

btw: which one is the correct kernel for athlon xp maschines?

---

### Post by HungSquirrel on 2004-10-26
AthlonXPs are K7 processors, so the -k7 kernel is the one you want.  ;)

---

### Post by SVen2000 on 2004-10-27
[B]Richte linux-image-2.6.8.1-3-k7 ein (2.6.8.1-16) ...
/usr/sbin/mkinitrd: line 1259: mkext2fs: command not found
Failed to create initrd image.[/B]

Wo krieg ich dieses mkinitrd her?

---

### Post by plasmo on 2004-10-27
would a i686 work for althonxp or just the k7 ? :s

---

### Post by fng on 2004-10-27
i recommend  k7 for an athlonxp

---

### Post by SVen2000 on 2004-10-27
[QUOTE=SVen2000][B]Richte linux-image-2.6.8.1-3-k7 ein (2.6.8.1-16) ...
/usr/sbin/mkinitrd: line 1259: mkext2fs: command not found
Failed to create initrd image.[/B]

Wo krieg ich dieses mkinitrd her?[/QUOTE]

I just realized I posted in German and the question was also wrong ... uh, was I drunk?

It should be:

Where can I get this mkext2fs ???

---

### Post by FLeiXiuS on 2004-10-27
To create your own initrd under Ubuntu, you will want to install the initrd-tools package. You can then customize to your heart’s content using the /etc/mkinitrd configuration directory.

sudo apt-get install initrd-tools 

Universe may be needed!

---

### Post by adbak on 2004-10-27
i386 is all Pentiums and Intel (I believe)
i586 is for Pentium III (I believe)
i686 is for Pentium IV
K6 is for all Athlons (perhaps)
K7 is for Athlon XP

---

### Post by Werpon on 2004-10-27
[QUOTE=adbak]i386 is all Pentiums and Intel (I believe)
i586 is for Pentium III (I believe)
i686 is for Pentium IV
K6 is for all Athlons (perhaps)
K7 is for Athlon XP[/QUOTE]
 i586 -> Pentium
i686 -> Pentium Pro / Pentium II

---

### Post by oddabe19 on 2004-10-27
[QUOTE=adbak]i386 is all Pentiums and Intel (I believe)
i586 is for Pentium III (I believe)
i686 is for Pentium IV
K6 is for all Athlons (perhaps)
K7 is for Athlon XP[/QUOTE]

i386 is for anything
i486 is for 486's and up
i586 is for pentiums and up
i686 is for PII/ Pro and up
k6 is for Older AMD's (k6 based) and up
k7 is for Athlon XP's/ Duron/ etc.... basically 1ghz and up
smp is for multiple processors
64 is well, for 64 bit
bigmem is for big memory (over 2 gigs i believe? or is it 1 gig?)

---

### Post by SVen2000 on 2004-10-27
[QUOTE=FLeiXiuS]To create your own initrd under Ubuntu, you will want to install the initrd-tools package. You can then customize to your heart’s content using the /etc/mkinitrd configuration directory.

sudo apt-get install initrd-tools 

Universe may be needed![/QUOTE]

initrd-tools are already installed ...

---

