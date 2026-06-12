---
title: "Installing Windows fonts"
date: 2007-11-27
forum: General Help
---

### Post by nandorj78 on 2007-11-27
Hi,
I would like to have some specific fonts in my Ubuntu that I had installed on windows before. How do I install them one by one, or a simply batch installation of them all?

Is it simply by copying them to the linux font folder?

thanks!

---

### Post by viking777 on 2007-11-27
Start/AddRemove programs then make sure that the 'show unsupported and proprietary software' boxes are ticked (allow it to update if necessary) and then search for 'fonts' and install Microsoft core fonts. 

If that doesn't include the ones you want then I can't really help you.

---

### Post by nandorj78 on 2007-11-27
Yeah, but those are not the fonts I want, thanks anyway.

Anybody else that could help me?

thanks

---

### Post by andref on 2007-11-27
try to copy microsoft fonts in a directory called "Fonts" in your own directory

ciao ciao!

---

### Post by nandorj78 on 2007-11-27
I dont believe the fonts I want to add are from Microsoft, they're fonts taken from font sites like dafont.com for example.

Microsoft fonts or not, will it work?

---

### Post by andref on 2007-11-27
> **nandorj78 said:**
> I dont believe the fonts I want to add are from Microsoft, they're fonts taken from font sites like dafont.com for example.

Microsoft fonts or not, will it work?

well if you don't have a win partition where find the fonts, you can download them from the site and add them in usr/share/fonts/truetype

---

### Post by mbeierl on 2007-11-27
You can install ANY true type font with the following howto:

[https://help.ubuntu.com/community/FontInstallHowto](https://help.ubuntu.com/community/FontInstallHowto)

Basically, it just comes down to copying the .ttf files into /usr/share/fonts/truetype/ and then running ```
sudo fc-cache -f -v
```

---

