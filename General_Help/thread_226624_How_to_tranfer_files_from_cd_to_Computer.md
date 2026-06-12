---
title: "How to tranfer files from cd to Computer"
date: 2006-07-31
forum: General Help
---

### Post by Roflcopterrr on 2006-07-31
How can I transfer folders from a cd to my htdocs folder?

(XAMPP)

---

### Post by T700 on 2006-07-31
Insert the CD into the CD drive.  Open your file browser (likely Nautilus).  Open the CD with the file browser.  Highlight and copy the files.  Using the file browser, open the directory where you wish to put them.  Paste.

That's one way.  There are many others.  Are you having trouble making it work?

Paul

---

### Post by FenrisAbraxas on 2006-07-31
> **T700 said:**
> Insert the CD into the CD drive.  Open your file browser (likely Nautilus).  Open the CD with the file browser.  Highlight and copy the files.  Using the file browser, open the directory where you wish to put them.  Paste.

That's one way.  There are many others.  Are you having trouble making it work?

Paul

```
 mount /mnt/cdrom
cp -r /mnt/cdrom /var/www/http/htdocs /*or something like that*/

```

---

### Post by Roflcopterrr on 2006-07-31
But for some reason, there is a picture of a Lock next to the picture of the folder :(

---

### Post by Metacarpal on 2006-07-31
Here's how to fix that:

Open a terminal (Applications menu > Accessories > Terminal) and type:

```
sudo nautilus
```

(Assuming that you're in Gnome)

Give it your password when prompted.  Then use the copy of Nautilus that opens up to navigate to the htdocs folder.  It should be unlocked.

(NOTE: Don't close the Terminal until you're done copying the files.  When you close Terminal, it'll take the su-enabled Nautilus window with it.)

---

### Post by Roflcopterrr on 2006-07-31
I'm using Xubuntu, and it says command not found for nautilus.

---

### Post by Metacarpal on 2006-07-31
> **Roflcopterrr said:**
> I'm using Xubuntu, and it says command not found for nautilus.

Try ```
sudo thunar
```

---

### Post by T700 on 2006-07-31
Just a gentle suggestion to the original poster:  You will get much better answers if you provide more information.  Had you mentioned the lock symbol next to the files and that you were using Xubuntu, a lot of back and forth would have been saved.

Not trying to be harsh to you.  Just a way to help you get better help!

Paul

---

