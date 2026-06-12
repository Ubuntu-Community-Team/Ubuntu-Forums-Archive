---
title: "Breezy not an upgrade from Hoary ?"
date: 2005-10-22
forum: General Help
---

### Post by cyberchrist on 2005-10-22
Hello,

How comes that :

- a fresh install of Ubuntu Hoary (version 5.04) detects and installs well my graphical card;
- a fresh install of Ubuntu Breezy (version 5.10) does not.

???


I did not change any material component between the two installs.
With Hoary I can play glxgears at 1400 fps whereas Breezy lets me with a score of only 100 fps.

Breezy 10 times slower than Hoary.

I thought Breezy would be at least AS good AS Hoary at openGL.


From what i've read, we must have a hard time to get the Hoary drivers to work under Breezy, if it can be done at all (I didn't manage to).

Back to Hoary here.

---

### Post by SickTwist on 2005-10-22
What kind of graphics card do you have (manufacturer and model)? If you are not sure, open a terminal ( Applications --> Accessories --> Terminal ) and run the command "lspci -vv" (without quotes). Post the output here.

---

### Post by cyberchrist on 2005-10-25
ATI Radeon Mobility 9000.


```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Radeon Mobility 9000 M9] (rev 02) (prog-if 00 [VGA])
```

---

