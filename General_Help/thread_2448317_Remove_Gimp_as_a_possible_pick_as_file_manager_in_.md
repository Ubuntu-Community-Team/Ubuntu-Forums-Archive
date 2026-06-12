---
title: "Remove Gimp as a possible pick as file manager in Preferred Applications"
date: 2020-08-05
forum: General Help
---

### Post by raleigh3 on 2020-08-05
Is there a way to remove Gimp as a possible pick as file manager in Preferred Applications?

I am using Ubuntu Mate 18.04.

[ATTACH=CONFIG]286625[/ATTACH]

---

### Post by Dennis N on 2020-08-05
Step 1: Post the output of:
```
cat /usr/share/applications/gimp.desktop | grep -i inode
```

---

### Post by ajgreeny on 2020-08-05
I thought this problem had been solved in your thread [https://ubuntuforums.org/showthread.php?t=2447977&highlight=gimp](https://ubuntuforums.org/showthread.php?t=2447977&highlight=gimp)

Are you asking something different here as it seems similar to me?
Do you still actually have a problem, or is this simply a question about the possible choices when choosing a file-manager?

It may help if you run command ```
cat .config/mimeapps.list | grep gimp
``` which will show all the info for your user related to the mime references in that mime file for potential uses of gimp.

---

### Post by raleigh3 on 2020-08-05
> **Dennis N said:**
> Step 1: Post the output of:
```
cat /usr/share/applications/gimp.desktop | grep -i inode
```

There is no output.

---

### Post by raleigh3 on 2020-08-05
[QUOTE=ajgreeny;13977477]I thought this problem had been solved in your thread [https://ubuntuforums.org/showthread.php?t=2447977&highlight=gimp](https://ubuntuforums.org/showthread.php?t=2447977&highlight=gimp)

Are you asking something different here as it seems similar to me?
Do you still actually have a problem, or is this simply a question about the possible choices when choosing a file-manager?

Gimp should not be listed as a choice as it's not a file manager.

---

### Post by Dennis N on 2020-08-06
> **raleigh3 said:**
> There is no output.

If you have no output to the command, then Gimp must be listed in the file ajgreeny named. Look for:
```
inode/directory=gimp.desktop
```
and remove it.

If inode/directory DID appear in the output, then you need to use a different procedure.
.

---

### Post by raleigh3 on 2020-08-07
```
bash: inode/directory=gimp.desktop: No such file or directory
```

---

### Post by ajgreeny on 2020-08-07
Have you run the command I suggested in post #3 ```
cat .config/mimeapps.list | grep gimp
```
If not do so now and let's see the output of that; it may give us a clue what has allowed gimp to be included in that listing.

---

### Post by Dennis N on 2020-08-07
> **raleigh3 said:**
> ```
bash: inode/directory=gimp.desktop: No such file or directory
```

This looks like some terminal output. What command gave you this result?

---

### Post by raleigh3 on 2020-08-07
inode/directory=gimp.desktop

---

### Post by ajgreeny on 2020-08-07
> **Dennis N said:**
> This looks like some terminal output. What command gave you this result?
I think raleigh3 used that as a terminal command, which needless to say, can't find a file or folder by that name.

@ raleigh3
You were meant to look in the file I showed in post #3 **~/.config/mimeapps.list** and see if it contained that line of text; it was not intended to be a command so please do what we are suggesting; read carefully and to avoid typo mistakes, use copy/paste.

---

### Post by Dennis N on 2020-08-07
> **raleigh3 said:**
> inode/directory=gimp.desktop
Like this?
```
dmn@Tyana-vm:~$ inode/directory
bash: inode/directory: No such file or directory

```If so, it's not a valid command. I'm not sure how bash understands it.

What you need to do is open the file (see post #11) in a text editor, copy all  contents and post it between code tags in order to get recommendations on how to proceed.

---

### Post by raleigh3 on 2020-08-08
I did what you asked and got this.

```
image/jpeg=userapp-gimp-FN7PN0.desktop;eom.desktop;gimp.desktop;org.kde.kolourpaint.desktop;
image/png=userapp-gimp-FN7PN0.desktop;eom.desktop;org.kde.kolourpaint.desktop;gimp.desktop;
image/x-xcf=gimp.desktop;
inode/directory=caja-folder-handler.desktop;gimp.desktop;
image/tiff=userapp-gimp-FN7PN0.desktop;
image/png=userapp-gimp-FN7PN0.desktop
image/bmp=userapp-gimp-FN7PN0.desktop
image/gif=userapp-gimp-FN7PN0.desktop
image/jpeg=userapp-gimp-FN7PN0.desktop
image/tiff=userapp-gimp-FN7PN0.desktop
```

---

### Post by Dennis N on 2020-08-08
> **raleigh3 said:**
> I did what you asked and got this.

```
image/jpeg=userapp-gimp-FN7PN0.desktop;eom.desktop;gimp.desktop;org.kde.kolourpaint.desktop;
image/png=userapp-gimp-FN7PN0.desktop;eom.desktop;org.kde.kolourpaint.desktop;gimp.desktop;
image/x-xcf=gimp.desktop;
inode/directory=caja-folder-handler.desktop;[COLOR="#FF0000"]**gimp.desktop**;[/COLOR]
image/tiff=userapp-gimp-FN7PN0.desktop;
image/png=userapp-gimp-FN7PN0.desktop
image/bmp=userapp-gimp-FN7PN0.desktop
image/gif=userapp-gimp-FN7PN0.desktop
image/jpeg=userapp-gimp-FN7PN0.desktop
image/tiff=userapp-gimp-FN7PN0.desktop
```

And there it is (in red). Just open this file in text editor, delete the text in red, save the file, and Gimp should be removed from the Preferred Applications for File Manager.

This may require log out and log back or in, or rebooting, to take effect.

---

### Post by raleigh3 on 2020-08-09
Perfect.

Thanks.

---

### Post by ajgreeny on 2020-08-09
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

