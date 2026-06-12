---
title: "add user - new users can see other users' folders"
date: 2007-11-11
forum: General Help
---

### Post by im7766 on 2007-11-11
Just added a new user with few permisisons ("guest").
Logging in as guest I can still see/browse my original user's home folder.

Is this normal behaviour? It's not what I expected.

(on Gutsy clean install)

---

### Post by Dwood108 on 2007-11-11
You have to set the file permissions for your home folder.

Login as your self and right click on your home folder, select 'properties' then the 'permissions' tab, set the permissions for 'group' and 'other' to 'none' (or whatever you want.

Once you have done this no-one else should be able to access your home folder.

PS you do not have to set the permissions for all the files and sub-folders i.e Apply Recursively.

---

### Post by im7766 on 2007-11-11
Thanks Dwood, I'll give it a try.

Kinda suprised that add user doesn't do this by default - I suspect this will catch out anyone switching to Ubuntu from Windows.

---

### Post by olejorgen on 2007-11-11
I think you need to set it for all files and folders to be completely sure.
```

drwxr-xr-x  2 me  me  4.0K 2007-10-22 12:47 /home/me/isus
drwxr-x--x 147 me     me     8.0K 2007-11-11 14:11 /home/me

```
ls /home/ole will fail, but ls /home/ole/isus will work

---

