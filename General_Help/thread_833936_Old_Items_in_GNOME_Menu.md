---
title: "Old Items in GNOME Menu"
date: 2008-06-19
forum: General Help
---

### Post by DavidCain on 2008-06-19
Okay. So, I tried installing a few things in Wine, and after an unsuccessful first attempt, I realized I didn't need/want said applications. Regardless of the back story, I tried to use Wine's uninstall feature. Instead, it just reinstalled the applications. I then tried to just purge Wine in terminal (I forget the exact syntax, but it was definitely --purge). That didn't work either, so I removed Wine from Synaptic Package Manager and simply deleted the folders containing old applications.

I know that deleting the folders wasn't exactly the best method for a clean uninstall, but I was just getting fed up. Long after I "uninstalled" all the applications, they still appear in the GNOME Menu under "Other". I know I can set them to be hidden through the "Edit Menus" option, but I'd like to erase all traces of them. This problem boils down to two few simple questions.

1) How can I remove the items from my GNOME Menu? I read that the files to edit are under /usr/share/gnome, but there's so many damn directories, I couldn't manage to just guess and check.

2) Is there anything I can do for a more complete removal of the old apps? I realize the "uninstall" was incredibly sloppy.

I apologize for the length, as I can never be brief. Thanks in advance.

---

### Post by plucky on 2008-06-19
Right click on **Applications** and select **Edit Menus**.
Select **Wine** and untick the four boxes. Wine will now not appear in the menus.


Then Open your home folder and **View Hidden Files** and delete the **.Wine** folder.


Good Luck:)

---

### Post by DavidCain on 2008-06-19
I appreciate the response, but you either didn't fully read my post or understand me (I think it's the latter, I wasn't too clear).

I'm already aware of the Edit Menu option. Not to mention, I had a clean uninstall of Wine; it's entirely gone from the menu and the .wine folder is long gone. The problem is that there are all sorts of remnants from the programs I installed with Wine.

I realize I can just hide all the options, but this seems like a temporary fix. I'm interested in completely removing all of the applications.

---

### Post by Kevanx on 2008-06-22
I'm having this same issue. 'Edit Menus' allows me to see a ton of extra things, and most of the applications previously installed under wine cannot be deleted from the menu, only unchecked.

What's more is that I just reinstalled Wine, and now there are dozens of programs that I had previously uninstalled completely!

As per another discussion's suggestions, I removed everything in /home/username/.config/menus/ because i couldn't see wine, and now I have a list of every program I ever installed under wine, instead of none of them!

As far as wine is concerned though, NOTHING is installed.

Where can I directly edit the gnome Applications panel?

*EDIT: Solutions explaind below*

Please use this at your own risk. Also, whenever someone tells you to use the rm command in a terminal, be very careful! Here, you will only be removing old menus items for wine.

1. Remove menu items.
- open up a terminal under Applications -> Accessories
- type
```
cd /home/***your username here***/.config/menus
```
this takes you to the menus folder for wine. As far as I know, this is only for wine. It should have a bunch of entries for programs that you installed.
- enter ls to list the contents of that folder
- enter the following.
```
rm -r * 
```
It will remove everything in this folder. URGENT: I don't know what happens if you use this with anything currently installed under wine. I had wine uninstalled at this point, but if you use gedit to open the .menu files, you can probably remove things by hand as needed, and won't need to remove everything from that directory.

2. Remove the directories under the applications folder.
type
```
cd ~/.local/share/applications/wine/Programs/
```
then ls to see the contents of the directory.
once again use
```
rm -r [folder name]
```
to remove whatever folders don't belong.

Via: [http://techxplorer.com/2008/04/21/removing-wine-application-entries-on-ubuntu/](http://techxplorer.com/2008/04/21/removing-wine-application-entries-on-ubuntu/)

3. After everything, in the terminal again, type
```
killall gnome-panel
``` to restart gnome. Your applications should all be gone, in theory, but I actually had two annoying applications sticking around. Fortunately, this time, going to Applications > Edit menus and then right-clicking and clicking Delete actually worked.

Hope this helps!

---

