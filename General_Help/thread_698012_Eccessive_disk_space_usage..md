---
title: "Eccessive disk space usage."
date: 2008-02-15
forum: General Help
---

### Post by ele_mugv on 2008-02-15
I'd always wondered where all my disk space was going until yesterday when used the disk usage analyzer and found out that /var/cache/apt/archives has all the *.deb installation archives that i have ever installed...if i back these up on a dvd and delete them from my disk drive...what's gonna happen..is the earth gonna rotate in the opposite direction or is there absolutely no harm done? pls hlp!!

---

### Post by accatagon on 2008-02-15
Nope, nothing is going to happen. I wouldn't even bother backing them up. Just use "sudo apt-get clean" and they will go away ( you will need to download them again if you want to install them again). There's an outstanding bug about this somewhere but using the aforementioned command will clear it out for you.

---

### Post by accatagon on 2008-02-15
Actually, upon further research, you can delete all the packages under "preferences" in synaptic, under the "files" tab. You can also set the default behavior for removing packages. If you don't like the command line, you can use this option.

---

