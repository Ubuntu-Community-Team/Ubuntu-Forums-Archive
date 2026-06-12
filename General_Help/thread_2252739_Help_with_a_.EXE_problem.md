---
title: "Help with a .EXE problem"
date: 2014-11-14
forum: General Help
---

### Post by Djvoldi123 on 2014-11-14
I use Ubuntu 12.04, and have been doing so for a while now(never got around to upgrading it). It has been working very well until recently, about a month or so back. For some reason, a Windows executable file is being created for every folder in Ubuntu. For example, in the Desktop folder, there is a "Desktop.exe" file, which is corrupt and cannot be executed(I know, I shouldn't have tried to open it). Similarly, in the folder Downloads, there is a "Downloads.exe" file. Basically, every folder in Ubuntu has a .exe counterpart inside it. I haven't found anything bad about this new phenomenon - no sudden crashes or anything. But it seems really strange to me, and besides, it's taking up space. Deleting one of these .exe files is useless - it is recreated within seconds.  Can someone help here? Thanks in advance....

---

### Post by dargaud2 on 2014-11-14
Windows 12.04 ?!? Whoah, and Windows 10 has only just been announced. Are you a MS beta tester ?

---

### Post by Djvoldi123 on 2014-11-14
Not exactly. I'm Satya Nadella in disguise.....shh, don't tell anyone.
Kidding :)
That was a mistake. I meant **Ubuntu** 12.04.

---

### Post by sotiris2 on 2014-11-14
Are they still being created? I mean you now have an .exe for every folder you already have, if you make a new folder "test" will you get a file "test.exe" ? Also open a terminal and do ```
file ~/Downloads/Downloads.exe 
``` or on any other .exe 

Do you have wine installed? Did you try executing them with it (if not don't) or otherwise describe how you did try to execute them.

---

### Post by monkeybrain20122 on 2014-11-14
A Windows virus you somehow activated by running something in wine?

---

### Post by The Cog on 2014-11-14
It may also be interesting to see the output of
```
hd Desktop/Desktop.exe | head
```
to see the exact contents of the start of the file.

---

### Post by buzzingrobot on 2014-11-14
Are they created in *every* folder (there are many, many, folders) or just folders in your /home directory?

If you delete them, do they return?  When?  Triggering surreptitious downloads in a browser is a reasonably common way to deliver malware. Do the files, then, return if you don't use the browser?  

Try temporarily disabling your net connection, use the machine for a while, and see if they return.  If so, that means something running on your system is creating them.

Windows .exe files won't execute on Linux.

---

### Post by Djvoldi123 on 2014-11-16
If I create a folder, a new exe version is created within 5 minutes. Strangely - I only noticed - the Desktop is the only folder without an exe version of itself. EVERY other folder, as far as I know(within the home folder) has the bug.
Not having an internet connection doesn't make a difference....
When I tried to execute them in the beginning, I just clicked on Open with Wine.

file ~/Downloads/Downloads.exe
Output: /home/******/Blog-fb/Blog-fb.exe: PE32 executable (GUI) Intel 80386, for MS Windows, PECompact2 compressed


 hd Blog-fb/Blog-fb.exe | head
00000000  4d 5a 90 00 03 00 00 00  04 00 00 00 ff ff 00 00  |MZ..............|
00000010  b8 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 01 00 00  |................|
00000040  0e 1f ba 0e 00 b4 09 cd  21 b8 01 4c cd 21 54 68  |........!..L.!Th|
00000050  69 73 20 70 72 6f 67 72  61 6d 20 63 61 6e 6e 6f  |is program canno|
00000060  74 20 62 65 20 72 75 6e  20 69 6e 20 44 4f 53 20  |t be run in DOS |
00000070  6d 6f 64 65 2e 0d 0d 0a  24 00 00 00 00 00 00 00  |mode....$.......|
00000080  d6 50 0e 80 92 31 60 d3  92 31 60 d3 92 31 60 d3  |.P...1`..1`..1`.|
00000090  05 f5 1e d3 90 31 60 d3  b5 f7 0d d3 52 31 60 d3  |.....1`.....R1`.|

---

