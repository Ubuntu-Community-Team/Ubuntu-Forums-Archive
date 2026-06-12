---
title: "Do'h! Permissions locked me out"
date: 2008-05-15
forum: General Help
---

### Post by remmyshroomo on 2008-05-15
Hello everyone,
I have been using Ubuntu for quite sometime now and haven't really had too many issues that I couldn't figure out until now...

I foolishly changed a directory permission when logged into root but the user group I gave permissions to didn't have any users in it. Now, when I boot up I encounter a whole bunch of error messages saying "user does not have permissions to ....".

The pain is that I have my user set to auto login.

I was wondering what would I have to do to stop it from auto login, so I then could log back into root to reverse the permissions?

Like some kind of command in the console when trying to do a safe boot?

If it matters, I am running Hardy Heron on an AMD 64.

Now if you excuse me, I'm off to bash my head against the wall for doing such a novice mistake.

Thanks,
Ryan

---

### Post by damis648 on 2008-05-15
Start up in recovery mode and select root shell. In the shell, just type
```
startx
```
and fix it from there ;).

---

