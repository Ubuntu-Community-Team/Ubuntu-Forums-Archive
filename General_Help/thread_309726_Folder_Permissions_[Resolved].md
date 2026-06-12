---
title: "Folder Permissions [Resolved]"
date: 2006-11-30
forum: General Help
---

### Post by Vord on 2006-11-30
So, I won't go into what I did to need to delete a directory, let's just say that I do. I created the directory while logged in as root, and I need to change the permission to make it to where I can delete the directory. Help?

---

### Post by aysiu on 2006-11-30
This should help:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Vord on 2006-11-30
well, the folder I need to modify (See: Delete) is ~/.wine, I'm reading an explination of chmod, saying use chmod 667 to allow read, write, and execute permissions, my only problem is, I have no idea how to make that work.

---

### Post by aysiu on 2006-11-30
You want to delete ~/.wine?

Just paste this command into the terminal (paste it--do not retype it): ```
sudo rm -r ~/.wine
``` In the future, there's no need to log in as root. Read the link I posted above.

---

### Post by Vord on 2006-11-30
Thank you so much, and I know there was no need to log in as root, I had done it earlier for some reason. I'm quite new to Ubuntu and I'm working with a friend of mine, he had me do it earlier tonight. That fixed it, thanks again :D

---

