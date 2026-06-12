---
title: "Strange XP phenomenon after using Feisty for a while"
date: 2008-01-08
forum: General Help
---

### Post by eternicode on 2008-01-08
Alright, I've had Kubuntu Feisty installed for a couple of months now and love it.  I set it up to automatically mount my Windows XP partition automatically at boot so I could work with the documents I had on that drive.

I just recently resized the Windows partition (shrank it....again!), which meant I had to boot into Windows for a disk check.  I decided to check out my disk usage using WinDirStat...

[ATTACH]55717[/ATTACH]

I have a grand total of *two* windows folders: C:\WINDOWS and C:\windows.  Funny thing is, is that in the Explorer tree pane, I can dropdown the C:\WINDOWS, but not the C:\windows.  Also, C:\windows subdirectories take me to the identical subdirectories under C:\WINDOWS.  If I try to delete either one to the Recycle Bin, it says C:\windows is a system directory, and required for proper functionality, etc.

To all intents and purposes, this looks like a Linux hard link...

Under Windows, on NTFS :confused:

I do know that, under linux (probably mostly under System Rescue CD), I had moved some files around using /mnt/windows/windows (instead of /mnt/windows/WINDOWS) a couple of times, but this doesn't really explain it to me.

How can I get rid of this "duplicate" windows directory?  Any clue?  I'd really like to claim back the 4GB it's taking ;)

EDIT:
I closed Explorer and opened a new Explorer window, and I can now drop-down both folders from the tree panel...

EDIT2:
If I highlight all C:\ files/folders, deselect one of the windows dirs, and right-click -> Properties, it gives me the 10.9GB that Drive C:'s properties says is the used space.  If I include both windows dirs, I get around 14GB filesize.  Wth??

---

### Post by SEMW on 2008-01-08
This is presumably a bug in WinDirStat, because you only have one Windows directory.  Unlike Linux on Ext2, Windows on NTFS is *not* case-sensitive (only case-preserving); which means that C:\Windows, C:\windows, C:\WINDOWS, and C:\WiNdOwS all point to exactly the same folder.

Once you realise that there is only one actual folder, all the 'inconsistencies' such as 'each folder' being 4GB but both folders only taking up 4GB are resolved.

---

### Post by eternicode on 2008-01-08
Thanks for the reply, but could you please explain this:

[ATTACH]55719[/ATTACH]

That's a screencap from Windows Explorer's tree pane.

It does seem that the two folders are *actually* the same folder...it's just strange to have two of them there (in Explorer, no less).

I guess it doesn't really matter, since I don't use Windows anymore anyways :) just a strange quirk that is slightly annoying.

I'll have to check it out from linux...

---

### Post by DarkN00b on 2008-01-08
One way to check if they actually are the same folder is to create a new text file (with a unique name like zyzzx.txt) in one windows folder and then look in the other folder to see of it shows up there.

---

### Post by SEMW on 2008-01-08
Woah.  Weird.  I'm guessing it's the unintentional result of some kind of behind-the-scenes application compatibility hack sitting between the file system and programs like Explorer and WinDirStat -- to provide support for some old DOS program that interprets filenames as if they were  case-sensitive, maybe.  Anyway, definitely a bug in Windows.

---

### Post by DarkN00b on 2008-01-08
> **SEMW said:**
> Woah.  Weird.  I'm guessing it's the unintentional result of some kind of behind-the-scenes application compatibility hack sitting between the file system and programs like Explorer and WinDirStat -- to provide support for some old DOS program that interprets filenames as if they were  case-sensitive, maybe.  Anyway, definitely a bug in Windows.

So this could be a *feature* and not a bug! [img]http://digilander.libero.it/le.faccine/faccinea/cartelli/statici/1524.gif[/img]

---

### Post by rubicon on 2008-01-08
So, this text file is in both directories? Interesting :)

FYI, NTFS supports both soft and hard links.

---

### Post by rubicon on 2008-01-08
To prove: [http://en.wikipedia.org/wiki/Comparison_of_file_systems#Features](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Features)

---

### Post by eternicode on 2008-01-08
> **rubicon said:**
> To prove: [http://en.wikipedia.org/wiki/Comparison_of_file_systems#Features](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Features)

Ah, so :) but it also says that NTFS is Case-sensitive.  I'm guessing it's the OS that is not....which could be the source of this bug-feature. :lolflag:

EDIT:
I tried the text file test (created it in WINDOWS), but when I went to enter windows, it redirected me to WINDOWS.

I'm also going to try a windows reboot later today, given the chance.

---

### Post by rubicon on 2008-01-08
You can use special software to look if one of these two folders is actually a link. Though I can't say what tool is worth using :) WinXP doesn't support FS-links out-of-the-box, so it doesn't know what to do with them but to show as usual folders/files.

And that WinDirStat doesn't works with links properly, it seems.

---

### Post by rubicon on 2008-01-08
Or, maybe you can even use your linux with ntfs-3g driver! Just make ```
ls -Al /media/windows/
``` This may help understanding what's going on after all.

If this will work, then, probably, you can use 'rm' to delete the link. Of course, if you still need to do it.

---

### Post by eternicode on 2008-01-08
> **rubicon said:**
> Or, maybe you can even use your linux with ntfs-3g driver! Just make ```
ls -Al /media/windows/
``` This may help understanding what's going on after all.

If this will work, then, probably, you can use 'rm' to delete the link. Of course, if you still need to do it.

Yes, I have a feeling it may be a link that either I or linux accidentally created, and Windows doesn't like to handle.  Still need to check on that, though.

EDIT:
Alright, a reboot to Windows did no good; they were both still there and both pointed to C:\WINDOWS

Back in good ol' linux:

```

andrew@Ximplix:~$ ls -Alh /media/windows
total 15M
-rwxrwxrwx 1 andrew root    0 2004-08-10 13:04 AUTOEXEC.BAT
-rwxrwxrwx 1 andrew root  12M 2006-11-16 12:16 AVG7QT.DAT
...........
drwxrwxrwx 1 andrew root 4.0K 2007-12-31 19:27 windows
drwxrwxrwx 1 andrew root 112K 2008-01-08 13:34 WINDOWS

```

I'm automounting it with fmask=0000,dmask=0000 in fstab, in case you're wondering about the permissions.

I'm not sure I understand the reasoning behind directory sizes; links are normally 4.0K, right?  Why would WINDOWS be 112K?

Also:
```

andrew@Ximplix:~$ cd /media/windows/windows
andrew@Ximplix:/media/windows/windows$ cd ../WINDOWS
andrew@Ximplix:/media/windows/WINDOWS$

```

Hmm....is this just how linux deals with hard (or soft) links?

EDIT2:
Alright, now things are interesting.

From C:\WINDOWS:
```
andrew@Ximplix:/media/windows/WINDOWS$ ls
0.log                                Minidump                                       setupact.del
addins                               ModemLog_Conexant HDA D110 MDC V.92 Modem.txt  setupact.log
AppPatch                             mozver.dat                                     setupapi.del
assembly                             mp10oem.txt                                    setupapi.log
atid.ini                             msagent                                        setupapi.log.0.old
Blue Lace 16.bmp                     msapps                                         setuperr.del
bootstat.dat                         msdfmap.ini                                    setuperr.log
calera.ini                           msdownld.tmp                                   setuplog.del
cdplayer.ini                         msgsocm.log                                    setuplog.txt
etc......  all the normal Windows dir files and then some.
```

However, back in C:\windows:
```

andrew@Ximplix:/media/windows/windows$ ls
command  explorer.exe  fonts  inf  notepad.exe  profiles  regedit.exe  system  system32  system.ini  temp  winebrowser.exe  winhelp.exe

```
That's all.

I also just checked my win configuration; the only thing referrencing the windows drive is Wine's C: drive, mapped to /media/windows.  However, I thought the "profiles" dir in "windows" looked odd so i followed it:
```

andrew@Ximplix:/media/windows/windows$ ls profiles/andrew/Desktop
[Linux desktop contents]

```
:???:

---

### Post by immolat3 on 2008-01-08
honest to god, i tried dual booting not long ago, and i let windows run a scandisk after i installed ubuntu, and it messed up both my partitions because it "fixed" it.

good game M$.

---

### Post by eternicode on 2008-01-08
> **immolat3 said:**
> honest to god, i tried dual booting not long ago, and i let windows run a scandisk after i installed ubuntu, and it messed up both my partitions because it "fixed" it.

good game M$.

Actually, I've been dual-booting for months without issue.  Still am :), except for this.

---

### Post by SEMW on 2008-01-08
> **immolat3 said:**
> honest to god, i tried dual booting not long ago, and i let windows run a scandisk after i installed ubuntu, and it messed up both my partitions because it "fixed" it.

good game M$.

Let me just check I understand this correctly.  You somehow contrived to run *Microsoft's Scandisk* on an *Ubuntu* partition (which presumably was an ext2 partition which you mounted in Windows with fs-driver or somesuch) and are *suprised* that it got "messed up"?

Anyway, back on topic for the thread; eternicode, I'm guessing that you at this point suspect that this is might be a WINE issue, in which case I'm afraid I'm not going to be able to be of much more help.

---

### Post by eternicode on 2008-01-08
```

andrew@Ximplix:~$ ls -l /media/windows/windows/profiles/andrew/Desktop
lrwxrwxrwx 1 andrew root 48 2007-12-14 00:43 /media/windows/windows/profiles/andrew/Desktop -> /home/andrew/Desktop

```

I believe it is a wine issue.  In my wine config (way back when I set it up), I pointed WINE's C: drive at the directory where I mount my windows partition.  If I'm right (and I have no clue if I am), apparently, wine creates its own, separate "windows" directory (note the lowercase) inside its C: directory.  In Windows, which is case-insensitive, it *runs* from the C:\WINDOWS directory; so it just makes sense (to XP) that C:\windows is the same as C:\WINDOWS.  As a result, it only shows me the content from C:\WINDOWS.  Just wonder why I never noticed it before :)

---

