---
title: "Nvidia drivers, AMD X2 and Edgy"
date: 2006-10-27
forum: General Help
---

### Post by Ronbo on 2006-10-27
Can anyone point me to the solution that will allow me to install the Nvidia drivers and keep both cores of my AMD X2 3800, maybe utilizing the linux Generic kernel.  Last night I tried to install the drivers and Edgy kept wanting to install the linux-image-386 and linux-resticted-modules-386 (or whatever they are).  When I did it the first time and it reverted to the 386 kernel without dual core support, but with the Nvidia drivers.  I was wondering if there is a work around for this?

---

### Post by Aberrix on 2006-10-27
are you using the 32 bit or 64 bit version of ubuntu?

---

### Post by jmwyatt on 2006-10-27
I have the same processor and an Nvidia card... Generic worked for me. Try Automatix for the Nvidia installation.

---

### Post by Aberrix on 2006-10-27
if your on 6.06 Dapper use the k7-smp kernel

```
sudo apt-get install linux-k7-smp
```

otherwise, I am using the generic kernel with 6.10 Edgy and its utilizing both cores with no problems.

---

### Post by Ronbo on 2006-10-27
I am using the 32 bit version of Edgy.  Aberrix, did you install the Nvidia drivers?

---

