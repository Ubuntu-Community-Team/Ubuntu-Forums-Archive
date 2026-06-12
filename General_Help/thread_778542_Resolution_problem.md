---
title: "Resolution problem"
date: 2008-05-02
forum: General Help
---

### Post by Manu S S on 2008-05-02
I had installed Ubuntu from 'Ubuntu-Gutsy' installation CD in my laptop. After starting it up I changed the resolution to a new value. Now the screen is all blurred and I am unable to even see the link for changing resolution to get it back to the original correct value. So I am unable to use Ubuntu.:( Is there any way to reset the screen resolution without having to reinstall? 
Also please tell me which resolution will be most appropriate for my laptop. I am using a wide screen Compaq Presario V3000 lap.
Thanks in advance.

---

### Post by Zorael on 2008-05-02
Without having an inkling as to what might be wrong, try the following command, entered in a terminal.
```
$ sudo dpkg-reconfigure xserver-xorg
```
Then restart X with Ctrl+Alt+Backspace.

---

### Post by Manu S S on 2008-05-02
Thanks a lot... It worked... :) Now I am able to use Ubuntu but when I started an error message came up saying that "Graphic details could not be detected" and it was running on "low graphics mode". A message also came saying I have to manually configure the graphic settings for advanced effects. How do I do it?

---

