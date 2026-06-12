---
title: "Copy file from an old ubuntu on external usb"
date: 2020-08-05
forum: General Help
---

### Post by ckrles on 2020-08-05
Hi, I had xubuntu on an old hdd. I moved to an ssd. I copied all the information except for some files that I forgot. How can I copy those file through a usb external case?. That old hdd is mine and I installed xubuntu on it, so if necessary to use the password, I can do it.

Thanks.

---

### Post by CelticWarrior on 2020-08-05
It depends.

Was the installation encrypted or not? If not, it should be as easy as attaching the drive as external storage and then use the file manager to access it and copy the files.
If encrypted you need to first decrypt and mount it.

---

### Post by sudodus on 2020-08-05
You need some hardware:

- a USB to SATA adapter or external box (typical for a new laptop), or
- if you have an eSATA port in the computer (typical for an older laptop) it should work with an eSATA to SATA cable and a power cable and power supply, or
- if it is a desktop computer it should work with an extra SATA to SATA cable and an extra power cable (you can probably use the desktop computer's internal power supply)

in order to connect your drive externally.

---

### Post by ckrles on 2020-08-05
I think it wasn't encrypted. As a matter of fact, there are many files that I can copy, but that there are a few I can not copy and have denied access.
I am using an external usb case with that 2.5" hdd inside.

How can I get permission access to those files with denied access? It is just 7 or 8 files (jpeg).

---

### Post by ckrles on 2020-08-05
> **CelticWarrior said:**
> It depends.

Was the installation encrypted or not? If not, it should be as easy as attaching the drive as external storage and then use the file manager to access it and copy the files.
If encrypted you need to first decrypt and mount it.

> **sudodus said:**
> You need some hardware:

- a USB to SATA adapter or external box (typical for a new laptop), or
- if you have an eSATA port in the computer (typical for an older laptop) it should work with an eSATA to SATA cable and a power cable and power supply, or
- if it is a desktop computer it should work with an extra SATA to SATA cable and an extra power cable (you can probably use the desktop computer's internal power supply)

in order to connect your drive externally.

> **ckrles said:**
> I think it wasn't encrypted. As a matter of fact, there are many files that I can copy, but that there are a few I can not copy and have denied access.
I am using an external usb case with that 2.5" hdd inside.

How can I get permission access to those files with denied access? It is just 7 or 8 files (jpeg).


I think it wasn't encrypted. As a matter of fact, there are many files  that I can copy, but that there are a few I can not copy and have denied  access.
I am using an external usb case with that 2.5" hdd inside.

How can I get permission access to those files with denied access? It is just 7 or 8 files (jpeg).

---

### Post by sudodus on 2020-08-05
Have you tried to copy those files with the cp command using elevated (sudo) permissions in a terminal window?

```

sudo cp -i source-file target-directory

```

-i <--> interactive (warning so that you do not overwrite an existing file in the target directory).

---

### Post by ckrles on 2020-08-05
> **sudodus said:**
> Have you tried to copy those files with the cp command using elevated (sudo) permissions in a terminal window?

```

sudo cp -i source-file target-directory

```

-i <--> interactive (warning so that you do not overwrite an existing file in the target directory).


Yes, I have tried it. No success. Finally, I decided to temporarilly install the hdd back in the computer where it was. I accessed the system and copied the files without any problem.

Thanks.

---

