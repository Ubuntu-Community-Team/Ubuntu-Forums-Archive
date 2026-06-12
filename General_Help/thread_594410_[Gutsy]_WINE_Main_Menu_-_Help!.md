---
title: "[Gutsy] WINE Main Menu - Help!"
date: 2007-10-27
forum: General Help
---

### Post by grantk86 on 2007-10-27
I had some problems trying to uninstall some programs on WINE, so I uninstalled WINE, which still left the WINE menu under the Applications menu.  I deleted this, as well as the .wine folder in my Home directory.  Now, I have re-installed WINE, but the WINE menu in the applications menu is no longer available.  Does anyone know how to get this back so I don't have to use command lines to run WINE?  Thanks.

---

### Post by zvacet on 2007-10-28
system>settings>main menu>accessories>new item

1. command browse under usr/bin and select wine
2. name it as you wish

---

### Post by grantk86 on 2007-10-28
> **zvacet said:**
> system>settings>main menu>accessories>new item

1. command browse under usr/bin and select wine
2. name it as you wish

I know how to do this, however, I would like to be set up the same menu format that was present when I installed Gutsy.  There was a Wine folder in the Applications menu which listed all of the installed Wine applications, so could just pick the one I wanted and click on it.  Anyone know how to get this back?

---

### Post by vashan on 2007-10-30
hello, i've got the same problem as you. After I deleted Wine and the Menu-Bars, i couldn't get Wine completely installed again. It creates no "short-cuts". Any way to fix that? 

bye

---

### Post by MR.UNOWEN on 2007-11-02
I'm having the same trouble. Also I can't find system>settings>main menu>accessories>new item. Is it supposed to be system>Preferences>main menu?
The New Menu option doesn't allow you to brows for it. All there is, is comment and name. There's no file path or anything of that sort.

---

### Post by Dropknee on 2007-11-02
Same problem here

anyone can help??

thx

---

### Post by PAULLYN on 2007-11-03
Allrighty I've been playing a bit and this is what I've got.
  Right click the Applications Tab. Then click Edit Menus. This should bring up the Main Menu dialog. Look to see if Wine is listed, if it is just tick the box and click close and all will be restored. If Not then click New Menu, a Directory Properties dialog will open. Under Name type Wine. Then click the folder icon and a dialog will open to browse icons, Type in /usr/share/pixmaps then find the icon wine.svg, double click the icon and you will go back to dialog properties. Click OK and you've set up your folder. Now while still in the Main Menu dialog on the left in the menus list, click on the Wine icon and the items box will empty. Click on New Item and the Create Launcher dialog appears. Note that the icon is that of a launcher NOT wine's icon, so do as before to select the wine icon or alternatively you can change it to anything that suits you. In the Command line type /usr/bin/winecfg. This is the command line for the Wine Configuration dialog so name it whatever you like I used Wine Config. I think thats close to the original. Click OK and now in the Items column of the main menu it should say Wine Config with the whatever icon you chose. The original folder had a search function and a programs folder also but I've not been able to sort that part out yet, but it would involve finding the relevant files and folders and adding the launchers with appropriate icons. This worked for me and I will post if I sort out the missing bits

---

### Post by Baby Boy on 2007-11-03
I also have the same problem :(. Why on earth did I have to delete that menu? I know there is a way to get it back (almost) manually, but I would really, really appreciate if there was **any** way to get that nice menu I got when I installed Gutsy...

---

### Post by MR.UNOWEN on 2007-11-03
Couldn't someone who has wine with all the menu items, look up menu items properties and tell us what they were, so we could input them in as new menu items?

---

### Post by Dropknee on 2007-11-04
Great idea, someone with Wine, pls help us to rebuild the menu item pls.

Thx

---

### Post by JayBee808 on 2007-11-04
Under "Applications" -> "Wine":

1.  "Programs"
	[Folder]
	Name: Programs
	Comment:  	

2.  "Browse C:\ Drive"
	Type: Application
	Name: Browse C:\
	Command: xdg-open ~/.wine/drive_c
	Comment:  Browse your virtual C:\ drive

3.  "Configure Wine"
	Type: Application
	Name: Configure Wine
	Command: winecfg
	Comment:  Change application-specific and general Wine options

4.  "Uninstall Wine Software"
	Type: Application
	Name: Uninstall Wine Software
	Command: uninstaller
	Comment:  Uninstall Windows applications for Wine

---

### Post by Dropknee on 2007-11-04
Ok I guess I found the solution, this work form me, maybe for you, pls confirm it.

remove any wine you got via Synaptic or with 
```
sudo apt-get remove wine
```

and remove the .wine directory in your home

then:

```
sudo apt-get clean
```

Then reinstall Wine, and the menu for wine is there again

This work for me, pls confirm is this work for you.

---

### Post by Dropknee on 2007-11-04
This work only with Wine from the official Ubuntu repositories, not with the WineHQ one, so is you want the latest Wine, install first the Wine from the Ubuntu repo, then the WineHQ package.

---

### Post by nolan- on 2007-11-04
> **Dropknee said:**
> 

This work for me, pls confirm is this work for you.

Hi, I'm having the same problem and unfortunately this didn't work for me :(

Nol

---

### Post by Baby Boy on 2007-11-04
> **Dropknee said:**
> Ok I guess I found the solution, this work form me, maybe for you, pls confirm it.

remove any wine you got via Synaptic or with 
```
sudo apt-get remove wine
```

and remove the .wine directory in your home

then:

```
sudo apt-get clean
```

Then reinstall Wine, and the menu for wine is there again

This work for me, pls confirm is this work for you.
This *still* doesn't work for me :(.

---

### Post by Dropknee on 2007-11-04
When I installed the fist time, Wine add in the Main Menu under Application, but now I got it in Other in the Main Menu, don't know why this happen, but at last is there.

You guys are using the Wine from the Ubuntu repo?

---

### Post by Dropknee on 2007-11-05
Ok another update:

When the menu appear with the method I describe, don't know why, but when you try to go to edit menu, the Wine menu disappear........:confused:

 I'm still searching for a permanent solution to this.

---

### Post by Ooht on 2007-11-05
**EDIT:** Nothing to see here. Check my post below.

---

### Post by Dropknee on 2007-11-06
Can you pls explain the procedure more clearly

Thanks

---

### Post by Ooht on 2007-11-06
Disregard everything I said in the above post. I found a much simpler solution here:

[http://ubuntuforums.org/showthread.php?t=527580](http://ubuntuforums.org/showthread.php?t=527580)

I've tested it, and it works perfectly. Installed programs now appear in Wine --> Programs.

---

### Post by Dropknee on 2007-11-06
> **Ooht said:**
> Disregard everything I said in the above post. I found a much simpler solution here:

[http://ubuntuforums.org/showthread.php?t=527580](http://ubuntuforums.org/showthread.php?t=527580)

I've tested it, and it works perfectly. Installed programs now appear in Wine --> Programs.

Man....... you are the best!!, thanks!!! at last, this work like a charm.

I don't know why all the previous apps I install with Wine, appear there, but thats isn't a problem, I just deleted right away and restore manually the Wine Icon, don't know why this didn't appear with the icons, but again, no problem with that, I just browse to /usr/share/pixmaps/ to find the Wine icon.

Once again.... Thanks :)

---

### Post by Ooht on 2007-11-06
No problem. Glad I was able to help. :)

I had been looking for a solution to that problem for a while.

---

### Post by Baby Boy on 2007-11-07
> **Ooht said:**
> Disregard everything I said in the above post. I found a much simpler solution here:

[http://ubuntuforums.org/showthread.php?t=527580](http://ubuntuforums.org/showthread.php?t=527580)

I've tested it, and it works perfectly. Installed programs now appear in Wine --> Programs.
...I am going to kiss you now :).

---

### Post by grantk86 on 2007-11-08
> **Ooht said:**
> Disregard everything I said in the above post. I found a much simpler solution here:

[http://ubuntuforums.org/showthread.php?t=527580](http://ubuntuforums.org/showthread.php?t=527580)

I've tested it, and it works perfectly. Installed programs now appear in Wine --> Programs.

Thanks!  This works great.

---

### Post by charlesgoddard on 2008-01-19
I recently had this same issue, so I thought I would throw my resolution on this thread.  As with everyone else, after uninstalling wine and deleting the menu from "Applications", reinstalling wine would not add back the wine menu.

I'll preface this with I have two shuttles running Ubuntu.  Both are fairly new installs of Ubuntu, with the high end one only being used to run games with wine.  Also, I am in no means an expert on Ubuntu.

I started investigating this issue by looking for files that were created/updated by the wine install.  When comparing files to my pristine Ubuntu, I noticed that files in ".config" and ".local/share" where mostly changed by the wine install.

In .config is a folder called "menus".  This folder contains menu settings merged with the root menu file, and the menu changes made by the wine install.  In my case it only contained wine specific settings.

In .local/share is an "applications" folder, a "desktop-directories" folder, and an "icons" folder.  Because I only use my gaming rig for...ummm...gaming using wine, the "desktop-directories" and "icons" folders only contained wine files/folders.

In the applications folder was a "wine" folder (It was pretty obvious were this folder came from).

WARNING!! I, in no way take responsibility for the reckless abandonment performed by mimicking my actions below.  :)

Given the solid evidence that menus, desktop-directories, and wine were only created/modified by the wine install, I sent them all to the trash.

Upon reinstalling wine, I magically had a new (working) menu. \\:D/

I want to note that likely your mileage will vary.  If you have installed other applications, you may want to be more cautious.  The contents of your ,config and .local most certainly will be different.  If so, you may want to take more finesse when deleting files/folders.

---

### Post by Armada651 on 2008-05-30
A better solution would be to edit /home/<your username>/.config/menus/applications.menu. Then look for <Name>wine-wine</Name>, then remove all the <Deleted/> tags under that. It will restore all wine menus and shortcuts with their icons and won't touch anything else.

(I realize I'm responding to an old thread but this might be handy for other people who find this thread)

---

### Post by steve101101 on 2008-06-09
enter the code ...

```

gedit /home/username/.config/menus/applications.menu

```

then delete all the <Deleted> lines in the code and save.

---

