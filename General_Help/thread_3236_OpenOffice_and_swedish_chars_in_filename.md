---
title: "OpenOffice and swedish chars in filename"
date: 2004-11-04
forum: General Help
---

### Post by JsPr on 2004-11-04
Hi,
Can someone pls explain this to me. If I create a file in for example openoffice writer and save it as "test åäöÅÄÖ.sxw" (without the quotes) it works. I can't, however, double click on the file and open it. I get an error message from OO saying that the file doesn't exist. 
I have traced this to be the Swedish chars åäöÅÄÖ that makes OO behave this way.
Can it be the character set? I use ISO8859-1 at the moment and I believe that I could "double click" open a document in SuSE 9.1 that uses UTF-8.
Can anybody confirm this behaviour or am I the only one???

Regards

Jesper

---

### Post by elwis on 2004-11-04
[QUOTE=JsPr]Hi,
Can someone pls explain this to me. If I create a file in for example openoffice writer and save it as "test åäöÅÄÖ.sxw" (without the quotes) it works. I can't, however, double click on the file and open it. I get an error message from OO saying that the file doesn't exist. 
I have traced this to be the Swedish chars åäöÅÄÖ that makes OO behave this way.
Can it be the character set? I use ISO8859-1 at the moment and I believe that I could "double click" open a document in SuSE 9.1 that uses UTF-8.
Can anybody confirm this behaviour or am I the only one???

Regards

Jesper[/QUOTE]
 tjenis!

Might be a GNOME thing, cause it works when you write "oowriter arneåäö.sxw" in the terminal..

---

### Post by JProgrammer on 2004-11-04
Hmm Gnome is 100% Unicode based eg pango even lets you run characters right to left. Unlike some other OS (MS). However the file system on your computer might not be UTF-8 based have a read of [this](http://www.newsforge.com/article.pl?sid=04/10/27/1631244) article on newsforge.

---

### Post by JsPr on 2004-11-05
Well, since it works to open a "test åäö.sxw" from the command line and from within OO I think that it's a Gnome/OO thing. Strangely enough I have no problems opening a åäö.pdf file from Gnome.

---

### Post by hyde on 2004-11-06
Hi

I have same issue with scandinavian characters...
[http://www.ubuntuforums.org/showthread.php?t=3061](http://www.ubuntuforums.org/showthread.php?t=3061)

Does your Nautilus browser show ä's and ö's? I see only question mark instead of non-english character.  :confused:

---

### Post by elwis on 2004-11-06
[QUOTE=hyde]Hi

I have same issue with scandinavian characters...
[http://www.ubuntuforums.org/showthread.php?t=3061](http://www.ubuntuforums.org/showthread.php?t=3061)

Does your Nautilus browser show ä's and ö's? I see only question mark instead of non-english character.  :confused:[/QUOTE]
 Mine does, but if I try open it it won't work, since the file "arne%E5%E4%F6.sxw" doesn't exist.

And that's correct, since that's not the name of the file, it's "arneåäö.sxw" ;)

---

### Post by fjleal on 2004-11-06
Hi! Identical problem here with portuguese characters on Gnome/OpenOffice relationship. Characters represeted as "à", "ã" and "ç" on some filenames make OpenOffice unable to open such files when I double-clicking on them. Gnome shows those characters ok, but OOffice doesn't understand them.

Opening OOffice and then choosing the "File -> Open" function opens the file. For instance, a file name that includes the words "à documentação" shows up in the OOffice title bar as "Ã documentaÃ§Ã£o".

This is weird, since I'm using Fedora Core 2 on my main machine and I have no such problem.

---

### Post by fjleal on 2004-11-06
Ok, I think I managed to solve my problem. Here's how I did it:

1. as root, I edited /etc/locale.gen and removed the "en" line that was causing strange errors ("directory 'en' does not exist", when setting locales);

2. I run "dpkg-reconfigure locales" and generated "en_GB.UTF-8" and "pt_PT.ISO-8859-1". I set "en_GB.UTF-8" as system default.

After restarting, "locale" shows "en_GB.UTF-8" for all items (system interface is in english) but now I can correctly read portuguese characters in the terminal, and OpenOffice also opens files with portuguese characters in their filenames when I double-click them.

---

### Post by JsPr on 2004-11-06
[QUOTE=fjleal]Ok, I think I managed to solve my problem. Here's how I did it:

1. as root, I edited /etc/locale.gen and removed the "en" line that was causing strange errors ("directory 'en' does not exist", when setting locales);

2. I run "dpkg-reconfigure locales" and generated "en_GB.UTF-8" and "pt_PT.ISO-8859-1". I set "en_GB.UTF-8" as system default.

After restarting, "locale" shows "en_GB.UTF-8" for all items (system interface is in english) but now I can correctly read portuguese characters in the terminal, and OpenOffice also opens files with portuguese characters in their filenames when I double-click them.[/QUOTE]
 Thanks fjleal, this solved my problem too!
I believe that UTF-8 is THE way to go. Hopefully this change won't impact negatively on some other applications, time will tell.

---

