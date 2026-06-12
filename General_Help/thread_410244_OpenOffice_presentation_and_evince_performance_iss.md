---
title: "OpenOffice presentation and evince performance issues"
date: 2007-04-15
forum: General Help
---

### Post by lamadredelsapo on 2007-04-15
I have a big problem with open office, whenever I try to view a presentation created with MS Office the processor runs at 100%. I don't know why this is happening. Could it be a graphics driver problem? I'm running dapper (2.6.15-28-k7) with the latest nvidia drivers.

I also have problems with evince, when I navigate through a pdf document my processor goes wild (100% usage) and it doesn't let me read the document.

---

### Post by kerry_s on 2007-04-15
Provide your specs please.

---

### Post by lamadredelsapo on 2007-04-15
Athlon XP 3000+ 1280MB RAM Geforce 6800

---

### Post by lamadredelsapo on 2007-04-16
No one had this problem?

---

### Post by kostkon on 2007-04-16
There is an option in *Openoffice* to select if you want to use *OpenGL* to display the presentations. Do you have this option checked. Maybe, if you select it your problem will be solved. Also, If you have it checked, uncheck it to see what happens.

Now, about* Evince*, it very strange, because for me with a less powerfull configuration than you, *Evince* is very fast even for large PDFs (>50MB).

---

### Post by lamadredelsapo on 2007-04-16
Thanks for the tip, it is working properly now. It appeared to be I had the "Use Hardware Accelaration" option activated. I switched it off and it is all working: MS PowerPoint presentations now go really smooth.

Even though evince is still a big mistery.

---

### Post by lamadredelsapo on 2007-04-16
I removed evince and switched to acroread, I know it's not free software but at least it works fine for me. It's a pity because i liked evince.

---

### Post by kostkon on 2007-04-16
I think libpoppler, which* Evince* uses to render PDFs, has problems with some PDF documents. 

Furthermore, *libpoppler* uses *Cairo* for outputting the PDFs. I think *Evince* is compiled with *Cairo* that uses the *glitz* library to provide hardware accelereted graphics using *GLX*. Thus, there is no coincidence that when you deactivated *OpenGL* from *Openoffice* everything worked OK.

Thus, there are two cases: Your PDFs are the ones that *Evince* has trouble to read or you have some problem with the 3d acceleration of your card. Do you use the drivers from nvidia?

---

### Post by lamadredelsapo on 2007-04-16
As i posted I'm using the latest nvidia driver, i should check xorg configuration

---

### Post by ricardisimo on 2007-11-02
I'm having a strange problem where evince is opening PDFs (very, very slowly, if at all) as though they were wall poster-sized, ridiculously large, where maybe the first letter or two of the document are on screen. I've tried all of the obvious viewing options, to no avail... it won't shrink down. The weirdest part is the memory usage shooting up so high. I don't get the logic. Even if it thinks the document is enormous, why would the amount of information be any different? Thanks.

---

