---
title: "Sound out after suspension"
date: 2008-06-18
forum: General Help
---

### Post by kpsk on 2008-06-18
When I put my laptop into suspension and close it, the sound does not work once I return from suspension mode.If it helps at all I am using an Intel chipset with an integrated sound card. 

Does anyone know of any quick fixes to this problem? 

Thank you for your help.

---

### Post by Exsecrabilus on 2008-06-18
> **kpsk said:**
> Does anyone know of any quick fixes to this problem?
Don't suspend.

---

### Post by tedrampart on 2008-06-26
I've had this problem as well in hardy, when I _searched_, I found I could do one of the following:

1.```
sudo /etc/init.d/alsa-utils restart
```
2.```
sudo alsa force-reload
```

which ever one works, you could try creating that into a script inside the /etc/acpi/resume.d folder with a weight heavier than the sound.sh so it does it everytime you resume from suspend.. might help..

---

