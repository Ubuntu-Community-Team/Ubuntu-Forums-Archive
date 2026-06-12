---
title: "Associating PHP files with Wine &gt; Notepad2"
date: 2007-05-27
forum: General Help
---

### Post by Martijn2 on 2007-05-27
Hello,
I've recently switched to Kubuntu Dapper Drake (my CDs for Feisty Fawn are already ordered) because on my laptop, Windows was really irritating (kept freezing up, major waiting time) me. Windows does work correctly on my desktop computer, btw ;)
Anyway, I'm no Linux newbie since I use it from time to time (mostly live CDs, so I backed up everything from my Windows configuration and installed Kubuntu from the CD, singleboot. Everything went and is fine.

_My problem is the  following:_
I had a favorite program code editor on Windows called [Notepad2]("http://www.flos-freeware.ch/notepad2.html"), and knew Wine alowed me to run a fair share of Win32 programs. Notepad2 runs fine through Wine, with the exception of the toolbar that either is hiden, blury, or viewable but inaccesible. 
I'm a Web designer/programmer and am using this program as a syntax highlighter, so I wanted to use Notepad2 as default program for PHP scripts (and HTML and other languages aswel, later on). The file-association manager wouldn't let me pass the location of the file being opened to the program (tried %1, %U, %S), then I Googled a bit and came across [this thread]("http://www.linuxquestions.org/questions/showthread.php?s=&threadid=355622") on another forum. 

I adjusted the script found on that page to:
```

#!/bin/sh
ROOT_DRIVE="Z:\\"
for arg
do
   sudo wine "C:\\windows\\Notepad2" "${ROOT_DRIVE}$(echo "$arg" | sed 's/\//\\/g')"
done 

```
And saved it as "notepad2.sh". Then I added the script to the association manager with nearly all settings available (run in/not in terminal, %1, %S,  %U, or nothing as argument passer to the script). It didn't work, while when I pass the arguments through Konsole it *does* open correctly. :S

I'm really stuck with this. Thanks in advance for any help :)

---

