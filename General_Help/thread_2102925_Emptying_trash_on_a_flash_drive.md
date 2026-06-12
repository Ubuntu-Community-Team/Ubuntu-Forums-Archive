---
title: "Emptying trash on a flash drive"
date: 2013-01-08
forum: General Help
---

### Post by TimmyK. on 2013-01-08
Hiya, does anyone know how to empty the trash on a flash drive? I have an 8 GB drive with 1.1 GB left, even though there are almost no files on it. I know flash drive trash goes into a hidden directory called trash.1000 or something but I have no idea where to find it. And when I do find it, do I need to enter admin mode (gksu nautilus) to delete files? Thanks,

Timmy

---

### Post by sljedi on 2013-01-08
Hey,
You don't have to worry. Just press **ctrl + h** in your file manager (Assuming you're using **Nautilus** or **Thunar** file manager),
Then you can see hidden folders of your drive,
and there is a folder **.Trash-1000**
go to this folder and there will be folder named **files**.
Just **delete** all files in the folder or just deleter the entire **.Trash-1000** folder.

Or if you familiar with the terminal.
Just change the directory to your drive in the terminal,
and run the command rm -rf *
Note:
Don't run this command if you don't know what it's mean.
Cheers...!

---

### Post by sudodus on 2013-01-08
You should find the trashcans of your mounted devices with the following command

```
sudo find / -name ".Trash*"
```

But if you have many files, you might go more directly to the target. If the flash drive is auto-mounted, probably you'll find it with the following command, which is much faster:

```
sudo ls /media/*/.Trash*
```

And when you have found it you can delete the files within its subdirecories using the command you suggested ```
gksu Nautilus
``` with the setting to see hidden files, as suggested by sljedi.

---

### Post by TimmyK. on 2013-01-08
OK, I deleted the folder, but it still says I have only 1.2 free GB.

---

### Post by Calinou on 2013-01-08
> **sljedi said:**
> 
Or if you familiar with the terminal.
Just change the directory to your drive in the terminal,
and run the command rm -rf *
Note:
Don't run this command if you don't know what it's mean.
Cheers...!

...why not use rm -rf .Trash-1000 instead of deleting everything on your system if you do a mistake?

---

### Post by TimmyK. on 2013-01-08
Only problem is, I've already deleted the .Trash-1000 folder, and it freed up no space at all.

---

### Post by John.Klockenkemper on 2013-01-08
If the flash drive is basically empty anyway, You can always reformat the device to clear the space.

---

### Post by sudodus on 2013-01-08
Maybe it is now in root's trashcan (if you used gksu Nautilus).

Try this, which should definitely free up your drive space
```
cd /media/name-of-your-flash-partition
```
with the actual name of your flash partition and then
```
sudo rm -r .Trash*/*
```

---

### Post by TimmyK. on 2013-01-08
Thanks, although it turns out I actually did have a very large file that was taking up a lot of room but didn't show up for some reason. Thanks everyone!

---

