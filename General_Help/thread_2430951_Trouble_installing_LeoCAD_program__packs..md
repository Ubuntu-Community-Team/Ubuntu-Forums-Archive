---
title: "Trouble installing LeoCAD program  packs."
date: 2019-11-09
forum: General Help
---

### Post by nocruoro on 2019-11-09
Im trying to add additional brick parts for LeoCAD a building program. But i'm running into issue. the following sudo command below isn't working and can't create the necessary folder for dumping sipped parts files

[https://github.com/leozide/leocad/issues/239](https://github.com/leozide/leocad/issues/239)

here is the intended command
> sudo mkdir /usr/share/leocad/library.bin 

but i receive a conflict error saying mkdir: cannot create directory ‘/usr/share/leocad/library.bin’: No such file or directory and yet there is a usr directory as seen here how do i get around this ?

[COLOR=#ff0000][SIZE=4]
UPDATE[/SIZE][/COLOR]

[I][FONT=Verdana]> **Holger_Gehrke said:**
> Actually it isn't necessary to put anything in /usr/share/leocad because leocad has an option in the menu "View"->"Preferences"->tab "General"->field "Custom parts library" which allows you to set the directory where the program looks for parts. And 'library.bin' isn't supposed to be a directory, it's a file that contains the compressed official library. The person who packaged the program for Ubuntu opted for not including that file. Instead there's a separate package 'ldraw-parts' that installs uncompressed parts into '/usr/share/ldraw' which seems to be the second default location for leocad to search. Since there are other programs that can use these in this form while only leocad can use them compressed that choice makes sense. The library in the repositories seems to be about a year older than the current one on ldraw.org and has about 9500 parts compared to about 11800 for the newest official one.[/FONT]

[FONT=Verdana]There's one small problem, though. Either the packager decided to compile leocad without support for archives or the version in the repositories is from before leocad gained that ability. So the easiest way to have a current library seems to be to download the library/ies from ldraw.org, unpack it/them into a directory in your home directory and point the option at that. [/FONT]

[FONT=Verdana]Holger[/FONT]
[/I]
[FONT=Verdana]I just did this and it works [/FONT][COLOR=#333333][FONT=Verdana]under [/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**view>preferences>general>downloads>ldrawunf**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana] as custom folder but after i did this all of the other regular parts disappeared and only way to get them back is to point the custom parts seacrh at a alternate path like [/FONT][/COLOR][COLOR=#333333][FONT=Verdana]view>preferences>general>pictures [/FONT][/COLOR][FONT=Verdana]and restart the program so i can see them. I really want to avoid this collision problem.[/FONT]

---

### Post by Holger_Gehrke on 2019-11-10
The directory your screenshot shows is '/usr/share/**doc**/leocad'. That is different from '/usr/share/leocad/', isn't it ? The command 'mkdir' has an option '-p' or '--parents' for situations where you need to create a path of directories; 'sudo mkdir -p /usr/share/leocad/library.bin' will create the directory '/usr/share/leocad/' if it doesn't exist and the directory 'library.bin' inside that. Or you could run 'sudo mkdir /usr/share/leocad' and then 'sudo mkdir /usr/share/leocad/library.bin'

Holger

---

### Post by nocruoro on 2019-11-10
Seeems to have worked, i'll send a further update later if it was succesful. Learning on ubuntu and sudo commands is hard work for me.

---

### Post by nocruoro on 2019-11-12
[SIZE=2]New problem. my computer wont let me move or copy the zip file into the new library folder. How do i get around this? Is there a sudo user command that can move the file [COLOR=#008000][I](and enable such permissions by default with the mouse for future use?)

[/I][/COLOR]currently the zip file is in the default downloads folder

edit: plz help me?[/SIZE]

---

### Post by nocruoro on 2019-11-13
hello?

---

### Post by nocruoro on 2019-11-14
[SIZE=3]BUMP My problem is still not solved and haven't found reliable help on google. plz help me.

**The intention is:** move file from documents from download folder to a library fold in a usr share folder but both....[/SIZE] [SIZE=3]**ctrl**[SIZE=2]+[/SIZE]**c **or** right click and paste** are both not working. what is the intended terminal command code for getting it through this restriction [/SIZE]:confused::confused::confused:

---

### Post by tea for one on 2019-11-14
If you want to move a file from your Downloads folder to a destination within /usr/share, you have to use admin rights with sudo.

For example, if you want to move a theme from Downloads to /usr/share/themes

```
cd Downloads
```

```
sudo mv mytheme /usr/share/themes
```

Substitute **mytheme** with the name of your file/folder

Substiute **themes** for the destination you need within /usr/share

Good luck

---

### Post by Holger_Gehrke on 2019-11-14
Actually it isn't necessary to put anything in /usr/share/leocad because leocad has an option in the menu "View"->"Preferences"->tab "General"->field "Custom parts library" which allows you to set the directory where the program looks for parts. And 'library.bin' isn't supposed to be a directory, it's a file that contains the compressed official library. The person who packaged the program for Ubuntu opted for not including that file. Instead there's a separate package 'ldraw-parts' that installs uncompressed parts into '/usr/share/ldraw' which seems to be the second default location for leocad to search. Since there are other programs that can use these in this form while only leocad can use them compressed that choice makes sense. The library in the repositories seems to be about a year older than the current one on ldraw.org and has about 9500 parts compared to about 11800 for the newest official one.

There's one small problem, though. Either the packager decided to compile leocad without support for archives or the version in the repositories is from before leocad gained that ability. So the easiest way to have a current library seems to be to download the library/ies from ldraw.org, unpack it/them into a directory in your home directory and point the option at that. 

And if you should ever get into the situation where you really need to put a file somewhere outside of $HOME, there are several ways to do that. 'sudo' stands for '**s**witch **u**ser and **do**' and unless you tell sudo to switch to a specific user (with 'sudo -u username command') it will switch to root (the administrative user account that's basically allowed to do everything). So 'sudo' can be used with basically any command, 'cp source[s] target' for copying, 'mv source[s] target' for moving or anything else. Using sudo with graphical tools is generally considered to be a bad idea; graphical programs often create files in the home directory for their settings; if you run them with sudo then these files are owned by root and you can get into situations where all of a sudden you can't change options in the program. Using the '-H' option of 'sudo' tells sudo to use the home directory of the user it switches to and not the home of the actual user and is somewhat safer. There's also pkexec (policy kit execute), which can also be used to run programs with higher privileges. But the IMHO easiest way is to use the 'admin://' scheme in the file manager. How you do that depends on the file manager you use; not every file manager gives you a constantly visible address bar into which you could enter something like 'admin:///usr/share/leocad' (no, the three '/' are not a typo, two of them are part of the scheme notation and the third is part of an absolute path) ; Thunar on XUbuntu - which I am using - does; Nautilus - the file manager of main line Ubuntu - doesn't, but I think you can get a location field by hitting ctrl-L. After entering an URI with an 'admin://' scheme, you will be asked for your password. After entering it you can drag and drop files from another window into the one where the admin scheme is active.

Holger

---

### Post by nocruoro on 2019-12-01
> **Holger_Gehrke said:**
> Actually it isn't necessary to put anything in /usr/share/leocad because leocad has an option in the menu "View"->"Preferences"->tab "General"->field "Custom parts library" which allows you to set the directory where the program looks for parts. And 'library.bin' isn't supposed to be a directory, it's a file that contains the compressed official library. The person who packaged the program for Ubuntu opted for not including that file. Instead there's a separate package 'ldraw-parts' that installs uncompressed parts into '/usr/share/ldraw' which seems to be the second default location for leocad to search. Since there are other programs that can use these in this form while only leocad can use them compressed that choice makes sense. The library in the repositories seems to be about a year older than the current one on ldraw.org and has about 9500 parts compared to about 11800 for the newest official one.

There's one small problem, though. Either the packager decided to compile leocad without support for archives or the version in the repositories is from before leocad gained that ability. So the easiest way to have a current library seems to be to download the library/ies from ldraw.org, unpack it/them into a directory in your home directory and point the option at that. 

Holger

I just did this and it works [COLOR=#333333][FONT=&quot]under [/FONT][/COLOR][COLOR=#333333][FONT=&quot]**view>preferences>general>downloads>ldrawunf**[/FONT][/COLOR][COLOR=#333333][FONT=&quot] as custom folder but after i did this all of the other regular parts disappeared and only way to get them back is to point the custom parts seacrh at a alternate path like [/FONT][/COLOR][COLOR=#333333][FONT=&quot]view>preferences>general>pictures [/FONT][/COLOR]and restart the program so i can see them. I really want to avoid this collision problem.

---

### Post by nocruoro on 2019-12-02
bump

---

### Post by nocruoro on 2019-12-09
BUMP After just doing all this and it works [COLOR=#333333][FONT=&amp]under [/FONT][/COLOR][COLOR=#333333][FONT=&amp]**view>preferences>general>downloads>ldrawunf**[/FONT][/COLOR][COLOR=#333333][FONT=&amp] as custom folder but after i did this all of the other regular parts disappeared.

The only way to get those back is to point the custom parts search for a different folder path like [/FONT][/COLOR][COLOR=#333333][FONT=&amp]view>preferences>general>pictures [/FONT][/COLOR]and restart the program so i can see them. 

Still haven't been able to solve them and Eurobricks forums don't have any members experienced with ubuntu.
Im running out of options and patience.

Ubuntu 18.4.3 64 Bit version

---

### Post by nocruoro on 2019-12-11
bump

---

### Post by nocruoro on 2019-12-13
bump

---

### Post by nocruoro on 2019-12-15
bump (i'm not here to increase my post count)

---

### Post by nocruoro on 2019-12-18
b u m p

---

### Post by nocruoro on 2019-12-22
bump bump bump bump bump bump

---

### Post by mörgæs on 2019-12-23
My dear fellow Icelander, several of your threads seem to end without a solution. Either in a series of bumps like this one or the activity just fades away.

A friendly meant advice: I think you will do yourself a favour and get a higher success rate by taking a look at your posting style, for example by seeking inspiration here: 

[https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by nocruoro on 2019-12-24
> **mörgæs said:**
> My dear fellow Icelander, several of your threads seem to end without a solution. Either in a series of bumps like this one or the activity just fades away.

A friendly meant advice: I think you will do yourself a favour and get a higher success rate by taking a look at your posting style, for example by seeking inspiration here: 

[https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

**[COLOR=#008000]There is no anti-bump rule or policy visible.[/COLOR]** i'm simply keepinng the thread active so it doesnt fade into obscurity and thread gets deleted before it's solved. which it hasn't been solved yet. I did add updates into my first post but still no success. :sad:

---

### Post by Holger_Gehrke on 2019-12-24
Try this: 
create a new folder 'leocadlib' in your home directory. Put the [complete.zip]("http://www.ldraw.org/library/updates/complete.zip") and the [ldrawunf.zip]("https://www.ldraw.org/library/unofficial/ldrawunf.zip") from ldraw.org in that folder. Start leocad. Select View->Preferences from the menu, go to the tab general and enter the complete path **and name** of the complete.zip into the field 'custom parts library' (example: /home/nocruoro/leocadlib/complete.zip). Close leocad and start it again. You should now have access to both the official and the unofficial parts (leocad 'knows' about the existence of ldrawunf.zip and if it's found in the same directory as the official library it gets loaded, too).

Remember the dire warnings about unofficial parts on ldraw.org, they are still in development and are subject to change without notice until they get promoted to being official parts. Projects that use unofficial parts usually get messed up if point of origin or standard orientation of an unofficial part changes during its further development.
Another problem is that leocad does not tell you whether a part is official or not, the library shows them all the same way. There supposedly is a way to put single unofficial parts in a folder named 'unofficial' in a non-zipped library to reduce the risk of using unofficial parts without noticing, but I haven't managed to do this.
To update either the official or the unofficial library, just download the new version and replace the files in ~/leocadlib.

Holger

---

### Post by nocruoro on 2019-12-25
> **Holger_Gehrke said:**
> Try this: 
create a new folder 'leocadlib' in your home directory. Put the [complete.zip]("http://www.ldraw.org/library/updates/complete.zip") and the [ldrawunf.zip]("https://www.ldraw.org/library/unofficial/ldrawunf.zip") from ldraw.org in that folder. Start leocad. Select View->Preferences from the menu, go to the tab general and enter the complete path **and name** of the complete.zip into the field 'custom parts library' (example: /home/nocruoro/leocadlib/complete.zip). Close leocad and start it again. You should now have access to both the official and the unofficial parts (leocad 'knows' about the existence of ldrawunf.zip and if it's found in the same directory as the official library it gets loaded, too).

Remember the dire warnings about unofficial parts on ldraw.org, they are still in development and are subject to change without notice until they get promoted to being official parts. Projects that use unofficial parts usually get messed up if point of origin or standard orientation of an unofficial part changes during its further development.
Another problem is that leocad does not tell you whether a part is official or not, the library shows them all the same way. There supposedly is a way to put single unofficial parts in a folder named 'unofficial' in a non-zipped library to reduce the risk of using unofficial parts without noticing, but I haven't managed to do this.
To update either the official or the unofficial library, just download the new version and replace the files in ~/leocadlib.

Holger

Thanks i'l give that a try and post results if there are problems.
**[COLOR=#b22222]Happy Holidays[/COLOR] [COLOR=#008000]for now[/COLOR]**

---

### Post by nocruoro on 2019-12-26
> **Holger_Gehrke said:**
> Try this: 
create a new folder 'leocadlib' in your home directory. Put the [complete.zip]("http://www.ldraw.org/library/updates/complete.zip") and the [ldrawunf.zip]("https://www.ldraw.org/library/unofficial/ldrawunf.zip") from ldraw.org in that folder. Start leocad. Select View->Preferences from the menu, go to the tab general and enter the complete path **and name** of the complete.zip into the field 'custom parts library' (example: /home/nocruoro/leocadlib/complete.zip). Close leocad and start it again. You should now have access to both the official and the unofficial parts (leocad 'knows' about the existence of ldrawunf.zip and if it's found in the same directory as the official library it gets loaded, too).

Remember the dire warnings about unofficial parts on ldraw.org, they are still in development and are subject to change without notice until they get promoted to being official parts. Projects that use unofficial parts usually get messed up if point of origin or standard orientation of an unofficial part changes during its further development.
Another problem is that leocad does not tell you whether a part is official or not, the library shows them all the same way. There supposedly is a way to put single unofficial parts in a folder named 'unofficial' in a non-zipped library to reduce the risk of using unofficial parts without noticing, but I haven't managed to do this.
To update either the official or the unofficial library, just download the new version and replace the files in ~/leocadlib.

Holger

> **nocruoro said:**
> Thanks i'l give that a try and post results if there are problems.
**[COLOR=#b22222]Happy Holidays[/COLOR] [COLOR=#008000]for now[/COLOR]**

Unfortunately no luck my intended folder path **/home/kristjan/Downloads/leocadlib **is not working. the new bricks don't show even if i go into view/preferences and set leocad to either complete.zip or ldrawunf.zip. Both are already extracted folders 
[ATTACH=CONFIG]284686[/ATTACH]

---

### Post by Holger_Gehrke on 2019-12-26
Did I say anything about extracting the zip-files ? Put both zip-files into that folder as they are. Give the path and filename for the official parts zip as the library. The zip with the unofficial parts will get picked up automatically if both are in the same folder and you give the official one as the library. My (previously stated but mistaken) belief that leocad couldn't work with compressed libraries stems from a slightly stupid file selector that only lets you select folders for libraries. You have to type in the name of the file to get it to work with a zip.

Holger

---

### Post by nocruoro on 2019-12-27
> **Holger_Gehrke said:**
> Did I say anything about extracting the zip-files ? Put both zip-files into that folder as they are. Give the path and filename for the official parts zip as the library. The zip with the unofficial parts will get picked up automatically if both are in the same folder and you give the official one as the library. My (previously stated but mistaken) belief that leocad couldn't work with compressed libraries stems from a slightly stupid file selector that only lets you select folders for libraries. You have to type in the name of the file to get it to work with a zip.

Holger

Thanks it finally worked :) Only problem is it always crashes and closes at random. Is there a workaround to prevent this crashing? There is no error message.

---

### Post by Holger_Gehrke on 2019-12-27
Tried it and yes, it crashes for me too. Starting it in the terminal only gives me a 'Speicherzugriffsfehler' (memory access violation) when it crashes. When I moved ldrawunf.zip out of the directory so that it wouldn't get used it I couldn't make it crash. Then I put ldrawunf.zip back into the library directory, moved complete.zip out and set leocad to use only ldrawunf.zip as it's library and it crashed when going through the library. According to 'unzip -t ldrawunf.zip' the file is OK, so it's not a broken zip. Seems like there are some parts in the unofficial library that leocad does not like. Scrolling around the list makes leocad access (and draw) these parts. I only need to open the 'Animals' list with the unofficial library active to get a crash. Since this is basically an untested collection of parts on some of which work is still ongoing it's not surprising that some parts are broken, but this shouldn't crash the program.

I then tried the appimage from leocad.org with the current version and that didn't crash in more than 10 Minutes of going through the 'all parts' list with the unofficial parts active, both slowly going from screen to screen and jumping around using the scroll wheel or the scroll bar. It also didn't crash on the 'Animals' list. So it's probably a bug which was discovered and fixed between 18.01 (which is in the Ubuntu repositories) and 19.07.1 (which is in the appimage). There are two parts in the 'Animals' categorie that don't get drawn (the popup-message on mouse-over identifies them as '27062p1.dat' and '27062p2.dat'; these seem to be differently textured variants of the parrot '27062.dat'), but no crash. Trying to access these parts in the version installed from the repos crashes the program. Removing these two .dat-files from the 'parts' directory inside 'ldrawunf.zip' clears up that particular crash. Of course I can't be certain that these are the only parts that are this badly broken. 

So I'd advise you to use the appimage which doesn't crash on bad parts in the library. Using an appimage isn't all that complicated. Create a directory named 'bin' in your home directory (this name is special; if a directory of that name exists it will be added to the list of directories that are searched for programs by the shell; this doesn't happen when the directory is created but at the next start of the shell, which is why I give a full path to the executable later on in the .desktop file; if I gave just the name of the program file (like I have done on my system, where ~/bin has existed for years) you'd have to log out and back in to make it work). Download the appimage into that directory. Change the permissions on the file to make it executable (either in the file manager or with 'chmod u+x ~/bin/LeoCAD-Linux-19.07.1-x86_64.AppImage' in a terminal). If you're happy with using the terminal to start it you're done ... To make it possible to call this from whatever launcher or menu your desktop environment uses, two more steps are necessary: copy the .desktop file for leocad from the system wide directory for desktop files to your personal directory: 'cp /usr/share/applications/leocad ~/.local/share/applications/', open it in an editor ('nano ~/.local/share/applications/leocad.desktop'), change the line starting with 'Exec=' to 'Exec=/home/kristjan/bin/LeoCAD-Linux-19.07.1-x86_64.AppImage %f', save and exit. If you start leocad now and choose 'Help'->'About' in the menu it should give it's version as 19.07.1. You could now remove the old version you installed from the repositories with 'sudo apt remove --purge leocad' in a terminal.

Holger

---

### Post by nocruoro on 2019-12-28
> **Holger_Gehrke said:**
> Tried it and yes, it crashes for me too. Starting it in the terminal only gives me a 'Speicherzugriffsfehler' (memory access violation) when it crashes. When I moved ldrawunf.zip out of the directory so that it wouldn't get used it I couldn't make it crash. Then I put ldrawunf.zip back into the library directory, moved complete.zip out and set leocad to use only ldrawunf.zip as it's library and it crashed when going through the library. According to 'unzip -t ldrawunf.zip' the file is OK, so it's not a broken zip. Seems like there are some parts in the unofficial library that leocad does not like. Scrolling around the list makes leocad access (and draw) these parts. I only need to open the 'Animals' list with the unofficial library active to get a crash. Since this is basically an untested collection of parts on some of which work is still ongoing it's not surprising that some parts are broken, but this shouldn't crash the program.

I then tried the appimage from leocad.org with the current version and that didn't crash in more than 10 Minutes of going through the 'all parts' list with the unofficial parts active, both slowly going from screen to screen and jumping around using the scroll wheel or the scroll bar. It also didn't crash on the 'Animals' list. So it's probably a bug which was discovered and fixed between 18.01 (which is in the Ubuntu repositories) and 19.07.1 (which is in the appimage). There are two parts in the 'Animals' categorie that don't get drawn (the popup-message on mouse-over identifies them as '27062p1.dat' and '27062p2.dat'; these seem to be differently textured variants of the parrot '27062.dat'), but no crash. Trying to access these parts in the version installed from the repos crashes the program. Removing these two .dat-files from the 'parts' directory inside 'ldrawunf.zip' clears up that particular crash. Of course I can't be certain that these are the only parts that are this badly broken. 

So I'd advise you to use the appimage which doesn't crash on bad parts in the library. Using an appimage isn't all that complicated. Create a directory named 'bin' in your home directory (this name is special; if a directory of that name exists it will be added to the list of directories that are searched for programs by the shell; this doesn't happen when the directory is created but at the next start of the shell, which is why I give a full path to the executable later on in the .desktop file; if I gave just the name of the program file (like I have done on my system, where ~/bin has existed for years) you'd have to log out and back in to make it work). Download the appimage into that directory. Change the permissions on the file to make it executable (either in the file manager or with 'chmod u+x ~/bin/LeoCAD-Linux-19.07.1-x86_64.AppImage' in a terminal). If you're happy with using the terminal to start it you're done ... To make it possible to call this from whatever launcher or menu your desktop environment uses, two more steps are necessary: copy the .desktop file for leocad from the system wide directory for desktop files to your personal directory: 'cp /usr/share/applications/leocad ~/.local/share/applications/', open it in an editor ('nano ~/.local/share/applications/leocad.desktop'), change the line starting with 'Exec=' to 'Exec=/home/kristjan/bin/LeoCAD-Linux-19.07.1-x86_64.AppImage %f', save and exit. If you start leocad now and choose 'Help'->'About' in the menu it should give it's version as 19.07.1. You could now remove the old version you installed from the repositories with 'sudo apt remove --purge leocad' in a terminal.

Holger

It is easiest to avoid the animal parts and regularly save progress instead. if only if was easier to drag and connect pieces instead of the clumsy arrow system.

---

