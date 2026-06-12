---
title: "Failed to load session &quot;ubuntu&quot;"
date: 2014-06-20
forum: General Help
---

### Post by dwarf2 on 2014-06-20
Hello! My faithful laptop has been chugging away using Ubuntu (currently version 12.04.4) for about 2 years now, I don't know much about the system but until now hadn't ran into any major problems. The laptop was a gift with Ubuntu already installed on it, I mostly only use it for painting in GIMP and internet browsing. Up until now I just installed/uninstalled things with the software center, and never used the terminal since I didn't know how to/didn't want to mess anything up. 

Any help would be greatly appreciated, but please remember you're talking to someone who has little knowledge about how to do anything with the system, but if you can just give me clear directions I'll be fine.

[I]
(I'll outline everything I can remember that happened here just in case it's needed, but you can just skip down to the bottom for the current problem)[/I]

     Wednesday evening I found an art program I wanted to try (Krita), but my software center only had an old version of it.  I really wanted the latest version so I ran a google search of how to install the ppa in the software center, and followed the directions to do it. I then restarted and went to download all the latest updates (it's been a while since I did that) before I downloaded Krita. Most of the updates went fine, but I got an error message that the last 90 or so were downloaded but couldn't be installed, and to check if I had any third party repositories installed, as that was a common source of problems.

     I restarted the computer, and before I reached the desktop I got a notice saying that the graphics card and the external devices I had couldn't be read, and so I went ahead and chose to login using the low graphics settings.

     Figuring this all had to do with the ppa I added, I went into the software center to undo it, but when I started it up there was large error message saying it had a problem, and did I want it to try and repair the problem? It was unable to repair it so I went and unchecked the boxes associated with third party repositories, and after I did that the software center was able to repair itself and I thought everything was fine.

     I restarted and again got the low graphics session error, but this time when I tried to login I got another error message saying 'Failed to load session "ubuntu"' and the only option was to be sent back to the login page.



So here's my problem: I get a notice 'Failed to load session "ubuntu"' upon startup and I can't get to my desktop.
-I attempted 'sudo apt-get install ubuntu-desktop' in the tty1 terminal, but it stops halfway through and says that I have held broken packages and that there are unresolved depencies.
-I've tried 'sudo apt-get install -f', 'sudo apt-get clean', 'sudo apt-get autoclean', 'sudo apt-get update' and still can't install ubuntu-desktop.
-When I put in 'sudo dpkg reconfigure ubuntu-desktop' it says the package doesn't exist and to install it if I want it. 


I'm going to hope that whatever has happened hasn't lost my files, I have a lot of important document/painting files on there that I never backed up. :|

---

### Post by mörgæs on 2014-06-21
Hi, welcome to the fora.

First, take a backup. If the installed system is fubar you can do a live boot and salvage the files from there.

---

### Post by dwarf2 on 2014-07-19
A linux savvy friend recovered my documents and wiped/installed a new OS for me. :)

---

