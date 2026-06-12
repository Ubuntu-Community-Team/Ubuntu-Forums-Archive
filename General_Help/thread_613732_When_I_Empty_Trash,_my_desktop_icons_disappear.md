---
title: "When I Empty Trash, my desktop icons disappear"
date: 2007-11-15
forum: General Help
---

### Post by azad on 2007-11-15
Hi,
My 6 year old niece somehow deleted the Desktop folder from /home

I came home and saw my Trash full so I clicked on Empty Trash. Then I found out that all the icons and files i had in Desktop disappeared. So I created all the icons again. Once again when I cleared my Trash, the icons disappear.

Here's what I found out later: See the screenshot.

The Desktop folder lies in Trash and when I clear Trash, all my icons disappear.

How can I restore my Desktop back to /home ?

Thanks in advance.
Azad

---

### Post by shad0w_walker on 2007-11-15
Have you tried just creating a folder in your home directory called Desktop?

---

### Post by azad on 2007-11-15
I did. But still when I create a file in Desktop, it is created in /home/username/.Trash/Desktop instead of /home/username/Desktop

What to do?

---

### Post by azad on 2007-11-17
bump bump. Anyone?

---

### Post by FuturePilot on 2007-11-17
Have you tried moving the Desktop folder out of the Trash back into your home folder?

---

### Post by rsambuca on 2007-11-17
What about renaming the Desktop in your trash to something else, and then creating a folder called Desktop in your /home/yourusername/

---

### Post by bettermentflux on 2007-12-05
Not sure if you ever found a fix, but I found the problem was with a file found here: **/home/username/.config/user-dirs.dirs**

Edit it and I think you'll find that the desktop is currently pointed to .trash.

Hope this helps.

---

