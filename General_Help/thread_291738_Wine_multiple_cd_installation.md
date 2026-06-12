---
title: "Wine multiple cd installation"
date: 2006-11-02
forum: General Help
---

### Post by morgue on 2006-11-02
I'm trying to setup a game with wine, it has 2 cds, I insert disk 1, run setup.exe and the installation gets to 50% now it's asking me for disk 2, but I can't eject the cd from the drive.

When I run 
```
$ lsof | grep cdrom

```

I get
```

bash      10583     morgue  cwd       DIR        3,0      2048      3904 /media/cdrom0
wineserve 10646     morgue   37r      REG        3,0 666107212      3926 /media/cdrom0/compressed.zip

```

What should I do? :confused:

---

### Post by morgue on 2006-11-02
bump

---

### Post by morgue on 2006-11-03
I'm not able to load the setup.exe from outside the directory where it is (cdrom) (which I find weird) which I think it's my problem :confused:

---

### Post by morgue on 2006-11-03
Ok I was able to load setup.exe from using: 
wine /media/cdrom0/setup.exe

I installed the game, when prompted for disk 2 I just took out cd 1, inserted cd2 and remounted using
mount /media/cdrom0/

Now I'm trying to run the game but I get this error when running the .exe
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135

Any suggestions? Thanks.

---

### Post by jaytek13 on 2006-11-03
You may try the appdb at winehq.com. A lot of problems are specific to the particular game, and if you do a search for your game you may find someone else who has had the same problem and knows how to fix it.

---

### Post by rkrisher on 2008-06-13
I just discovered by playing around and tested a way to do it.  Spreading it around to a lot of posts because I've been searching for months.

in terminal or under start/run, type "wineconsole cmd"

This brings you to a windows like dos terminal.

change into your CDROM disk typing "d:" or whatever your drive letter is

type in your setup program name, i.e.: "setup.exe" or "install.exe"

the install will start. Change to your C drive with "C:"

When prompted for disk x, type in "eject"

insert next disk and continue.

Repeat until application is complete.

Remember to let your CD auto-mount by selecting "open in window" or manually mount it before clicking OK at the "Insert CD X" prompt.

Hope it helps.

BTW, you need to use dos commands when exploring around in the command prompt.  Like "dir" instead of the "ls" we got used to.

---

