---
title: "All installed applications aren't showing in my application menu."
date: 2019-03-08
forum: General Help
---

### Post by jjc55 on 2019-03-08
How do I get all my applications to show in my apps menu?  It appears to only show maybe half of them. Even if I click the "all" button. However, if I navigate to the ubuntu software icon in apps menu it shows all installed apps. Is there even a way to move or somehow put shortcut icons for my entire software collection in my application menu?

---

### Post by slickymaster on 2019-03-08
*Thread moved to **General Help**.*

---

### Post by kc1di on 2019-03-08
Hello it would help if we know which desktop your using?

---

### Post by again? on 2019-03-08
If referring to the gnome-shell application overlay.
Ubuntu uses app-folders.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] gsettings [COLOR="#FF0000"]get[/COLOR] org.gnome.desktop.app-folders folder-children**
['Utilities', 'Sundry', 'YaST']
```

You can reset this value as the default value is empty. In terminal run...
```
gsettings [COLOR="#FF0000"]reset[/COLOR] org.gnome.desktop.app-folders folder-children
```

eg
```
[B][COLOR="#006400"]glen@Bionic:~$[/COLOR] gsettings [COLOR="#FF0000"]reset[/COLOR] org.gnome.desktop.app-folders folder-children
[/B]
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] gsettings [COLOR="#FF0000"]get[/COLOR] org.gnome.desktop.app-folders folder-children**
@as []
```

---

### Post by jjc55 on 2019-03-08
Oh yeah, knowing what I'm running might help. Sorry. Im running ubuntu 18.04 bionic beaver with gnome. Thanks.

---

### Post by jjc55 on 2019-03-09
I'm not sure what the above command was supposed to achieve, but it didn't appear to have any affect. I entered it into the terminal and nothing seems to have changed. One line even spit out an error message. Most likely I'm either doing something wrong, I don't know what I'm looking for, or my description was too vague and misinterpreted. Maybe I'm not properly explaining what I'm trying to accomplish. All I'm really trying to do is put all the software shortcut icons for all the installed software that I have, that is currently in "Ubuntu Software", inside the application menu that's on my dock. By that I mean the the actual button at the bottom of my dock that has the nine dots in it. From there, it takes me to a nice, full screen graphical menu layout with a bunch of application icons. At the top of the screen in the left corner, it says "Activities" , then there's a search bar in the center top. At the bottom there are two buttons that say "Frequent" and "All". So, if it's possible, I'd like to be able to have a one stop shop, with access to all my software tucked inside this menu. I mean, whether it's default installed software, or stuff that I've installed myself. As of right now, the application menu, or drawer, only shows less than half the software that I have. I apologize for the extremely detailed, super broken down description of this reply, I just feel like I perhaps was too vague in my first description. Either way, I don't think the above commands weren't quite what I was looking for, unless I did something wrong along the way. With that said; any other ideas? Thanks again.

---

### Post by Dennis N on 2019-03-09
> At the bottom there are two buttons that say "Frequent" and "All". So, if it's possible, I'd like to be able to have a one stop shop, with access to all my software tucked inside this menu. I mean, whether it's default installed software, or stuff that I've installed myself. As of right now, the application menu, or drawer, only shows less than half the software that I have.

When you click the "All" button, in addition to the icons initially displayed, there can be 2 or more pager buttons on the right side in order to display the rest of your application icons. You don't mention them, so maybe you didn't notice these.

---

### Post by jjc55 on 2019-03-09
That's right, as detailed as that description was, I forgot to mention the pager buttons. There are two little circular buttons on the right of the screen, pressing the bottom button shows more apps. But no, I did't overlook them, so yes, unfortunately the problem still exists. Any ideas?

---

### Post by Dennis N on 2019-03-09
Well, I can see one application that is on my Ubuntu dock that's not included in the 'All' display: Tilix terminal. It does show up in the top panel Applications Menu, so I'm not sure at the moment why it's not in the display.

---

### Post by Dennis N on 2019-03-09
My missing Tilix that I mentioned in my previous post and thirteen other missing utilities like System Monitor, Seahorse, Disk Usage Analyzer, Screenshot, ... were 'hidden' behind the 'Utilities' icon. Click on that and you may see some of your missing application icons.

---

### Post by jjc55 on 2019-03-09
I just checked to see if that might be the problem, but I don't have a utilities icon, or any other such icon where software might be hidden.  What I did see though is those other utilities that you mentioned actually have their own icon right on the main screen in the application menu. So it must be some other problem. In the mean time, I don't believe so, but I will open up each icon one by one just to see if there is in fact an icon that's hiding a bunch of stuff.

---

### Post by again? on 2019-03-09
Give an example of a couple of your applications you don't see in the Applications overlay.

---

### Post by Dennis N on 2019-03-09
>  I don't have a utilities icon, or any other such icon where software might be hidden.
For what it's worth, here is the Utilities icon I have (attached image). It's on all the Ubuntu 18.xx that I have looked at (4).  There is another collection-type icon called 'Sundry' which can display more applications. My 18.04 'Sundry' has dconf-editor and adobe flash player preferences. My top panel applications menu Utilities category has the same items as the Utilities icon. Sundry icon has dconf-editor, but Sundry category in Application menu doesn't; it's in Utilities. Go figure.

> So it must be some other problem.
That's seems likely. Is your Bionic Beaver a fresh install?

---

### Post by rbmorse on 2019-03-09
Pick one of the apps that doesn't show an icon in "show applications".  

With a text editor, open ```
/usr/share/applications/{name of app}
``` and find the line ```
nodisplay={boolian value}
``` If this line is set to "true", the icon for the app won't appear in "show applications". 

 If there is no file corresponding to the application in /usr/share/applications/,  look in /home/{username}/.local/share/applications (note the "." preceeding local) and see if the launcher is hiding there. 

In either case, you can fix it by changing "true" to "false".  Don't forget to save the file after you make the change.  You'll need administrator permissions if it's under the /usr directory. 

The change should take place immediately -- there is no need to restart the Gnome session to verify if this solves the problem.

---

