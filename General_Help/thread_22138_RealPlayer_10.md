---
title: "RealPlayer 10"
date: 2005-03-25
forum: General Help
---

### Post by tdell on 2005-03-25
Against better judgement I installed the RealPlayer. It works OK but it has created THREE menu entries.
I would just like to get rid of it now. how do I uninstall it and remove the menu entries?

---

### Post by arnieboy on 2005-03-25
There is no uninstall command in realplayer if u did not install it as a .deb package. The "install.log" file in the Realplayer directory (where u chose to install relaplayer) will tell u where each file got installed. U can delete these manually. Sounds like a pain eh? 
Well if u just wanna remove the multiple menu entries just type this in terminal:
sudo gedit /usr/share/applications/realplay.desktop

and edit the "Categories" line to:
Categories=GNOME;Application;AudioVideo;

Close the file and log out of gnome once and come back and tell me the difference.

-arnieboy

---

### Post by tdell on 2005-03-25
Well tried that now I have TWO Sound & Video Menus the first with only Real in it and the original with two entries and one does not work.

Thank for trying to help.

Tom

---

### Post by arnieboy on 2005-03-25
Tom,
       I think u added a new line called "Categories". U should have edited the existing line called "Categories".
Check for multiple entries of "Categories" in the same file. 
If I am wrong and U really did edit the "Categories" line then edit it again to
Categories=AudioVideo;
It should work this time. As u must have guessed the GNOME menu reads the .desktop files in /usr/share/applications and /usr/share/applications/kde and the menu that u see in the end is a result of the configuration in these files. For example if u see something in Kubuntu and not in Ubuntu, u possibly need to remove the line 
"OnlyShowIn=KDE" from the concerned .desktop files in /usr/share/applications/kde
let me know whether this works for u. It should.
-arnieboy

---

### Post by tdell on 2005-03-25
Thanks again but still no change. There is only one Categories line.

Tom

---

### Post by arnieboy on 2005-03-25
Ok on to the next step:
in terminal type:
"sudo updatedb"  and press enter. This will take around half a minute to finish depending on the speed of ur system.
After that search for the file "realplay.desktop" (in Gnome find) and tell me the location of all instances of this file in "/usr/share/applications/
For example if u find a copy in /usr/share/applications/kde let me know that as well.
-arnieboy

---

### Post by tdell on 2005-03-25
OK there are two:
/usr/share/applications  and
/usr/share/RealPlayer/share

I edited them both as you said logged out and back in still no change.

Thanks for your time on this. I will try to reboot and see if that changes anything.

Tom

---

### Post by arnieboy on 2005-03-25
Tom,
      if rebooting does not help, delete /usr/share/RealPlayer/share/realplay.desktop 
U only need one .desktop file (not 2). After that log out of gnome and log back in. 
-arnieboy

---

### Post by tdell on 2005-03-25
Done. Still no joy.

Tom

---

### Post by arnieboy on 2005-03-25
alright, onto the last step.. cut /usr/share/applications/realplay.desktop and paste it onto ur desktop (dont delete it). then log out of gnome and log back in. This time u will see a difference. let me know what it is.
-arnieboy

---

### Post by tdell on 2005-03-25
OK one menu entry gone. I still have the two Sound & Video entries an the first still has only RealPlayer in it.

Tom

---

### Post by arnieboy on 2005-03-25
Tom,
      What this means is that Gnome has hidden 1/2 realplay.desktop files somewhere either in /root or in ur home folder. Now the problem with that is that these files wont come up in search beacuse they are placed possibly in hidden folders (folders starting with a "." (dot)). U might wanna look in folders like:
/root/.gnome2/panel2.d/default/launchers
though I cant guarantee that such a folder will exist on ur machine. yu have to do some searching urself though I know its tricky.Some apects of Gnome arent exactly super user-friendly. 
I am signing off for the night... and I am sorry I couldnt solve ur problem entirely though I hope I have been of some use to u atleast. 
-arnieboy

---

### Post by tdell on 2005-03-26
Thanks for all your help. I finally got it all sorted out. There was a duplicate hidden file in my /home folder. Not sure what created the problem in the first place, but it was a good learning experience.

Now if I can just get Ubuntu to print to my XP printer thru the network I will settle down for a while.

Tom

---

