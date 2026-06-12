---
title: "wine help please"
date: 2007-04-09
forum: General Help
---

### Post by RiPPeR777 on 2007-04-09
ripper@ripper-desktop:~$ wine SteamInstall.exe
wine: could not load L"c:\\windows\\system32\\SteamInstall.exe": Module not found

im trying to install cs:s and steam but i can seem to get this working i so new at linux its sad, i read alot of forms and it says i have to download this fount and i did and put it into te directory and they said it should work after that but as you can see it is not woking please help

---

### Post by hikaricore on 2007-04-09
Just a thought, unless SteamInstall.exe is in your /home/ripper directory (aka ~)  you need to change directories to the one it's in:

Example
```
 cd ~/Desktop
```

If it's on your desktop.

---

### Post by RiPPeR777 on 2007-04-09
i figurd it out SteamInsall was a msi extenton not an exe

---

### Post by secular on 2007-04-09
Check Franks' Corner to see how to install a .msi: [http://frankscorner.org/index.php?p=msi]("http://frankscorner.org/index.php?p=msi")

---

### Post by machoo02 on 2007-04-09
did you check out the [CounterStrike page at the WINE AppDB]("http://appdb.winehq.org/appview.php?iVersionId=3731")?

---

