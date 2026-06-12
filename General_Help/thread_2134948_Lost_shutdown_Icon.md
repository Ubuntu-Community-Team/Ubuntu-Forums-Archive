---
title: "Lost shutdown Icon"
date: 2013-04-12
forum: General Help
---

### Post by nealaustin on 2013-04-12
I installed Lubuntu 12.10 and was messing with the panel and all of a sudden the shutdown icon was gone. Any Idea where to find it again? Been looking for about an hour now.

---

### Post by Locus Kiesselbachi on 2013-04-12
LOL! :D
Is taskbar still there? What about taskbar menu?

---

### Post by nealaustin on 2013-04-12
The taskbar is still there. I guess it was the taskbar I was messing with. Just no !@#$%^ shutdown icon. It seems as though it went from all the way on the right to moving around as I was moving other things. and the it was gone.

---

### Post by Locus Kiesselbachi on 2013-04-12
Well I have "Taskbar menu" icon and I choose "Logout" from there, after that, there is "shut down". So I understand you have managed to somehow by some wizardry get "shut down" button to taskbar? Hey, cool - I want that too. :)

---

### Post by nealaustin on 2013-04-12
I am using Lubuntu which does not have the launcher but there is at the bottom a panel with a sys-tray as a part of it. It had the shutdown button on it to begin with. But I have lost it

---

### Post by Routhinator on 2013-04-12
This may sound silly however I had this issue in Gnome2 at one time due to a corrupt GTK theme.. try switching out your theme. You never know.

---

### Post by Locus Kiesselbachi on 2013-04-12
naelaustin!
Try to remember how you got @shut down button to taskbar anyway? I try to summon it also, becouse I want it! :)
I think I can help you like that.

---

### Post by nealaustin on 2013-04-12
> **Locus Kiesselbachi said:**
> nealaustin!
Try to remember how you got @shut down button to taskbar anyway? I try to summon it also, becouse I want it! :)
I think I can help you like that.

You would have to switch to Lubuntu or another distro ,maybe Xubuntu. Otherwise I don't think that would work. As I explained I switched from Ubuntu to Lubuntu.I am working with a netbook and Lubuntu is customized for older and weaker computers. The price that you pay is missing features such as not being able to make a shortcut or customize icons. (Nautilus is a pretty darn good tool, but a power hog) I did find a way to shut down in the windows (GAG) type menu on the left lower corner where your trash bin is.

---

### Post by Locus Kiesselbachi on 2013-04-12
I have Lubuntu 12.10 and 11.10 on another machine. Otherwise I wouldnt bother.

---

### Post by Dennis N on 2013-04-12
> **nealaustin said:**
> I installed Lubuntu 12.10 and was messing with the panel and all of a sudden the shutdown icon was gone. Any Idea where to find it again? Been looking for about an hour now.

You can reset the panel to it's original state with this command:[B]

lxpanelctl restart[/B]

The shutdown button will reappear.

---

### Post by nealaustin on 2013-04-13
> **Dennis N said:**
> You can reset the panel to it's original state with this command:[B]

lxpanelctl restart[/B]

The shutdown button will reappear.

 Thanks alot. I really like Lubuntu. My little System 76 Starling Netbook once again purrs like a kitten. With today's internet it sure is hard for these netbooks to keep up. I at one point I had to get a cheap HP windows laptop for work related programs. I mostly use this netbook though because the keyboard has such a good tactile feel to it. Also it isn't as flimsy as the HP. The only problem that I have had was when I did an update on an unreliable wireless system while on vacation. Boy did that screw things up. Wiped it clean and haven't had a problem since. The HP has hardware issues already. I think Lubuntu will help keep this netbook alive for quite a while.

---

### Post by TREESofRIGHTEOUSNESS on 2013-04-13
Actually there is a *simple* way to fix this problem if you run into it...open your terminal (Ctrl+Alt+T)
```

 gksu leafpad /usr/share/applications/lubuntu-logout.desktop

```
find this line and change it, then save it.
```

NoDisplay=true --> NoDisplay=[B]false 
[/B]
```
Then Right click your panel --> Add/Remove Panel Items --> Add --> Application Launch Bar
Find your shutdown icon (I think it is in system)
and now you have your logout dialog back.

If you have any further questions feel free to pm me... I have tweaked Lubuntu quite a bit, so I may have come across whatever it is you are trying to do.

---

### Post by Locus Kiesselbachi on 2013-04-15
Hello!
I discovered that I already had "shutdown" button, so I lost it and got same problem as you have.
I asked Uncle Google.
This is how you get it back ([source]("http://cipricuslinux.blogspot.com/2012/07/add-shutdown-button-to-lxpanel.html")):
in terminal
```
sudo leafpad /usr/share/applications/lubuntu-logout.desktop
```
I made copy of my file, look that it is exactly the same, you may over-copy it.
```
[Desktop Entry]Name=Shutdown
Name[zh_TW]=&#38364;&#27231;
Comment=Shutdown or Reboot
Icon=system-shutdown-panel
Exec=lubuntu-logout
#NoDisplay=true
Type=Application
Categories=Settings;DesktopSettings
```
So right click in Taskbar, "Add/Remove Panel Items", select "Application Launch Bar" (you may add second/new one), edit, Preferences, ...theres should be a "shut down" button (!). Add it!

Best wishes!

---

