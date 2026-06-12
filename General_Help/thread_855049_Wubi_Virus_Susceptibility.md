---
title: "Wubi Virus Susceptibility?"
date: 2008-07-10
forum: General Help
---

### Post by Helical on 2008-07-10
Hi, I was just curious as to weather Wubi was just as secure as Ubuntu being on it's own partition? Since it's on the same partition as my Windows files, if I for example downloaded a Windows virus would my Windows get infected? I know Ubuntu itself doesn't really have viruses - I'm just talking about Windows viruses getting in through Wubi.

Thanks and sorry for the newb questions.

---

### Post by gunashekar on 2008-07-10
I don't know about WUBI. My client's sysadmin accused me that my ubuntu laptop was responsible for introducing malware/viruses into his network when I did some work at their office.

---

### Post by minhmeoke on 2008-07-10
Wubi will not be affected by Windows viruses. Wubi is almost identical to the standard Ubuntu installation, except for the fact that everything is inside a file on the Windows partition. Therefore it cannot run windows executables (including viruses). The only way you can get a virus from Wubi is if you download something containing a virus, transfer the file to Windows, boot Windows, and then run the virus from Windows.

I would also advise you to avoid hard-reboots: do not push the power button on the computer if it freezes in Wubi, since this has a chance of causing filesystem corruption. Instead, hold the "magic" alt-sysreq combination and then press reisub to shut down the computer. [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

