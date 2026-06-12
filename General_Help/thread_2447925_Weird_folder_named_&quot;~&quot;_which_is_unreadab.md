---
title: "Weird folder named &quot;~&quot; which is unreadable and empty in home"
date: 2020-07-29
forum: General Help
---

### Post by holytree2 on 2020-07-29
Hi,

I am on Ubuntu 18.04, have been for a while. In the home directory, there is a new directory which is created repeatedly, its unreadable and I'm not sure what its doing.

It looks as shown in the screenshot.

[ATTACH=CONFIG]286574[/ATTACH]

Not 100% sure this is the right place to post this, but was curious if I needed to be concerned as I haven't seen this before.

Thank you!

---

### Post by Impavidus on 2020-07-29
Let's find out a bit more about this directory. In the terminal, try this:```
ls -l *~*
```I use the * just in case there are leading or trailing spaces, so this will print details about all files and directories with ~ in their name. ~ is used by bash as shorthand for $HOME, your home directory, and many applications add a leading or trailing ~ to filenames when they create a backup.

---

### Post by ActionParsnip on 2020-07-29
What is the output of:
```

ls $HOME

```
Thanks

---

### Post by kneutron on 2020-07-31
--It sounds like maybe a badly-coded script is running and instead of creating a proper file in your /home directory the programmer used '~' incorrectly.  You should be able to delete it safely with Midnight Commander ('mc' package.)

See also:
[https://serverfault.com/questions/565914/remove-corrupt-file-with-bad-file-name-linux](https://serverfault.com/questions/565914/remove-corrupt-file-with-bad-file-name-linux)

---

