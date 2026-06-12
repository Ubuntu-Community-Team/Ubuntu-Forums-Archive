---
title: "how to create an icon for a manually installed program?"
date: 2007-04-16
forum: General Help
---

### Post by mbil on 2007-04-16
Hi,
 I had to manually install a more recent version of Azureus than is available through the install manager. 

Now it seems to be running ok, but how do i create an icon to run the application? There is a script in the Azureus directory that runs it, but im at a loss as to how to create a 'shortcut'..
have trawled other posts but not found 'owt..

---

### Post by beerorkid on 2007-04-16
right click on the desktop  --> select create launcher --> give it a name (Azureus) --> in command put in what you need to run it --> can pick an icon by clicking the no icon button.  Not sure if you need to check run in terminal.

---

### Post by Waappu on 2007-04-16
> **mbil said:**
> Hi,
 I had to manually install a more recent version of Azureus than is available through the install manager. 

Now it seems to be running ok, but how do i create an icon to run the application? There is a script in the Azureus directory that runs it, but im at a loss as to how to create a 'shortcut'..
have trawled other posts but not found 'owt..

Hi

See if this helps you
[http://ubuntuforums.org/showpost.php?p=2422715&postcount=3](http://ubuntuforums.org/showpost.php?p=2422715&postcount=3)

---

### Post by stchman on 2007-04-16
> **mbil said:**
> Hi,
 I had to manually install a more recent version of Azureus than is available through the install manager. 

Now it seems to be running ok, but how do i create an icon to run the application? There is a script in the Azureus directory that runs it, but im at a loss as to how to create a 'shortcut'..
have trawled other posts but not found 'owt..

A lot of packages will create their own menu item.  If you install Azureus though the package manager it will install an icon in the menu.

If you go and download Azureus from sourceforge website it will be in a .tar.bz2 format.  I have not looked inside the tarball but if it contains .rpm files you are good to go.  Use alien to convert .rpm into .deb.  .deb packages Ubuntu understands.

First off get alien from package manager:

sudo apt-get install alien

Then convert the .rpm files to .deb

sudo alien -k *.rpm

When done do this:

sudo dpkg -i *.deb

This should take care of everything.

If Azureus does not contain .rpm files for conversion you can add an item to the menu.

Right click on the Application menu and go to menu editor.

When in menu editor go to which menu you want to install to.  Then click add item.  It will ask you for a Name and path.  Provide it.  Once done you will have to restart the workspace and the new item will be in the menu.

Hope this helps.

---

### Post by mbil on 2007-04-17
thank you chaps, sorry for the delay. Worked like a dream.

Its good to see that you can do this from the GUI, altho the right click wasnt all that intuitive - in that you can only right click on the titlebar, not on the menus themselves. I had tried that originally...

---

