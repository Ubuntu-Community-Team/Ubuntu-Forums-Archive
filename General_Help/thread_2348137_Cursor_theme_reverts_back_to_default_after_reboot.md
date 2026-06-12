---
title: "Cursor theme reverts back to default after reboot"
date: 2017-01-01
forum: General Help
---

### Post by ardouronerous on 2017-01-01
I'm running Xubuntu 16.04.

I've downloaded a cursor theme and I placed the contents in '/home/username/.icons/'.
However, after rebooting or restarting, the cursor theme reverts back to default.

How to fix?

---

### Post by Dennis N on 2017-01-01
After rebooting or restarting, does the new cursor theme show up in some places (like inside application windows, over the panel, or desktop) but not others? Or does it not appear at all?

---

### Post by ardouronerous on 2017-01-01
When I first installed the cursor theme, COMODO Antivirus doesn't recognize the new cursor, it reverts back to default whenever I visit COMODO's application window or hover my mouse over it's icon on the tray.

After rebooting or restarting, COMODO Antivirus, when I get into COMODO's application window, the new cursor theme shows up, but the rest of the system it doesn't, reverting back to default.

---

### Post by ardouronerous on 2017-01-02
Bump

---

### Post by Dennis N on 2017-01-03
Please check the contents of the new cursor's folder. Does it contain a file named **cursor.theme**?

If so, you can probably make the new cursor appear everywhere by following all the instructions in the old post linked below, except in the first command, substitute the exact name on the new cursor's folder for Pulse-Glass, and then if using Xubuntu, in the final step select your new cursor theme in Settings > Mouse and Touchpad > Theme. 
 
Log out and then log back in and see if things are better.

[https://ubuntuforums.org/showthread.php?t=2234783&p=13075327#post13075327](https://ubuntuforums.org/showthread.php?t=2234783&p=13075327#post13075327)

---

### Post by ardouronerous on 2017-01-04
Unfortunately it doesn't, it has a index.theme file, can your method work with index.theme files instead of cursor.theme?

---

### Post by vasa1 on 2017-01-04
> **ardouronerous said:**
> Unfortunately it doesn't, it has a index.theme file, can your method work with index.theme files instead of cursor.theme?

For some reason, you haven't provided information about the theme! Why?

---

### Post by ardouronerous on 2017-01-04
> **vasa1 said:**
> For some reason, you haven't provided information about the theme! Why?

I didn't feel the need to.

It's the Breeze cursor theme.

---

### Post by Dennis N on 2017-01-04
> **ardouronerous said:**
> Unfortunately it doesn't, it has a index.theme file, can your method work with index.theme files instead of cursor.theme?

You just have to create the cursor.theme file yourself. I use the Breeze-White cursor theme - create this as a text file named **cursor.theme** and place it inside the cursor folder (change name of cursor to yours):

```
[Icon Theme]
Inherits=Breeze-White

```

Additional fix needed:
This cursor theme has an adjustable size. I know with Xubuntu, this size causes an additional problem in that when I restart or reboot, the cursor reverts to the smaller default size after log in (it will always be small on the log in screen). My solution was to create a text file **.Xresources** containing the line:

```
Xcursor.size: 40
```

This makes a 40 pixel cursor, or use one of the other allowable sizes for that cursor theme, and place the file in your home folder. That fixed the size problem. Of course, if you like the small default size, you don't need to do this.

---

### Post by ardouronerous on 2017-01-04
Thanks Dennis, it worked! :)

---

