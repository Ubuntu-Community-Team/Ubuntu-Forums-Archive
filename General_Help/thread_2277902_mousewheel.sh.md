---
title: "mousewheel.sh"
date: 2015-05-12
forum: General Help
---

### Post by cmcanulty on 2015-05-12
I added this mousewheel.sh to my home folder and put a shortcut on my desktop but seem unable to make a shortcut to it on panel where I want it, the app is called imwheel. In fact I have never been able to make a launcher work on panel unless it is one you can pick from the available listed ones I put a name for it and command as either ```
 imwheel or mousewheel.sh
```  and nothing works
here is a link to the web explanation
[http://9m2pju.blogspot.com/2014/08/how-to-adjust-mousetouchpad-scroll.html]("http://9m2pju.blogspot.com/2014/08/how-to-adjust-mousetouchpad-scroll.html")

Here is the error I get
```
Failed to execute command ""thunar /home/cmcanulty/mousewheel.sh"".
Failed to execute child process "thunar /home/cmcanulty/mousewheel.sh" (No such file or directory)
```
but the file is there and marked executable, see screenshot[ATTACH=CONFIG]261954[/ATTACH]

---

### Post by Holger_Gehrke on 2015-05-12
To put something on a panel you need a .desktop-file either in '/usr/share/applications' or in '~/.local/share/applications'. You can use one of the files already there as a template or read the [specification for a Desktop Entry at freedesktop.org]("http://standards.freedesktop.org/desktop-entry-spec/latest/").

---

### Post by cmcanulty on 2015-05-12
so how does the xfce4 add launcher to panel work, I have never gotten that to add anything. I m afraid the link you gave is way above me, pages of code just to add something to the panel?

---

### Post by buzzingrobot on 2015-05-12
> **cmcanulty said:**
> so how does the xfce4 add launcher to panel work, I have never gotten that to add anything. I m afraid the link you gave is way above me, pages of code just to add something to the panel?

The .desktop file approach is a standard across Linux. Something is needed to associate a specific icon with a specific executable so the right thing happens when that icon is clicked. 

A developer or a packager is expected to create .desktop files to enable icons representing that tool to appear in panels, docks, overview, etc. I.e., if there's a .desktop file for Widget in /usr/share/applications or ~/.local/.share/applications, then Widget's icon will automagically be displayed where a given desktop environment displays icons.

When you create your own app -- a shell script in this case -- you also need to make a .desktop file for it if you want it to play by the same rules.  

Going by memory, to add icons to an XFCE panel you right-click on a panel and select the appropriate option. Google or the help files can explain it.

---

### Post by cmcanulty on 2015-05-12
I didn't create the app but downloaded it. I can easily add an app to the panel but I can't add a custom launcher, see the error I get above I don't care about the icon just being able to add a custom launcher

---

### Post by steeldriver on 2015-05-12
Please post the contents of your .desktop file

It looks like you are trying to invoke the script via thunar (a file manager) instead of actually running it

---

### Post by cmcanulty on 2015-05-12
sorry but I can't find it in home or .config where is it? there are a bunch of .desktop files in .local/share/applications

---

### Post by steeldriver on 2015-05-12
I mean the .desktop file that you created when you "put it on your desktop" - if you didn't create such a file, then that's where we need to start

Perhaps let's back up and start with exactly what you put on the desktop - file? symlink?

---

### Post by cmcanulty on 2015-05-12
I have the mousewheel.sh in my home folder and rt clicked it to put a shortcut on the desktop but the reason I need it on panel is so I can easily change the scrollrate without going to desktop and back to browser all the time, thanks I did follow the suggested protocol for putting it on a launcher (I think) but I keep getting  "no such file or directory" see original post

---

### Post by steeldriver on 2015-05-12
Instead of right clicking on the script, right click anywhere on the XFCE4 desktop and choose 'Create Launcher...'

[ATTACH=CONFIG]261956[/ATTACH]

Then fill in the details as appropriate: this example is to start the Geany editor, but you get the picture (your command will just be something like /home/cmcanulty/mousewheel.sh)

[ATTACH=CONFIG]261957[/ATTACH]

---

### Post by cmcanulty on 2015-05-12
that did it! wonder why I have to create a desktop launcher then it moves OK to panel but directly creating a panel launcher doesn't work, thanks!

---

