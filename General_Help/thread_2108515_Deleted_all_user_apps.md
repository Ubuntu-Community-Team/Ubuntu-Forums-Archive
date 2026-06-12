---
title: "Deleted all user apps?"
date: 2013-01-24
forum: General Help
---

### Post by rochford77 on 2013-01-24
disclamer, not really a D.E. problem...

ok, so ive been running ubuntu 12.10 with unity as my D.E for quite a while.

after digging around and trying a few desktop env i settled on gnome 3.6 and liked it a lot. i came across an app called "software" and clicked on (highlighted) the stock gnome browser as i wanted to uninstall it. i clicked in the bottom left where it said "delete". as i lifted my finger off the trackpad, i realized that EVERY APP ON MY MACHINE WAS SELECTED by a blue check box. i panicked and immidiatly held down the power button on my laptop turning it off, hoping to kill it before everything was gone. when i booted back up and logged into gnome and everything was gone. not one single app would show. nothing. so on a whim i logged out and logged into unity and the same thing happened. Whats queer is that when in unity, any app i have docked to the launcher still works without a hitch, making me think everything is still there. if i go to "file system -> usr -> lib" there is still a bunch of stuff in there. 

im lucky enough to still have software center in my launcher dock. but it says all my stuff is installed????? 

one last odd ball that i JUST realized is in unity, when i go to dash home, under the home tab (house icon on the bottom), it says "applications; see 17 more results" but when i go under the applications tab (ruler and pencil on the bottom) it says "Installed; see 114 more results" and its all there.

so how to i get my launchers (gonme and unity) to actually see them? 

ive attached screenshots for your review.

and aren't i supposed to have an "applications" folder under "home" or am i just imagining things?

ive found several old threads from when people updated from 11.10 to 12.04 but those seem to be issues with unity itself. my issue goes across 2 D.E's both unity and Gnome. I think its a file system issue....please help!

Anyone?

---

### Post by rochford77 on 2013-01-24
also, when i access the software center and download something, it is not showing in the home/dash, only in applications/dash...

if that helps...

---

### Post by furything on 2013-01-25
I am wondering if all you have done is hidden the applications from the menus
have a look at 
[http://ubuntu-tutorials.com/2007/07/18/removing-kde-icons-in-gnome-remove-gnome-icons-in-kde/](http://ubuntu-tutorials.com/2007/07/18/removing-kde-icons-in-gnome-remove-gnome-icons-in-kde/)

This is not the one I remember following as mine was much more scripted but have a look and see if your menu is just hiding items. I am guessing unity can be supplemented for kde. Or try googling for unity gnome hide menus and see what comes up.

---

### Post by zombifier25 on 2013-01-25
I think what you did is that you removed the apps' menu entries. Open "alacarte"; is that the all-deleting app you're referring to?
> **rochford77 said:**
> 
one last odd ball that i JUST realized is in unity, when i go to dash home, under the home tab (house icon on the bottom), it says "applications; see 17 more results" but when i go under the applications tab (ruler and pencil on the bottom) it says "Installed; see 114 more results" and its all there.

The "Applications" part on Unity's first page displays the most used applications, so everything is normal.

---

### Post by rochford77 on 2013-01-25
zombi, you sir are on to something. alacarte aka "Main menu" i think is the issue. however, i have somehow hidden that from the menu too (at least in gnome). im in a paradox here. i can pull the app up in unity dash but i click on it and it does not open...

so with the inability to see the app(alacarte) in gnome, and the inability actually open it in unity....what am i to do?

can i open it in the command line in gnome? if so what is the full command? 

or, does anyone know what the app is doing at a file system level? so i can go in and reverse it?

i tried uninstalling the app but stuff was still hidded, so i re installed it.

---

### Post by rochford77 on 2013-01-25
alacarte wont open

ryan@ryan-Aspire-4830T:~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 37, in <module>
    main()
  File "/usr/bin/alacarte", line 33, in main
    app = MainWindow(datadir, version)
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 43, in __init__
    self.editor = MenuEditor()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 31, in __init__
    self.load()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 45, in load
    raise ValueError("can not load menu tree %r" % (self.name,))
ValueError: can not load menu tree 'applications.menu'
ryan@ryan-Aspire-4830T:~$

---

### Post by snowpine on 2013-01-25
Try:

```
sudo apt-get install ubuntu-desktop
```

to restore your Ubuntu system to its default package selection.

---

### Post by rochford77 on 2013-01-25
> **snowpine said:**
> Try:

```
sudo apt-get install ubuntu-desktop
```

to restore your Ubuntu system to its default package selection.

meh, didnt work... 

im just going to do a fresh install. i was thinking about it and...

a) im going to give more drive space to linux and less to windows (i dual boot). i cant think of the last time i used win7 other than to play swtor.

b) since i like gnome more than unity anyway, im going to give fedora a spin...

thanks for the help guys

---

### Post by CharlesA on 2013-01-25
rochford77: I have merged the four posts you made in a row into the original post. In the future, please use the edit button if you need to add more information to the original post.

---

### Post by rochford77 on 2013-01-25
> **CharlesA said:**
> rochford77: I have merged the four posts you made in a row into the original post. In the future, please use the edit button if you need to add more information to the original post.

Thank you for the kind reminder.

And for me, fedora was bunk. It is tough with the combinaiton of no software center *and* diffrent terminal commands. So, back to ubuntu :-)

---

