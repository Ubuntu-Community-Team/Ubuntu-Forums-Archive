---
title: "Password Problem"
date: 2008-05-08
forum: General Help
---

### Post by Akebono on 2008-05-08
I have a problem logging in on Hardy Heron with Gnome. My password is 13 characters in length, but the password field is only allowing me to type in 11 characters. How can I fix this? Thank you.

---

### Post by por100pre1 on 2008-05-08
As a workaround, reboot and use Recovery Mode. There change the password using this command:

```
passwd *your-user-name*
```

type a shorter password (you wont be able to see anything) twice as instructed.

```
reboot
```

Once you log back to Gnome, try using another GDM screen:

```
gksu /usr/sbin/gdmsetup
```

---

### Post by Akebono on 2008-05-08
Thanks very much. That resolved the issue.

---

### Post by cdenley on 2008-05-08
You can type in more than 11 characters, you just can't see more than 11. Every time you type a character, a dot is added for that character. Once the input field is "full", the characters shift to the left to make room. Since all the characters are identical dots, you can't see this happening. Just type your password and it will work.

---

