---
title: "ATi&amp;LinuxWiki: Ubuntu_Dapper_Installation_Guide woes"
date: 2006-11-20
forum: General Help
---

### Post by redbluemangle on 2006-11-20
I'm trying to instal the drivers for my Radeon 9550 card and all was going well with this wiki ([HERE]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_new_driver"))
untill I got to this step: 

Create .deb packages:
```

bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper
```

where I just get the "no such directory" error. I have downloaded the file to my homefolder. What am I doing wrong?

---

### Post by Foxmike on 2006-11-20
> **redbluemangle said:**
> I'm trying to instal the drivers for my Radeon 9550 card and all was going well with this wiki ([HERE]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_new_driver"))
untill I got to this step: 

Create .deb packages:
```

bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper
```

where I just get the "no such directory" error. I have downloaded the file to my homefolder. What am I doing wrong?

What do you get if you do instead:
```
./ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper
```
?

---

### Post by Foxmike on 2006-11-20
Of course this is assuming you are in your download path.  If you are not, then CD to it and then copy/pase the above command:D

---

### Post by redbluemangle on 2006-11-23
ok it turns out i just had to add .bin at the end of the package name but now that I get an error when i'm uncompressing the driver:

```

user@host:~/Desktop$ bash ati-driver-installer-8.29.6.run.bin --buildpkg Ubuntu/dapper
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.29.6
.........................................................
.........................................................
.........................................................
........................................................
Extraction failed........Signal caught, cleaning up


```

---

