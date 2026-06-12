---
title: "wine wont open .exes"
date: 2006-11-06
forum: General Help
---

### Post by leveliv on 2006-11-06
```
leveliv@leveliv-desktop:~$ wine "BitComent_0.70_Setup.exe"
wine: could not load L"c:\\windows\\system32\\BitComent_0.70_Setup.exe": Module not found

```

that's what I get...help me please :( (when i try to open any .exes)

---

### Post by Cable on 2006-11-06
Try typing your command without quotes around the file you're trying to open.

---

### Post by hikaricore on 2006-11-06
I see the immedate problem here.  It looks like you're not launching the program from the directory that it actually resides in.  I can see you're at your home directory in the terminal.  Is this where the BitComent_0.70_Setup.exe is?  Or did you mistakenly download it to your desktop and forget to switch to that location? If it's on your desktop try in the terminal from "home" aka: ~

```
cd Desktop
```

then

```
wine BitComent_0.70_Setup.exe
```

and make sure the file name is exact :)

This should launch the installer.

But on the other hand if you're just looking for a good bittorrent client (just a guess from the file name) there's dozens of decent ones availible for linux, some can even be accessed from Synaptic or even the Add/Remove application.  :)

Good luck,

--Aaron

---

