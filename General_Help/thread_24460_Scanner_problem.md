---
title: "Scanner problem"
date: 2005-04-07
forum: General Help
---

### Post by Bhliljor on 2005-04-07
My Epson scanner Perfektion 3170 Photo does not work with Sane in Ubuntu. They are in diffrent places in Ubuntu but cannot reach each other. What to do ?Please help me !
 
Roland

---

### Post by Bhliljor on 2005-04-09
I have found the solution for my Epson scanner here: [http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html) 

Roland   :-D

---

### Post by Pink Chick on 2005-06-27
[QUOTE=Bhliljor]I have found the solution for my Epson scanner here: [http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html) 

Roland   :-D[/QUOTE]
 How did you install it? Can you describe the procedure, I read a lot about it, and a lot of people are writing about installation ore compiling errors.

---

### Post by LordBug on 2006-01-31
Dredging up an old thread, since I could use the answer to this as well.  Sane 1.0.13-2, Sane-utils 1.0.15-9, Libsane-extras 1.0.15-9 from Synaptic, and Iscan from the website listed above.  sane-find-scanner finds it, scanimage -L finds it.  Xsane and Iscan can't communicate.  Not sure where it's going wrong.

Figured it out.  I had to manually hack Iscan in, as there's a file conflict (a manpage) between the Iscan install package (RPM, converted to DEB via Alien) and the libsane-extras package.  Then, I needed to install the Iscan GT-9400 Plugin package (also converted via Alien).  After that, Iscan and Xsane both work perfectly.

---

### Post by joey111 on 2006-02-08
for me it worked (epson perfection 2480 photo);
i lakced the Libsane-extras 1.0.15-9. thx guys:mrgreen:

---

### Post by kpictjl on 2006-12-14
my solution to make the epson scanner work is here...

[http://ubuntuforums.org/showthread.php?t=143504&page=2](http://ubuntuforums.org/showthread.php?t=143504&page=2)

---

