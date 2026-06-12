---
title: "List all .bin files (executable)"
date: 2007-12-18
forum: General Help
---

### Post by Purplecatty on 2007-12-18
I am trying to list .bin (executable) files in Terminal which I forgot what command (I tried it once).  It was a simple command.  I came across one of other blog while searching for solution on missing KDE Guidance program.  Blogger just note it on his blog that you can list files in terminal for fun of it.  I ran Terminal and typed command and it did listed many binary files that are executable.  I thought it was so cool that I can use it for reference in case if I want to run any program through Terminal (like if I want to run GAIM, I simply type GAIM in Terminal ect..)

I DID add it to bookmark for reference.  But later on, after I upgraded Feisty to Gusty,  something screwed in KDE and Gnome (I had two sessions that I can hop)  so I decide to copy bookmark (my mistake) from folder instead of Firefox's file export to my thumbdrive.  After I reinstall Ubuntu Gusty (using CD) and move bookmark files from thumbdrive.  I tried to open it and realized it's an "empty" bookmark.  I kinda banged my head to the wall wishing I had written it on notebook so I won't be asking around. (I writes note of commands from now on, lesson learned)

Ok What it look like on Terminal is that it just lists all executable programs without any ".bin" or ".xxx" or any character ect.  It is simply the name of the programs in aphabetical order which is long.

Command was simple. It show long list of binary (executable) files without any character or "*.bin" on both ends of file name.  It even list Evolution (email), GAIM (now Pidgin), Firefox, Calc  and many common programs

Can you answer my riddle?


Thanks!
Catty

---

### Post by psusi on 2007-12-18
There is no such thing as .bin, unix does not use file extensions for executables.  You can search your system for executable files with:

find / -type f -perm /+x

That will find anything executable anywhere on your system, but that includes libraries and things like that.  Generally if you are just looking for programs, you just want to

ls /bin /sbin /usr/bin /usr/sbin

---

### Post by Purplecatty on 2007-12-18
Ok thanks I'll give it a try.

Catty

---

