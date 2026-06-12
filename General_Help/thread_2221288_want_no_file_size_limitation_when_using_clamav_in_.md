---
title: "want no file size limitation when using clamav in command line"
date: 2014-05-01
forum: General Help
---

### Post by ubto66 on 2014-05-01
ubuntu 12.04

             I want to use clamav in the command line.
Not the clamtk gui.
If you want to make comments about that there is no reason to use antivirus scanner on linux then
do not make them. 


These commands I know about.


Sudo freshclam updates.
Command clamscan 'file or folder' tostart a scan. Command clamscan -r 'folder' and folder in folder gets scanned.


Command clamscan -- help lists a lotof commands. 


What I do not understand about clamav in terminal, is the file size limitations. And my question is,
how do I remove these limitations?


[FONT=Times New Roman]Fxby default clamscan has a max file size limit about 20mb.[/FONT]
[FONT=Times New Roman]Command clamscan 'file that is 100mb' gives the result than only 20 mb are scanned. Try for your self.[/FONT]


[FONT=Times New Roman]Toget clamav to scan bigger files you may use[/FONT]
[FONT=Times New Roman]Command [/FONT][FONT=Times New Roman]clamscan--max-filesize=700M --max-scansize=700M[/FONT]
[FONT=Times New Roman]That gets clamav to scan files up to 700mb.[/FONT]


[FONT=Times New Roman]But fx clamscan --max-filesize=7000M --max-scansize=7000M[/FONT]
[FONT=Times New Roman]results in a warning saying that max will be 4G, could be 4000mb.[/FONT]
[FONT=Times New Roman]But that is not the case. Clamav will not scan bigger files than about 2gb.[/FONT]
[FONT=Times New Roman]Even if you [/FONT][FONT=Times New Roman]command 
Clamscan --max-filesize=3000M --max-scansize=3000M[/FONT]


[FONT=Times New Roman]But how do you scan fx a dvd hd file that is bigger than 4gb or 1tb hdd that contains a folder with[/FONT]
[FONT=Times New Roman]700gb of files?[/FONT]


[FONT=Times New Roman]Thankyou.[/FONT]

---

