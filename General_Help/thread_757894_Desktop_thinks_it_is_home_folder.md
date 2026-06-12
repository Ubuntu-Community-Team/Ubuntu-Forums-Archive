---
title: "Desktop thinks it is home folder?"
date: 2008-04-17
forum: General Help
---

### Post by talking Llama on 2008-04-17
Using Ubuntu 7.10 Gutsy and the other day I just booted up and all the items that are in my /home/[user] folder are now displayed on the desktop and my /home/Desktop folder was missing.
So I recreated the Desktop folder by using "sudo mkdir /home/Desktop" so now thats back but its still displaying my home folder on my desktop. Any help?

---

### Post by GCoffee on 2008-04-17
try doing:

sudo mkdir /home/[yourusername]/Desktop

or try:

sudo mkdir /home/[yourusername]/desktop

(Ubuntu has case sensitive directorys as far as I can tell...)

---

### Post by talking Llama on 2008-04-17
Hmm, it's just created those folders but not taken the icons off the desktop... Thanks though...

---

### Post by dje on 2008-04-17
Press Alt + F2 then type:
```
gconf-editor
```
and click OK

When it opens navigate to apps >> nautilus >> preferences and untick 'desktop_is_home_directory'

hope that helps,
dje

---

### Post by talking Llama on 2008-04-17
Thanks, but the box is already unchecked. I thought it might be this as well but it turns out it wasn't. Thanks though.

---

### Post by GCoffee on 2008-04-17
Does the same problem occur on other users?

Try creating a test user...

---

### Post by talking Llama on 2008-04-17
Hey, sorry I didn't try the other user creation. One of my other friends helped me and just for reference if this ever happens to other users here's what I did:
First of all I created a file called "Desktop" in my home user folder eg. /home/[user]/Desktop, then this is what I did afterward:
1.Went to /home/[user]/.config
2. In there I edited the file user-dirs.dirs
3. In there the XDG_DESKTOP_DIR="$HOME/Desktop" was XDG_DESKTOP_DIR="$HOME/" instead so my home folder contents were being displayed on the desktop.
4. I then edited XDG_DESKTOP_DIR="$HOME/" to XDG_DESKTOP_DIR="$HOME/Desktop"

Then made sure this was saved then restarted my computer. AFterwards everything was fine.

Thanks to everyone that tried to help me. :D
But special thanks to Oliver_FF who finally sorted this problem out. Thanks guys.

---

