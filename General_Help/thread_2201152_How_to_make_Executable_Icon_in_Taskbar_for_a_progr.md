---
title: "How to make Executable Icon in Taskbar for a program??"
date: 2014-01-22
forum: General Help
---

### Post by secuono on 2014-01-22
This question has been bugging me dang near forever! Have a program I use all the time and wanted to make an Executable Icon I can click and run from the Taskbar. In Windows, all I had to do was drag the program to the Taskbar and it would make an Icon for it. How do I do this in Lubuntu?
Thanks.

---

### Post by stinkeye on 2014-01-22
By default the lxpanel has an "application launchbar applet" enabled
Right click on the panel > panel settings

Goto the panel applets tab and highlight the "application launch bar" and click the edit button.
[ATTACH=CONFIG]249677[/ATTACH]

Then you can choose applications from the right column to add to the left and reorder them if needed.
[ATTACH=CONFIG]249678[/ATTACH]

---

### Post by secuono on 2014-01-23
It's not there. It isn't a program that was installed by the Packet Manager. It's a file I downloaded and placed in a folder and then double click it, pressing Execute when the window pops up. 
Also, is it possible to put that file into Home directory? I can only put it in the Users folder and it's supposed to go into Home. 

Here's the program, last one at the bottom.
[http://www.kintraks.com/downloads.htm]("http://www.kintraks.com/downloads.htm")

---

### Post by Dennis N on 2014-01-23
The program needs to be added to the main menu first. Then you can add it to the application launch bar on the panel. 

Before starting, put the program folder somewhere in your home folder. You might want to put it inside a subfolder like ~/Programs. 

To add it to the main menu, you only need to create a .desktop file for it. This is just a text file. Here is an example made for **atari800** program which had no menu entry after installation from the repository:

```
[Desktop Entry]
Type=Application
Name=Atari 800 Emulator
Comment=Run Atari 800 games
Icon=/usr/share/icons/atari1.png
Exec=/usr/bin/atari800
Terminal=false
Categories=Game;

```

You could modify this for your program. Change the Name, Comment (which becomes the tooltip), Icon (full path to icon), Exec (full path to executable), and Categories (menu category)

Name the file with the extension **.desktop** and save it to **~/.local/share/applications**. I named this one [B]atari800.desktop
[/B]

After it's saved, log out and log in and the entry should appear somewhere in the main menu (games in my case). Then, you can add it to a launch bar on the panel as described in previous post.

I had to make my own icon. You may have to do the same if none is available.

Reference on registered categories you can use: [http://standards.freedesktop.org/menu-spec/latest/apa.html](http://standards.freedesktop.org/menu-spec/latest/apa.html)

[891]

---

### Post by secuono on 2014-01-23
File saved as Kintraks.desktop in ~/.local/share/applications.
Restarted, can't find anything. Had made a tiny pic showing KT saved as .png.
I can find the file, it's in the right place. Am I missing a step?
The link you sent me confuses the tar outta me. 

[Desktop Entry]
Type=Application
Name=Animal Breeder 50702
Comment=Run Animal Breeder office
Icon=/home/secuono/Documents/Kintraks
Exec=/home/secuono/Kintraks
Terminal=false
Categories=Office;

---

### Post by Dennis N on 2014-01-23
> **secuono said:**
> File saved as Kintraks.desktop in ~/.local/share/applications.
Restarted, can't find anything. Had made a tiny pic showing KT saved as .png.
I can find the file, it's in the right place. Am I missing a step?
The link you sent me confuses the tar outta me. 

[Desktop Entry]
Type=Application
Name=Animal Breeder 50702
Comment=Run Animal Breeder office
Icon=/home/secuono/Documents/Kintraks
Exec=/home/secuono/Kintraks
Terminal=false
Categories=Office;

I think the executable is wrong. I downloaded the package and the directions say there is an executable file "Kintraks" in the Kintraks folder. There isn't, or did I get the wrong package? The file "Animal Breeder 50702" is executable, so I tried that. It started up, but crashed after I saw the startup screen with the picture of the dogs. But if it runs for you, great. Your **Exec=** line probably should be:

**Exec=/home/secuono/Kintraks/"Animal Breeder 50702"**

You need the quotes since the file name has spaces in it. OR you could rename that file without spaces, such as Animal_Breeder_50702.

**Exec=/home/secuono/Kintraks/Animal_Breeder_50702**

I ran it from the terminal, and got the error message - Segmentation fault - each time. 

```
dn@Sydney:~$ /home/dn/Programs/Kintraks/"Animal Breeder 50702"
Segmentation fault

```

The **Icon= line** is also wrong - you need to name the image file too. Maybe:
  
**Icon=/home/secuono/Documents/Kintraks/xxxxx.png** (replace xxxxx with the file name of course)

if it's in the Kintraks folder.

Make those fixes and log out and in. Look again in the menu.

[892]

---

### Post by Dennis N on 2014-01-23
Here's a short eference on the LXDE wiki about .desktop files, menus and adding things to the menu. It may be worth studying.

[http://wiki.lxde.org/en/Main_Menu](http://wiki.lxde.org/en/Main_Menu)

[893]

---

### Post by secuono on 2014-01-23
Ok, did those and restarted.
An error popped up. After that, went to find the text to look at it and noticed it had moved my icon pic file over to .local/share.
Was that supposed to happen?
There's still no icon in Office or in any of the selections.

Whaaa......Um, clicked the icon file w/the pic KT and it's actually the text document......Was that supposed to happen? The text doc gets the program icon as it's own pic/icon???
The file is called Kintraks.desktop when you open to edit. But if you check the info of the file via Properties, it's name is KTraks.

[Desktop Entry]
Type=Application
Name=KTraks
Comment=Run Animal Breeder office
Icon=/home/secuono/Documents/Kintraks/kt.png
Exec=/home/secuono/Kintraks/KTraks
Terminal=false
Categories=Office;


[ATTACH=CONFIG]249695[/ATTACH][ATTACH=CONFIG]249696[/ATTACH][ATTACH=CONFIG]249697[/ATTACH][ATTACH=CONFIG]249698[/ATTACH]

---

### Post by monkeybrain20122 on 2014-01-24
Well where did you put the Kintraks folder?

The executable is "Animal Breeder 50702" so your Exec line is definitely wrong, it has to be **the path to the executable**. If you put the folder in your home, then you should have (make sure that the file "Animal Breeder 50702" is executable, right click > Properties > Permissions>  allow executing file as a program and check it)

Exec="/home/secuono/Kintraks/Animal Breeder 50702" 

Not sure why you put the icons in Documents, you should put it in the same folder, there doesn't seem to be an icon that comes with the program, so you may download one online , say xxx.png and put it in the same folder (/home/secuono/Kintraks), and then

Icon=/home/secuono/Kintraks/xxx.png 

The .desktop file should go to .local/share/applications. The Kintraks folder should remain in your home. Also make sure your desktop file is executable as a program ( right click > Properties > Permissions>  allow executing file as a program and check it)

---

### Post by Dennis N on 2014-01-24
@monkeybrain20122

The permission should be ok, since the program works now with double-click. 

@secuono

Suggestion: As a test if everything is correct, rather than look in the menu for the launcher, open PCManFM file manager and browse to **~/.local/share/applications** where the .desktop file is located. Using the file manager's icon view mode (View > Icon View) you should see the program launcher with name and icon, and it should work to launch your program from there if you double-click on it. Try it. **If you don't see your icon, the path to the icon is probably wrong. If the program won't start, the path to the executable is probably wrong.** 

Right now, you still have the **Exec=** path wrong in post #8. You have still left out the file name of the executable at the end of the path. See my post #6, or monkeybrain20122's post #9.

Once all is fixed, Lubuntu will find it and include it in the applications menu. The menu is built from the .desktop files in various locations (including ~/.local/share/applications) when you log in. By the way, if it can't find a valid category, your program will appear under the "Other" category.

Finally, you can then follow post #2 and create a launcher on the panel.

Note: My working atari icon is a 48x48 png file. It's full size on a separate program launch panel I use on the left side of the screen. It is scaled down by Lubuntu in the applications menu to match the other icons there in size.

[894]

---

### Post by stinkeye on 2014-01-24
Test your exec command in the terminal so at least you know that part of the .desktop file works.

---

### Post by secuono on 2014-01-24
There is no share/applications folder. There's a menu://applications that I can see on the left side when I open any folder.
I changed file names last time. Program to KTraks and the icon to KT.png
File Properties, General/Permissions. Permissions lists Owner, Group, Access control- View content:anyone, Change content:anyone, Execute:anyone. There is no option for 'allow executing file as a program'
Moved the icon file to the kintraks folder. Paint program saves to Documents, didn't realize it had to be in the same folder.

Exec=/home/secuono/Kintraks/KTraks.Document
or 
Exec=/home/secuono/Kintraks/KTraks
?

Changed the .desktop file to Anyone can execute. 
I'll restart and see if it helps.

---

### Post by Dennis N on 2014-01-24
> **secuono said:**
> There is no share/applications folder. There's a menu://applications that I can see on the left side when I open any folder.
I changed file names last time. Program to KTraks and the icon to KT.png
File Properties, General/Permissions. Permissions lists Owner, Group, Access control- View content:anyone, Change content:anyone, Execute:anyone. There is no option for 'allow executing file as a program'
Moved the icon file to the kintraks folder. Paint program saves to Documents, didn't realize it had to be in the same folder.

Exec=/home/secuono/Kintraks/KTraks.Document
or 
Exec=/home/secuono/Kintraks/KTraks
?

Changed the .desktop file to Anyone can execute. 
I'll restart and see if it helps.

OK, so "Animal Breeder 50702" was renamed KTraks. Then the **Exec=** line should be:

[FONT=Courier New]Exec=/home/secuono/Kintraks/KTraks[/FONT]

The **Icon=** line should now be the same except for the file name at the end.

[FONT=Courier New]Exec=/home/secuono/Kintraks/KT.png[/FONT]

I think you should follow the suggestion made to you in Post #10 and check the .desktop file in ~/.local/share/applications. Does the icon appear? Does it start when you double-click?

If it fails that check, you then have to troubleshoot the paths and filenames in Exec= and Icon= until they are correct. 

Also note my comment in Post #10 about icon size. It shouldn't be too big.

[896]

---

### Post by secuono on 2014-01-24
Icon is 36x28
There is no ~/.local/share**/applications**  
There's just ~/.local/share

Error 
The specified directory is not valid


Is the Icon= Supposed to stay as Icon= or be changed to Exec=  ?

---

### Post by Dennis N on 2014-01-24
> **secuono said:**
> Icon is 36x28
There is no ~/.local/share**/applications**  
There's just ~/.local/share

Error 
The specified directory is not valid
Is the Icon= Supposed to stay as Icon= or be changed to Exec=  ?

You should create the **applications** folder if it's missing. Use PCManFM, navigate to **~/.local/share** then **File > Create New > Folder**.

**Icon=** should not be changed. Put in the path to your icon. Even if you don't put anything after **Icon=** it will still work, give you a generic file icon and a menu entry. I tried it.

I had some time at lunch to test a .desktop file, which I called **kintraks.desktop** It is in **~/.local/share/applications**

```
[Desktop Entry]
Version=1.0
Name=Kintraks
Comment=My New Program
Exec=/home/dn/Programs/Kintraks/Ktraks
Icon=galculator
Terminal=false
Type=Application
Categories=Office;
StartupNotify=true

```

It works, and a menu entry appears under Office as expected. I did not have to log out, it was created as soon as I saved the file to ~/.local/share/applications.  I temporarily used the icon from the galculator program just to have an icon. Even if you don't supply an icon, it still makes an entry in the menu under Office.

You can see by the **Exec=** line where I put the Kintracks folder.

Note:
I even got the program to open to it's main window in Lubuntu 13.10. It crashed in Lubuntu 12.10 that I previously tried it on.

Success is close.

Good Luck.

[897]

---

### Post by monkeybrain20122 on 2014-01-24
> **secuono said:**
> Icon is 36x28
There is no ~/.local/share**/applications**  
There's just ~/.local/share

Error 
The specified directory is not valid


Is the Icon= Supposed to stay as Icon= or be changed to Exec=  ?

Icon=path to icon
Exec=path to executable

Well I see your confusion. The icon is just a picture (typically a .png file), it is not a program. In Windows you call everything an "icon" but an "icon" that is clickable to launch an application is not really an "icon" but a launcher.  Here the equivalent is the .desktop file which points to the executable (Exec=....) and the icon is just a (any) picture that it links to (Icon=...)

It is odd that you don't have ~.local/share/applications. How did you install lubuntu? Anyway, you can just create it. In any case the .desktop file would work no matter where you put it (assuming you have made it executable), if it contains the correct path to the executable clicking it should launch the applications. Putting it in ~/.local/share/applications is for it to appear in the menu.

P.S if you want your program to appear in the right click "open with" options change the exec line to
Exec=/home/secuono/Kintraks/KTraks %F

---

### Post by secuono on 2014-01-24
I installed Lubuntu on this desktop on Tuesday, not sure how or why Application was missing. Got the file to make the CD from below link 4-6mo ago-
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu/13.04](https://help.ubuntu.com/community/Lubuntu/GetLubuntu/13.04)


I installed some random games from Package manager and restarted. It made it's own Application folder. 
I moved the file over to that one from the Application folder I made and POOF! It's working!!

Ugh, what a picky OS with a mind of it's own, lol. 

Thanks a ton to you guys!! =D Y'all are awesome!




Adding-
It's not there in the Panel preferences, Application launch bar to be added to the bottom bar next to the internet icon and such. But that's ok. Under Office is far better than where it was before.

---

