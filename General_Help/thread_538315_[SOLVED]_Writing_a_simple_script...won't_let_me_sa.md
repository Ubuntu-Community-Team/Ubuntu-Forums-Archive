---
title: "[SOLVED] Writing a simple script...won't let me save."
date: 2007-08-29
forum: General Help
---

### Post by ArtF10 on 2007-08-29
Hello, I;m trying to write a script using a text editor.  When I enter the relevant text and try to save, it says that I do not have permission.  Here's the part of the article I'm tryuing to follow:

> A couple of utilities exist that preload OpenOffice.org. One, called Quickstarter or oooqs, exists for KDE; another, called ooqstart-gnome, exists for GNOME. We have not seen new development on the later utility, though, and it often causes an error message.

You also can use a built-in program called ooffice -quickstart, which you can start manually from the command line. The command is

$ ooffice -quickstart &

To use it, start ooffice -quickstart manually or have it launched automatically when you start your window manager or desktop. You then can start up your word processor, for example, work and then close the applications. But as soon as you close OpenOffice.org, the background quickstart process automatically dies.

The scripts used by oooqs and ooqstart-gnome do not experience this problem. So, you may want to use a script modified from Linux Desktop Hacks, published by O'Reilly & Associates. With this method we create a script and place it in a file called /usr/local/bin/oostay. The script looks like this:

```
#!/bin/bash
# Restart ooffice -quickstart every time it exits
instances=`ps ax | grep -e -quickstart | grep -v grep | wc -l`
if [ $instances == 0 ]; then
while true; do ooffice -quickstart ; done
    else
    exit 1
fi
```
Then, after creating it, make it executable with the following command:
```
# chmod +x /usr/local/bin/oostay
```

1.  How do I go about placing this text in a text editor and saving it?

2.  I don;t want to use quickstart.  IS this needed for the script to work?

---

### Post by aysiu on 2007-08-29
/usr/local/bin is a system directory.

Ordinarily, you'd launch the text editor this way to be able to save the file to a system folder: ```
gksudo gedit /usr/local/bin/oostay
``` Since you already have the text editor open, save it to your desktop. Then press Alt-F2 and type ```
gksudo nautilus
``` This will open the file browser with administrative privileges. Navigate to /usr/local/bin. Then move the oostay file from your desktop to /usr/local/bin. Right-click on it, and go to properties, and make sure it's marked as being executable.

---

### Post by ArtF10 on 2007-08-29
Thanks, that helps.

---

### Post by ArtF10 on 2007-08-30
Any ideas about my second question?

---

### Post by aysiu on 2007-08-30
Isn't the whole point of the script to use quickstart?

If you don't want quickstart, don't use the script... as far as I can tell.

---

### Post by ArtF10 on 2007-08-30
I think I was reading it wrong...I thought it was quickstart OR script.  I see now that I would need both.

---

