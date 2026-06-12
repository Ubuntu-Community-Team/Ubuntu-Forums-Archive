---
title: "KDE File Manager"
date: 2006-11-26
forum: General Help
---

### Post by Frunktz on 2006-11-26
Hi!
Is possible in Konqueror save the profile view for only a certain directory?
For example
/home/aaaaaaa/ -> Big icons
/home/aaaaaaa/Directory1 (and subdirs) -> Detailed View
/home/aaaaaaa/Docs -> Big Icons

Of course without change each time the aspect type.

Thanks

---

### Post by solarwind on 2006-11-26
> **Frunktz said:**
> Hi!
Is possible in Konqueror save the profile view for only a certain directory?
For example
/home/aaaaaaa/ -> Big icons
/home/aaaaaaa/Directory1 (and subdirs) -> Detailed View
/home/aaaaaaa/Docs -> Big Icons

Of course without change each time the aspect type.

Thanks

Yes of course. Just open up Konqueror , go to your directory, create a new view profile and check remember URLs or something like that. I'm on a mac right now so I cant actually see it and tell you step by step, sorry.

---

### Post by Frunktz on 2006-11-26
Well, I've created a default profile for Konqueror (File Manager) and it's ok, but If I use your way, I must open XX konqueror profile for navigate in some directory under /home
I would to know if there's a way to set ".directory" and add some flag that customize the aspect view. Now in .directory I have only the icon of the folder.

---

### Post by glave on 2006-12-12
I was just hunting the functionality myself, and I stumbled on this:
```
Chapter 8. Saving Settings & Profiles
Pamela Roberts 
Revision 3.2 (2003-11-06)
General Settings
When you close down Konqueror your current View menu settings (such as the View Mode, Use index.html and Show Hidden Files  items) are not automatically saved as the default options; however, you can have Konqueror remember these settings by selecting Settings->Save View Profile "Web Browsing"... and the current setting will become the default option to be used the next time Konqueror is started.
But you can also specify different View menu settings for an individual folder. To do this check the View Properties Saved in Folder box in the Settings menu, change the View settings to whatever you want then uncheck the View Properties saved in Folder box. Doing this creates a .directory file in that folder to hold the folder View settings. Use the  Settings->Remove Folder Properties option to remove the folder specific settings (or just delete the .directory file).
Note
One nice use of this feature is if you have a folder full of pictures. You can set that particular folder to display thumbnails of the pictures (by choosing Icon View and Preview->Show Previews from the View menu) when you open it, while not displaying images as thumbnails in other folders.
```

---

### Post by Frunktz on 2006-12-12
Yes!!
I search right that function..
But I don't find that voice in the menu...Grrr..

---

### Post by aysiu on 2006-12-12
> To do this check the View Properties Saved in Folder box in the Settings menu, change the View settings to whatever you want then uncheck the View Properties saved in Folder box. Where is this? 

Can someone post a screenshot of this part of the settings menu?

---

### Post by Frunktz on 2007-01-13
Up!
Anybody can post a screenshot of that feature? I try to restore original Konqueror menù because Kubuntu Konqueror is a light version, but I cannot find that.

---

### Post by strabes on 2007-04-23
I am also unable to find thsi option. Perhaps it was in an old version of konqueror? This feature would be really nice for browsing my image directories so I don't always have to go to view, view mode, icon view.

---

### Post by strabes on 2007-05-12
bump

---

### Post by kebes on 2007-05-12
The issue is that Kubuntu makes some modifications to Konqueror to make it more streamlined and user friendly. In doing so, many menu items have been removed. For example there is no menu item for "show terminal" but the functionality still exists (press F8 to toggle it).

Similarly the menu options for controlling per-folder view settings have been suppressed. This site:
[http://seerofsouls.com/wiki/How-Tos/KonquerorIconSizeIssue](http://seerofsouls.com/wiki/How-Tos/KonquerorIconSizeIssue)

Appears to explain what to do to fix this, if it's important to you. I have not tried it yet, so I don't know if it works...

---

### Post by strabes on 2007-05-13
That site neither fixed this nor added new options into konqueror. Very frustrating.

---

### Post by strabes on 2007-07-31
Fixed: [http://ubuntuforums.org/showthread.php?p=3112826#post3112826](http://ubuntuforums.org/showthread.php?p=3112826#post3112826)

---

### Post by Frunktz on 2007-08-05
Fantastic!

---

