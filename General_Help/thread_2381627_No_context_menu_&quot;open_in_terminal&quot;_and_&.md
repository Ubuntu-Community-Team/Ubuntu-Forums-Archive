---
title: "No context menu &quot;open in terminal&quot; and &quot;open as admin&quot; in Nemo file manager"
date: 2018-01-03
forum: General Help
---

### Post by dzingishan on 2018-01-03
Hi, 
I run Xubuntu 16.04. I have changed default file manager from Thunar to Nemo. I set Nemo as the default file manager in the settings. Nemo is the default file manager, it opens, but in the context menu there is no "open in terminal" and no "open as admin".
On youtube I saw other using Nemo and they all have this feature, and for this feature I changed to Nemo.
You can help me to start this feature. I have Nemo 3.6.4
Kind Regards

---

### Post by Dennis N on 2018-01-03
> I have changed default file manager from Thunar to Nemo....in the context menu there is no "open in terminal" and no "open as admin". On youtube I saw other using Nemo and they all have this feature, and for this feature I changed to Nemo.

Look again at Thunar - it has both of those options, open in terminal and open as root, in the file menu and also the context menu. See the attached image. From file menu (shown) Thunar opens either the current folder if none is selected, or the selected folder. The context menu has those options when you right-click on a selected folder (but not on a file).

---

### Post by again? on 2018-01-03
I can install nemo on a live usb of Xubuntu 16.04 and both options are available although I need to install
gnome-terminal for "open in terminal" to work.
Default version of nemo for Xubuntu 16.04 is 2.8.6-2.
Did you install from a ppa?

What's your output for 
```
apt policy nemo
```

---

### Post by dzingishan on 2018-01-03
[COLOR=#222222][FONT=Verdana]> **DennisN said:**
> Look again at Thunar - it has both of those options, openin terminal and open as root, in the file menu and also the contextmenu. See the attached image. From file menu (shown) Thunar openseither the current folder if none is selected, or the selectedfolder. The context menu has those options when you right-click on aselected folder (but not on a file).[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]I have Thunar 1.6.11 and I don&#8217;t have the options that you talking about. [/FONT][/COLOR]




[COLOR=#222222][FONT=Verdana]> **guber2 said:**
> Ican install nemo on a live usb of Xubuntu 16.04 and both options areavailable although I need to install
gnome-terminal for "openin terminal" to work.
Default version of nemo for Xubuntu16.04 is 2.8.6-2.
Did you install from a ppa?[/FONT][/COLOR]


[COLOR=#222222]First I have installed Nemo 2.8.6. Because it didn&#8217;t have what I was looking for I installed Nemo from PPA and now I have Nemo 3.6.4.[/COLOR]


> **guber2 said:**
> 
[COLOR=#222222][FONT=Verdana]What'syour output for[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]```
aptpolicy nemo
```[/FONT][/COLOR]


```

[COLOR=#222222][FONT=Verdana]nemo:[/FONT][/COLOR]
[COLOR=#222222]  [FONT=Verdana]Zainstalowana:3.6.4-1~webupd8~xenial02[/FONT][/COLOR]
[COLOR=#222222]  [FONT=Verdana]Kandyduj&#261;ca:  3.6.4-1~webupd8~xenial02[/FONT][/COLOR]
[COLOR=#222222]  [FONT=Verdana]Tabelawersji:[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]***3.6.4-1~webupd8~xenial02 500[/FONT][/COLOR]
[COLOR=#222222]        [FONT=Verdana]500http://ppa.launchpad.net/webupd8team/nemo3/ubuntu xenial/main amd64Packages[/FONT][/COLOR]
[COLOR=#222222]        [FONT=Verdana]100/var/lib/dpkg/status[/FONT][/COLOR]
[COLOR=#222222]     [FONT=Verdana]2.8.6-2500[/FONT][/COLOR]
[COLOR=#222222]        [FONT=Verdana]500http://archive.ubuntu.com/ubuntu xenial/universe amd64Packages[/FONT][/COLOR]
```

---

### Post by Holger_Gehrke on 2018-01-03
You can [make these options available]("http://docs.xfce.org/xfce/thunar/custom-actions") in Thunar. The linked page in the Thunar manual explains how to set up user defined actions and has several examples, including "open in terminal", "open in terminal as root" and "open in Thunar as root".

Holger

---

### Post by dzingishan on 2018-01-03
That solve the problem.
Those actions are even better than just "open in terminal" and "open as root". Now I set myself an action like "edit in Leafpad as root" and will be able to set aditional acions under the right mouse button. 
Thunar rules !

---

### Post by Dennis N on 2018-01-03
You are right, they are custom actions (see attached image of Edit > Configure Custom Actions), but I don't recall creating them.

---

