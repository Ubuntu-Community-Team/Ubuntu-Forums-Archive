---
title: "Where am I suppose to store files I want all users to have access to?"
date: 2007-09-24
forum: General Help
---

### Post by prophet665 on 2007-09-24
I want to store my MP3 and JPG files and have them accessible to all users.  Which folder are they suppose to be stored in?  

Do I create a folder called /usr/share/MP3 and /usr/share/Pictures?

Does it even need to be said that I am new to Linux?

---

### Post by reckless2k2 on 2007-09-24
you can really share them where ever you want. that's the beauty of linux.

---

### Post by louieb on 2007-09-24
As far as I know there is no designated place for shared files. What i did is create a folder /stuff  and anything I want to share goes in there. I  made mine the mount point to the second drive. But you don't have to do that. Just create a folder, use chmod and give it 777 permissions and share away. Probably you will want to look at the type of linux permissions and ownership rules. primarily the chown and chmod commands.

---

