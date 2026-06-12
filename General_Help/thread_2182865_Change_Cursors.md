---
title: "Change Cursors"
date: 2013-10-22
forum: General Help
---

### Post by linuxnewbie3 on 2013-10-22
Hey,

I downloaded cursors from this [LINK](http://gnome-look.org/content/show.php/Aero+Mouse+Cursors+with+Drop+Shadow?content=67833) and I installed them with Tweak Tool. 

Unfortunately the cursor is only changed in some of the applications, in some other cases it is still the old one.

How can I change that?

---

### Post by stinkeye on 2013-10-22
Ok this is an example where I downloaded the "Aero Mouse Large with Drop Shadow" cursor from your link.
You need to register and select your cursor with galternatives as well as changing the dconf setting.
Using one of the tweak tools only changes the dconf setting which is why your cursor is inconsistent.

Firstly install galternatives.....(via terminal)
```
sudo apt-get install galternatives
```

Downloaded theme to download folder and then extacted to give a ~/Downloads/[COLOR="#FF0000"]aero-large-drop[/COLOR] folder.
The theme does not have a **cursor.theme** file.
I need to create a **cursor.theme** file to use with galternatives.
Open gedit and copy and paste this  and save as **cursor.theme** to the themes folder. ([COLOR="#FF0000"]use your themes folder name[/COLOR])...
```
[Icon Theme]
Inherits=[COLOR="#FF0000"]aero-large-drop[/COLOR]
```
...where [COLOR="#FF0000"]aero-large-drop[/COLOR] is the name from my theme folder.
[ATTACH=CONFIG]247163[/ATTACH]

Now I need to move the **~/Downloads/aero-large-drop** folder to **/usr/share/icons**
Open your file browser  to where your downloaded theme is 
then open another browser  with admin privileges(via terminal)...
```
gksudo nautilus /usr/share/icons
```
Drag and drop your theme into **/usr/share/icons**.
While you have **/usr/share/icons** open go to your newly added theme's folder, open the folder
and right click copy the **cursor.theme**  file.
This will save the path to your clipboard.

Now I need to register and select the theme with galternatives.
Open galternatives and select **x-cursor-theme** in the left panel.
Click on the add button and paste in the path you copied earlier.
Hit ok, choose your newly added theme and close.
[ATTACH=CONFIG]247164[/ATTACH]  [ATTACH=CONFIG]247165[/ATTACH]

Now all you need to do is select your theme in one of the tweak tools.
I could also do this with the terminal command...
```
gsettings set org.gnome.desktop.interface cursor-theme [COLOR="#FF0000"]aero-large-drop[/COLOR]
```

Log out/in to complete the change.

There may be more info than you need but I've written so anyone can follow.

---

