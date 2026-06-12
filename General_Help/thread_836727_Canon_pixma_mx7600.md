---
title: "Canon pixma mx7600"
date: 2008-06-21
forum: General Help
---

### Post by gianholland on 2008-06-21
Has anoyne gotten a canon pixma mx7600 to function properly under ubuntu 8.04

---

### Post by x1a4 on 2008-06-21
Canon does not, in any way, provide Linux hardware support for this printer.  They do, however, have [MacOSX CUPS drivers]("http://www.usa.canon.com/consumer/controller?act=ModelInfoAct&tabact=DownloadDetailTabAct&fcategoryid=334&modelid=16506").  If you can extract the files, and install them manually, you *might* be able to get it to work.  After all, CUPS is CUPS, regardless if it's running on Linux or OpenBSD (what OSX is based on).

EDIT: You can find information on how to open Mac's dmg files [here]("http://baghira.sourceforge.net/dmg.htm").  Or you can just mount the file.  DMG files are just disk images of Apple's file system: HFS.

to mount it:
```

sudo mount -t hfs -o loop printerdriver.dmg /mount/point

```

EDIT2: You must install the following packages first:
hfsplus
hfsutils
hfsprogs
libhfsp0

---

### Post by slickbob on 2008-12-12
Has anyone had success with this printer yet?

---

### Post by slickbob on 2008-12-26
I was able to get the printer to print this morning.  I intalled the cups-bjnp driver from: [http://sourceforge.net/projects/cups-bjnp/](http://sourceforge.net/projects/cups-bjnp/) then used the Canon PIXMA iP5300 - CUPS+Gutenprint v5.2.0-rc1 Simplified driver.

---

### Post by blueice_haller on 2009-01-02
Hello slickbob,
plese tell me, if scanning (e.g. with sane) with the Pixma MX7600 works, too.

If not, I will buy an HP, Epson or Brother with same features, instead.

---

### Post by slickbob on 2009-01-09
I haven't tried sane yet.  Support should be in the Sane CVS. Check out this blog post:  
[http://mp610.blogspot.com/2008/10/canon-pixma-scanners-are-now-network.html](http://mp610.blogspot.com/2008/10/canon-pixma-scanners-are-now-network.html)

---

### Post by pluMmet on 2009-07-11
> **slickbob said:**
> I was able to get the printer to print this morning.  I intalled the cups-bjnp driver from: [http://sourceforge.net/projects/cups-bjnp/](http://sourceforge.net/projects/cups-bjnp/) then used the Canon PIXMA iP5300 - CUPS+Gutenprint v5.2.0-rc1 Simplified driver.

I've installed the cups-bjnp driver

How do I "use" the gutenprint-5.2.4-rc1.dmg file?

---

### Post by pluMmet on 2009-07-12
Bump.

---

### Post by pluMmet on 2009-07-12
No love for the Canon mx7600?

---

### Post by mrchumpley on 2009-07-21
I too am thinking of getting this printer/fax/scanner but am not very expert with setting stuff up in Ubuntu. I have had a Canon S900 which I managed to get to work by following advice in the forums, but for some reason it has gone very temperamental!
Has anyone managed to get all the mx7600 functions working???

---

### Post by wsuetholz on 2009-09-16
I have one of these working with the above mentioned documents.  I was not able to mount the HFS images, so I used a MX860 printer type.  It seems to print the test page ok.

Unfortunately, Jaunty doesn't include sane 1.0.20 which includes the scanner drivers.  So, I'm in the process of searching for that package.

---

### Post by borepstein on 2011-03-15
I used the following to get it to print under CentOS 5.5:

[http://greg.porter.name/wordpress/?p=430](http://greg.porter.name/wordpress/?p=430)

Some variation thereof should work for Ubuntu too, I would think. However, thus far I have had no luck finding a way to get it to scan.

Boris.

---

