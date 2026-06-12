---
title: "Ubuntu Auto Load"
date: 2008-07-01
forum: General Help
---

### Post by lenswipe on 2008-07-01
Im trying to make a file automatically load when a user logs on. Or better still get a message box to apear displaying an AUP. Also does anyone know how i can make the AUP readable in the users home directory but not deleteable or writable?


Any ideas?

---

### Post by ryanhaigh on 2008-07-01
How about a simple zenity dialog:

```

zenity --info --text "Don't mess with stuff your not supposed to!"

```

Just use this for a session startup command (system>preferences>sessions). How you would add this to all users sessions I am not sure.

If the AUP is going to be long or change often you could use:
```
cat /root/AUP.txt | zenity --text-info --width 530
```

Once you have created the AUP file you can right click on it to change permissions and allow only the owner to write/modify it. The location /root/AUP is just an example you could have it in your own home directory as long as all users can read it (again right click > properties > permissions).

---

### Post by dcstar on 2008-07-02
> **lenswipe said:**
> Im trying to make a file automatically load when a user logs on. Or better still get a message box to apear displaying an AUP. Also does anyone know how i can make the AUP readable in the users home directory but not deleteable or writable?


Any ideas?

xmotd

---

