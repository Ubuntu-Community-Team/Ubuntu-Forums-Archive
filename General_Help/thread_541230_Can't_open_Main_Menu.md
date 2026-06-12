---
title: "Can't open Main Menu"
date: 2007-09-02
forum: General Help
---

### Post by Nistenf on 2007-09-02
Hello.

I've been using Ubuntu for a while, and I had no problems since now.
The problem I have is: When I click System/Preferences/Main Menu the configuration for main manu doen't starts.
The only thing that happens is the message that says "Starting Main Menu", but when it disapears, nothing else happen.
Here is an image:
[[IMG]http://img262.imageshack.us/img262/9681/pantallazoae7.th.jpg[/IMG]](http://img262.imageshack.us/my.php?image=pantallazoae7.jpg)
"Iniciando Menu Principal" = "Starting Main Menu"
How can I fix this and be able to configure the main menu?

Thanks in advance.

---

### Post by ThrobbingBrain66 on 2007-09-02
Open a terminal and type 'alacarte' and press enter.  What, if any, output is given?

---

### Post by Nistenf on 2007-09-02
Here is the output:


```
nistenf@nistenf-desktop:~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 42, in __loadMenus
    self.applications.path = os.path.join(util.getUserMenuPath(), self.applications.tree.get_menu_file())
  File "/usr/lib/python2.5/site-packages/Alacarte/util.py", line 135, in getUserMenuPath
    os.makedirs(menu_dir)
  File "/usr/lib/python2.5/os.py", line 172, in makedirs
    mkdir(name, mode)
OSError: [Errno 13] Permiso denegado: '/home/nistenf/.config/menus'
```

Permiso denegado = Acces denied.

---

### Post by ThrobbingBrain66 on 2007-09-02
Something is wrong with your python2.5 installation.  Try this:
```
sudo apt-get install --reinstall python2.5
```

---

### Post by Nistenf on 2007-09-02
Tried that, but nothing changed.

---

### Post by ThrobbingBrain66 on 2007-09-02
Did you try purging alacarte?
```
sudo apt-get remove --purge alacarte
```

It will want to remove ubuntu-desktop, but don't worry, its just a meta-package. Nothing important will be uninstalled.

To reinstalled both with one command, just use
```
sudo apt-get install ubuntu-desktop
```
That should pull alacarte in as well.

---

### Post by Nistenf on 2007-09-02
This week I'm not where my computer with Ubuntu is. Next week I'll try that, and will tell how it worked.

Thanks you!

---

### Post by JoshOwen on 2007-09-03
Hi there,

Hope I'm not being rude in hijacking this thread:).

Unfortunately I'm suffering the same symptoms as Nistenf....

I received the same output in the terminal re the alacarte command.

As recommended I also ran

sudo apt-get install --reinstall python2.5

&

sudo apt-get install ubuntu-desktop

followed by

sudo apt-get remove --purge alacarte

To no avail :(

I'm the ultimate Ubuntu beginner, any further suggestions re this would be gratefully received, I've googled this prob to the hilt and now seem to be ](*,)

Many Thanks in advance

---

### Post by JoshOwen on 2007-09-04
Hi Nistenf,

The only resolution I've found to this so far is to create a new user, not exactly ideal I know....

Will post again if I find anything more suitable re solving this one....

Does anyone else on the forum know why this might be?

I've only ever seen anything like this before on Windows (very new to Linux and just learning with Ubuntu). In windows you could copy the ntuser.dat file from a correctly working users profile into another which isn't. Essentially a crude registry fix.

Hope that makes sense.... Is there an equivalent User Profile structure/Registry within Ubuntu? (hopefully there isn't a registry equivalent as it's one of many flaws of windows:))

Many Thanks in advance

---

### Post by Nistenf on 2007-09-09
I did everything you told me, but the problem isn't fixed :(
And I don't wanna create another user yet...
If anybody knows a possible solution, please tell me.
Thanks in advance.

---

### Post by NoThanksM$ on 2007-11-23
BUMP

I'm having this problem as well.  This seems like a pretty basic functionality we're lacking.  Anyone have a fix for this?  Was running Feisty, now running Gutsy, exact same behavior in both.

---

### Post by phasenew on 2008-01-16
I found the solution.
the problem is the permission of the  directory  of ~/.config/menus and files under it. probably when installing some softwares, you used sudo while you should not. for me I used
sudo wine xxxx.exe to install a software. and the ownership of the directory and files were taken by the root.

the solution is:
use sudo mv to move  ~/.config/menus to somewhere else

change the access permissions to a+rw by
 sudo chmod -R a+rw ./menus

then copy back: 
 cp -r  ~/Desktop/menus ~/.config/menus

done!

---

### Post by NoThanksM$ on 2008-01-16
That did the trick for me...thank you very much for posting the solution!

---

