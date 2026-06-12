---
title: "HELP! Wine hates me!"
date: 2007-06-10
forum: General Help
---

### Post by GeekyWill on 2007-06-10
So I just installed Ubuntu Feisty on my machine yesterday, and started looking for ways to play my Windows games and use some of my old apps. I quickly found Wine, followed there installation page, and it installed fine. The tabs in the Accessories bar were there, along with the uninstaller in the Systems Tools bar. The program started and worked fine.
         Soon after I wanted to check the status on some debit cards online. The sites required IE to work, so I went looking for a Linux compatible one, and found IE4Linux. I followed the instructions and was soon using IE to check my balances. However, when I went to install some games through Wine, it wasn't in the Accessories tab. Puzzled, I went and completely removed the prgram and then reinstalled the application, to no effect. Finally, I removed IE4Linux, along with the changes it made to my sources.list. Still no Wine. I have checked my file system, and there is no .wine folder, even though Add/Remove Applications and Synaptic Package Manager both say it is installed. 
      Someone please help me!:(

---

### Post by tpg on 2007-06-10
If you go into a terminal and type "wine", what happens?
Also, what happens if you type "ls -al ~/.wine"?

---

### Post by GeekyWill on 2007-06-10
Thanks.  Just typing "wine" in the terminal gives me the program arguements. The second one says there is no such file or directory.:(
Please, any other ideas?

---

### Post by tpg on 2007-06-13
Sorry for the delay! Try running
```
sudo dpkg-reconfigure wine
```
to reconfigure the wine package, and see if that recreates your .wine directory. I've never had this problem before, so I'm just guessing! :)

---

### Post by cookies on 2007-06-13
If you type winecfg in a Terminal, what happens? It should recreat ~/.wine

---

### Post by Citizin on 2007-06-13
I dont suggest using WINE, google a program called Crossover Linux :)

---

### Post by misha680 on 2007-06-14
ies4linux uses a different prefix than .wine (I think .ies4linux).
To use wine just go into the directory of an .exe you have (e.g. an installer for some program you'd like to install), and then type:

```
wine nameofyourprogram.exe
```

If you'd like to just create the .wine directory for some reason, without running any programs, you can type:

```
wineprefixcreate
```

Also, if you need to configure thins in wine try:

```
winecfg
```

Misha

---

### Post by Nythain on 2007-06-14
crossover not that great, not quite as functional as wine, it spends to much time focusing on just a handfull of apps... and it costs money, wine is free

winecfg as mentioned will set up wine, wich includes making the ~/.wine directory and the windows directory structure under that (~/.wine/drive_c/)

once you have that going, wine should work well... you just use wine by typing wine /path/to/whatever.exe and it will use wine to run it...

keep in mind wine wont run everything, and some things it will run but not great, but for the most part its awesome

---

### Post by tpg on 2007-06-14
> **Citizin said:**
> I dont suggest using WINE, google a program called Crossover Linux :)
The OP implied that he wants to use it to play games, so if looking for a commercial version of wine, Cedega might be more appropriate.

---

