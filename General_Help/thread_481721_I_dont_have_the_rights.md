---
title: "I dont have the rights?"
date: 2007-06-22
forum: General Help
---

### Post by The Wisedude on 2007-06-22
When I'm trying to put a new skin in the aMSN folder, (usr/share/amsn/skins)

It says I'm not allowed?

And Im the administrator of the computer..

So whats up? How can I bypass this or use the terminal to move the skin I want to put in the folder?

---

### Post by Bachstelze on 2007-06-22
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by trak87 on 2007-06-22
When you are copying files to a location outside your home directory you will need to prepend your commands with 'sudo' to gain root privileges.

```
sudo cp myfiles /usr/share/amsn/skins
```

---

### Post by The Wisedude on 2007-06-22
Both of that didn't work :(

@(link): I'm already admin, Im the first account made on my home computer's OS. ..

---

### Post by NeoLithium on 2007-06-22
Did it give you an error message?  When you're in a terminal window, you have to make sure that you CD to the directory where the files you want to move are stored, or simply let linux know where to move from. IE, if you saved it on your Desktop, as in downloading with firefox:

sudo cp /home/USERNAME/Desktop/filename /usr/share/amsn/skins

OR, CD to that directory
cd /home/USERNAME/Desktop
sudo cp filename /usr/share/amsn/skins

---

### Post by The Wisedude on 2007-06-22
> **NeoLithium said:**
> Did it give you an error message?  When you're in a terminal window, you have to make sure that you CD to the directory where the files you want to move are stored, or simply let linux know where to move from. IE, if you saved it on your Desktop, as in downloading with firefox:

sudo cp /home/USERNAME/Desktop/filename /usr/share/amsn/skins

OR, CD to that directory
cd /home/USERNAME/Desktop
sudo cp filename /usr/share/amsn/skins

Thanks :)

---

### Post by NeoLithium on 2007-06-22
You're very welcome :)

---

