---
title: "Copying Hidden Files to New Install"
date: 2024-04-23
forum: General Help
---

### Post by Rick St. George on 2024-04-23
After searching, could not find a specific answer to this problem ....

Installed v22.04 Fresh. Now need to copy .thunderbird and .firefox etc. from old drive to new location. 
Used to open file mgr via sudo, but in v22.04 I can't do that as a msg in terminal shows - "not possible due to unfixable security vulnerabilities.

What is a good method to copy these hidden files to my new install?

Thanks!

---

### Post by #&amp;thj^% on 2024-04-23
Mine works with:
```
 sudo cp -r '/home/me/.mozilla' /media/me/114A78974247BEA9/

```

Please change the paths to your needed locations.
```
 cd  /media/me/114A78974247BEA9/ && ls -a | grep .mozilla
.mozilla

```

Please keep in mind though I'm a snap free user. ;)

---

### Post by Rick St. George on 2024-04-23
Thanks fallen ... apparetnly I'm able to do it inside Dolphin - without using Sudo. Prefer the gui method instead of T-command.

Now I am experiencing the same thing inside Dolphin / UbuntuStudio v24.04. 
Is there a Work-around?

I'm trying to move files from one drive to another ... which should be a simple task! Right?

---

