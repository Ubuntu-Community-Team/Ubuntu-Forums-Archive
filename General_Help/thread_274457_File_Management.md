---
title: "File Management"
date: 2006-10-09
forum: General Help
---

### Post by dontgetshocked on 2006-10-09
I cant seem to move my files from one folder to another, the paste command is grayed out.What can I do  to correct this? Also, how do I open a terminal so I can install my software? Open the terminal with the folder that I wish as the active folder?

---

### Post by bswilson on 2006-10-09
> **dontgetshocked said:**
> I cant seem to move my files from one folder to another, the paste command is grayed out.

Maybe you can clarify where you're trying to move files?  You may simply not have the proper permissions, which would be by design...

---

### Post by dontgetshocked on 2006-10-10
I believe I have admin privileges which i setup thru users and groups with my name in the root group.Move files from the My Documents folder to the user/share/sounds folder.

---

### Post by nikhilk on 2006-10-10
If you are using Kubuntu you can open a terminal from:
Main menu(KMenu)->System->Terminal

What error message(s) (if any) do you get if you attempt to copy the files using the terminal?

---

### Post by ProjectGod on 2006-10-10
use the terminal with root privy to move them. i'm not too fond of adding users into the root's group.

---

### Post by epennings on 2006-10-10
The Terminal is located under Applications>Accessories>Terminal

By default you can only write files in your user folder (/home/yourname)
Most other folders, including those the /usr folder, require root access

If you really want to cut and paste some files there you could type this in a  terminal :

```
sudo nautilus 
```

This will open a filebrowser with root access. You have full access to all files and folders, including important system files, so be carefull ;)

---

