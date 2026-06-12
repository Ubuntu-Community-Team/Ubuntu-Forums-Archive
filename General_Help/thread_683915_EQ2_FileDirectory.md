---
title: "EQ2 File/Directory?"
date: 2008-01-31
forum: General Help
---

### Post by dzgruntld on 2008-01-31
I have tried different searches, no luck yet so here I am.  I have been able to get WINE installed, Directx9.0c installed and EverQuest2 installed.  My question is this: when EQ2 installed it went to my "/home/myname" folder.  How do I get it to install into it's own folder like: "/home/myname/Sony/EverQuest2" ??  Do I even need to??  I am enjoying my experiment with Ubuntu 7.10 so far.  Quite a learning curve.

---

### Post by pointone on 2008-01-31
If you installed it via Wine, it should've been installed to /home/username/.wine/drive_c/... I don't know how you could've installed it anywhere else. :|

---

### Post by dzgruntld on 2008-01-31
Thanks Pointone,
  I tried to follow instructions I found on the forums at EverQuest2.com, "http://forums.station.sony.com/eq2/posts/list.m?topic_id=396323".  
The author explained how to get Wine and DirectX working from other links. 
He said to make a folder :  " Make a folder for EQ2  mkdir ~/.wine/drive_c/Program\ Files/Sony/EverQuest\ II/".
 I think some of the hash marks were backwards, but I was able to get it.  
Next he said to: "Copy EQ2.exe from windows install of EverQuest 2 to the folder you created in the previous step." 
 I have my other HD mounted so Ubuntu can see it, so I just copied and pasted the EQ2.exe file.
This where I think I got lost:  "Change directories into your Linux based EQ2 folder and type:
   wine ./EQ2.exe".  
Clicking on the EQ2.exe file allows me to choose what to open it with, I used WINE.  
 Everything ran and the game downloaded but not to ".wine/drive_c/Program Files/Sony/EverQuest2". 
 All the EQ2 files and folders got into /home/myname/.
 I can get the game to play, I just think it is not installed into the correct directory, ( I like neatness and order).

---

