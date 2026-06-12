---
title: "Unable to Choose the 32 Bit Version With the 7.10 Installer"
date: 2007-12-30
forum: General Help
---

### Post by aidoru on 2007-12-30
I have installed the 64-bit version using the 7.10 installer.
I unistall that and delete the files.
Now i want to install the 32-bit version, but the installer doesn't ask me which version any more. I have tried many things but it seems that Wubi have saved the information somewhere and doesn't ask me any more which version i want to download.I'm downloading the iso manually, but i would know if there is another way to solve this problem, even because my internet connection is a bit slow. Thanks to all.

---

### Post by Knoll318 on 2007-12-30
Wait, what?  I think it backed up the ISO, so you could try to go to Wubi unistaller and choose to back up nothing.

---

### Post by flamelab on 2007-12-30
Through cmd you do this 

(We suppose that you have downloaded the wubi installer on C:\Downloads so you do 

```
cd C:\Downloads\Wubi-7.10-alpha-rev386.exe
```

then 

```
Wubi-7.10-alpha-rev386.exe --32bit
```

and it will download the 32 bit version .

---

