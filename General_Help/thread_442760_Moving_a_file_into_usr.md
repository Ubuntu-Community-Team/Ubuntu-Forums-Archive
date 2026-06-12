---
title: "Moving a file into /usr"
date: 2007-05-13
forum: General Help
---

### Post by OsakaWilson on 2007-05-13
I am using KDE World Clock in Ubuntu Feisty. I want to change the map, but this requires putting the new map image into usr/share/apps/worldclocks/maps/. When I try to drop them directly into the file, I get "You do not have permissions to write to this folder."

How do you move a file into this folder?

---

### Post by taurus on 2007-05-13
Open a terminal and run

```
sudo cp filename /usr/share/apps/worldclocks/maps
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by OsakaWilson on 2007-05-13
I did that, but got this message.

cp: cannot stat `bio_2400.jpg': No such file or directory

I definitely have a file called bio_2400.jpg.

---

### Post by taurus on 2007-05-13
Are you sure you're in the right directory?  What's the output of this command from a terminal then?

```
ls -la
```

---

### Post by OsakaWilson on 2007-05-13
I'm quite sure I have no idea what directory I'm in.

I ran the command you gave me, but the folder contents give too much private information about my work to list  publicly. Is there any other way we can establish which directory I'm in?

---

### Post by OsakaWilson on 2007-05-13
Do I need to be in the directory of the file that I want to move?

---

### Post by taurus on 2007-05-13
> **OsakaWilson said:**
> Do I need to be in the directory of the file that I want to move?

Yes, or you need to include the full path.  So you know exactly where that file is?  If you don't, you can search for it with

```
find ~ -name bio_2400.jpg -print
```
Otherwise, just start nautilus with root permission and drag 'n drop it to where you want it to.

```
gksudo nautilus
```

---

### Post by OsakaWilson on 2007-05-13
The gksudo nautilus did it. That was easy. 

Once again, I avoid learning how to really use the command line. Hehe. 

Thank you very much for helping with this.

---

