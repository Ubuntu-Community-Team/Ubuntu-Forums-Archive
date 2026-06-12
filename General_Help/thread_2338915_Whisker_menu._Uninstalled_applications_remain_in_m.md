---
title: "Whisker menu. Uninstalled applications remain in menu.(Solved not issue with Whisker)"
date: 2016-10-02
forum: General Help
---

### Post by T2uiYKb7 on 2016-10-02
When I uninstall an application not from a repository (a local .deb file for example) the application name stays in the Whisker menu (but it loses it's icon.) There's no option to remove them using the menu config GUI** (Edit: By this I mean when you right click and select "Edit applications)** and they don't appear in the normal XFCE menu.

Where abouts is the Whisker config file?

Cheers in advance, Andrew

---

### Post by yetimon_64 on 2016-10-03
> There's no option to remove them using the menu config GUI and they don't appear in the normal XFCE menu.
I assume by "menu config GUI" you are using "menulibre"; which is what you get by right clicking on the whisker menu icon in the panel and choosing "Edit Applications".

If you don't have this option you may have to install menulibre with the command "sudo apt-get install menulibre" (in terminal without the quotes).

Once you open the menu editor, menulibre, highlight the entry in the left hand side pane and try the delete button up top. I don't have an uninstalled local .deb type application to test on here but that may work if uninstalled. I have tried to use the delete button here to test on apps still installed and they return to the menu automatically, it may work though with a fully uninstalled application.

If the delete button still fails to remove the menu entry try to hide the menu entry by selecting it in the left side pane then go to the right hand section and turn on the option to "Hide from menus", that option works well here with installed applications that I don't want in the menu.

The delete option (on the top toolbar) would be best with a fully uninstalled application (I haven't been able to test here for your circumstances) but a good work around for you should be to "hide from menus". See attached screen shots ...

I was unable to find the actual config file for the menu here as well and am also interested in where it is in xubuntu installs. Cheers, yeti
[B]
Edit:[/B] just found it, if you want to try editing it manually  ...
```
mousepad ~/.config/menus/xfce-applications.menu
```

---

### Post by T2uiYKb7 on 2016-10-03
Cheers for the reply but's that's the GUI menu editor I'm talking about it doesn't list the programs and neither does the text file you mentioned (that's for the normal XFCE "start" menu.)

I'm talking about the Whisker menu that comes with Xubuntu but not other XFCE distros. It's the default menu for Xubuntu.

xfce4-whiskermenu-plugin

[http://packages.ubuntu.com/xenial/xfce4-whiskermenu-plugin](http://packages.ubuntu.com/xenial/xfce4-whiskermenu-plugin)

**Edit: If you can try yourself that'll be cool. I'll submit a bug on launch pad. Install a program from a .deb file that isn't in the Ubuntu repository then remove it using apt remove. Then see if the menu entry stays in the Whisker menu. (I know it doesn't stay in normal XFCE menu.)**

---

### Post by ajgreeny on 2016-10-03
I have never seen the behaviour you talk of either, nor do I have anything that I want to remove from the whisker menu in order to try it.

However, two possible answers spring to mind:-

1). Have a look in **~/.local/share/applications** to see if there is a **.desktop** file for the application you want to remove from the menu, and if there is, remove it.
2). Install and use **alacarte** the older main-menu editor which still seems to work on the whisker menu; you may find that does the trick for you.

---

### Post by T2uiYKb7 on 2016-10-03
Ok will do cheers.

There absolutely has to be a config file in the home directory though. It can't just use the normal XFCE menu config file because it has favorites and other custom stuff (icon size, lock button, settings button etc.) that has to be stored [B]somewhere.

[SIZE=3]Anyone know what the Whisker config file is in the home directory?[/SIZE][/B]

---

### Post by ajgreeny on 2016-10-03
The only configuration I can find for the menu is **.config/xfce4/panel/whiskermenu-51.rc** but I don't think it will help you make the sort of changes you are looking for as it configures only the settings you can change if you right click on the icon and choose Properties; it does not actually edit the menu items themselves as far as I can see.

---

### Post by T2uiYKb7 on 2016-10-03
Thank's for spending the time to track that down much appreciated.

I actually tracked down the developers email and got the same answer. (The numbers at the end of the file differ person to person.) 

Looks like this bug is specific to the software being removed and has nothing to do with any error in Whisker or XFCE.

Will close thread now.

---

### Post by ajgreeny on 2016-10-04
A sudden thought!

When you remove those non-repository applications, do you do it with the package manager, eg, **apt-get remove --purge packagename** or using one of the GUI applications and use the **Remove completely** option in that?

If not you may be left with a bit of detritus in the form of the .desktop file for the application and various other files which could be causing this.

---

