---
title: "Change default normal mouse pointer size."
date: 2016-03-04
forum: General Help
---

### Post by Robert_Gaines on 2016-03-04
I'm using Cinnamon so I don't know if this is a global problem or not. I have Ubuntu 15.10. I can't get the default normal mouse pointer to change from anything other than 22 pixels square in the desktop enviroment. This only effects the specific cursor that is used normally to click on icons and folders in the Desktop enviroment. The other cursors for size, etc. do change in size. Applications like Firefox use the pointer size I have selected for all the cursors, but the normal cursor in the desktop enviromnent stays at 22 pixels square no matter what. I've even made the normal cursor itself physically bigger, but when used on the desktop environment it stays at 22 pixels square. I've used various command line utilities and configuration editors that change the theme everywhere and the size for the mouse cursors everywhere. You can see the changes in Firefox, but the size of the normal cursor used in the desktop environment remains fixed at 22 pixels. I use a 1080 desktop so the 22 pixel cursor is a little tiny, but it's only size it will use for the normal cursor. The other cursors change in size, but the normal cursor remains the same. Do you understand my problem? Is there a solution to my problem? It could be a bug in Cinnamon because even though it's a really popular desktop environment, the developers in Cinnamon are not concerned with fixing various bugs in the enviroment like the mount/dismount bug that corrupts the desktop when you insert or remove media, and you have to logout and back in as the only effective solution. I love using it because it is simple and straight foward, but I hate the bugs.

---

### Post by jim_deadlock on 2016-03-04
When I update my cursor theme I have to do it in 2 places:

```
sudo update-alternatives --config x-cursor-theme
```

...and Tweak Tool > Appearance > Cursor

If I don't do both then I get the type of behaviour you're describing. If you still have the same problem after this, then it might be an issue with the cursor theme itself, if so try a different theme to see if that's the problem.

---

### Post by Dennis N on 2016-03-04
1) In Ubuntu, the system default is DMZ-White and it supports three sizes: 24, 32, and 48 px. What is the name of your default cursor theme?

2) Not all cursors support changing the size. you may be using one of those.  The default cursor can be changed in Debian-based systems as suggested in post #2, but that method does not specify the size - you get the smallest. I believe size selection (when the cursor supports it) is made possible by the desktop environment. For example, Lubuntu with LXDE does not support changing the size, while Xubuntu with XFCE does. I don't know about the Cinnamon desktop.

---

