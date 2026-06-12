---
title: "bootchart not working?"
date: 2007-10-21
forum: General Help
---

### Post by juicymixx on 2007-10-21
Hey everyone,

  I installed bootchart (0.9-0ubuntu7) recently since I've been having longish startups since I switched to gusty.   After installing I don't seem to have any info left in 
/var/log/bootchart
(and there isn't a /var/log/bootchart.tgz either)
Posts I've seen say to install the 0.83 deb, which makes me wonder if 0.9 works at all..?   Should something have been added to my grub menu.lst?   Nothing changed in it.   I added:
init=/sbin/bootchartd
to the kernel line as per [http://www.bootchart.org/docs.html](http://www.bootchart.org/docs.html) however this dropped me to a prompt after boot.   Also, there doesn't appear to be a 'bootchartd' in /sbin either.

  I've completely uninstalled and reinstalled bootchart via synaptic now, and there's still no effect.

---

### Post by chrisccoulson on 2007-10-21
The bootchart stuff should be built in to the initramfs. Do you have a script at /usr/share/initramfs-tools/scripts/init-top/bootchart? Try doing:
```
sudo update-initramfs -c -k `uname -r`
```

..although, this should have happened when you installed the package

---

### Post by juicymixx on 2007-10-22
well that did it...   It's working now!   Thanks!:)

---

