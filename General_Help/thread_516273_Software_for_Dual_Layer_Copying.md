---
title: "Software for Dual Layer Copying?"
date: 2007-08-03
forum: General Help
---

### Post by andrew.46 on 2007-08-03
Hi,

 Just picked up a dual layer dvd burner and a few dual layer discs. What software are people using to _legally_ decrypt and copy dual layer discs to iso and then burn onto blank discs?

              Andrew

---

### Post by andrew.46 on 2007-08-03
Hi again,

 Well I have pretty much found the solution that works for me:

```
vobcopy -v -m  /media/cdrom0
cd MOVIEFolder
mkisofs -v -dvd-video -o ../MOVIE.iso .
```

 Couldn't be easier could it? This presupposes that libdvdcss / libdvdread is present if you can legally copy commercial DVDs

             Andrew

---

