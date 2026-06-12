---
title: "Nero Linux 3.5.0.1 not working with 4.4.x.x kernels..."
date: 2018-01-31
forum: General Help
---

### Post by omelette on 2018-01-31
Hello.  I've just upgraded my Ubuntu setup from kernel 3.9.x.x to 4.4.0.111 and found that Nero Linux can no longer detect my USB CD/DVD burner. Booting with 3.3.x.x everything works perfectly. The Nero Linux manual mentions the /proc/scsi/scsi item list (drive listed) and the 'sg' kernel module (loaded, as it's built-in) as being possible culprits but both check out ok.

Has anyone come across this problem and is there an easy solution?

---

### Post by mc4man on 2018-01-31
Maybe find yourself a .deb of 4.0.x, it's only 3 years old vs. 9+ for 3.5.0.1

---

### Post by #&amp;thj^% on 2018-01-31
> **mc4man said:**
> Maybe find yourself a .deb of 4.0.x, it's only 3 years old vs. 9+ for 3.5.0.1

+1^^^^^^
Maybe here: [http://www.nero.com/enu/downloads/previous-versions/download-linux4-update.php](http://www.nero.com/enu/downloads/previous-versions/download-linux4-update.php)
System Requirements:
```
General

    Linux kernel 2.4 or higher (2.6 recommended) with X-Window
    Glibc 2.3.6 and libstdc++6 4.1.1 (or higher)
    GTK+ 2.8.0 (or higher)

Processor and installed memory

    800 MHz Intel® Pentium® III processor, AMD Sempron&#8482; 2200+ processors or equivalent, 128 MB RAM

Hard disc space

    50 MB for program installation

Supported Distributions*

    Red Hat Enterprise Linux 5
    SuSE Linux 10.3
    Fedora 7
    Debian GNU/Linux 4.0
    Ubuntu 7.04

Supported Languages

    Nero Linux currently supports 23 languages

Supported Recorders

    All CD, DVD, and Blu-ray recorders

Optional requirements

    Sound device and speakers

```

* Nero Linux 4 supports all higher versions of the above supported distributions

---

### Post by omelette on 2018-02-01
> **mc4man said:**
> Maybe find yourself a .deb of 4.0.x, it's only 3 years old vs. 9+ for 3.5.0.1

Thanks for the responses guys.

Nero Linux 4 is too buggy - failure when attempting Continuation of a DVD-write being the one that had me going back to NL 3, but it had other problems as well.

---

### Post by mc4man on 2018-02-01
For me the best burning program by far is ImgBurn. There isn't a linux version but it works fine thru wine.

---

### Post by omelette on 2018-02-08
> **mc4man said:**
> Maybe find yourself a .deb of 4.0.x, it's only 3 years old vs. 9+ for 3.5.0.1

Quick note, out of curiosity I downloaded & installed the Nero Linux 4 'update' linked to here - this doesn't detect my external Lite-on USB drive either!  I'm putting the blame squarely with the 4.4.x.x kernel developers because as has been noted, Nero Linux versions have been around for years!  Even so, they are imo still the best burning softwares Linux has had, so someone should have checked for breakages.

Incidentally, I've had another 4.4.x.x kernel issue as well.  My 240GB Transcend SSD works perfectly with all kernels up to 4.4.x.x  Try booting with these and I am treated to a 'validation failed (errno=-2)' error and dropped to the initramfs prompt - so this SSD is completely useless with all 4.4.x.x kernels that I have tried, and there's been a few!  Sucks.

---

