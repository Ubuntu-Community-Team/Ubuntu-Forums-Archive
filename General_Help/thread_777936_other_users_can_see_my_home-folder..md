---
title: "other users can see my home-folder."
date: 2008-05-01
forum: General Help
---

### Post by jakupl on 2008-05-01
Hi. I have an other user on my computer. I am the only one with administrative rights.

I want to make it so the other user can't see my files in my home folder... maybe even preventing him to enter my home folder in the first place, if that is possible?

I thought that I should ask here before doing anything stupid. You need to know what you're doing, before tinkering with permissions.

thanks in advance :)

---

### Post by damis648 on 2008-05-01
Try going to /home then right click your home and goto properties and choose the permissions tab. Under "group" and "others" (the last two sections), set folder access to none. DO NOT CHANGE THE TOP "OWNER" SECTION!

and thats it :)

---

### Post by jakupl on 2008-05-01
uuuh i am so stupid!!! I actually knew that myself, but never thought about it :lolflag: well thankyou very much:popcorn:

---

### Post by sisco311 on 2008-05-01
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

change the permissions of your home folder to 0750 (rwxr-x---)
owner : read, write, execute
group : read, execute
                                 others: nothing

```
chmod 750 $HOME
```

---

### Post by damis648 on 2008-05-01
lol welcome

---

### Post by jakupl on 2008-05-01
noo hahahaha I am not new here :)
Just incredibly stupid at times.

---

### Post by damis648 on 2008-05-01
ha ok :)

---

