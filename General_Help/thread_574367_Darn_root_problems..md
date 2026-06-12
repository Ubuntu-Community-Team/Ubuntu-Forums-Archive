---
title: "Darn root problems."
date: 2007-10-12
forum: General Help
---

### Post by jiminy82 on 2007-10-12
How can I make it so that I can extract files to my file system? It won't let me. It says I don't have permission. I am assuming I need to be root, but I can't become root. The only time I can ever do anything is if I use sudo in console. Unfortunately I am trying to extract a metacity theme file and it is a graphic interface. 

How can I turn this off, I am tired of putting in my password for everything. 

Thanks.

---

### Post by bodhi.zazen on 2007-10-12
To become root, 

```
sudo -i
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

to sudo without a password, see man sudoers

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

### Post by dfreer on 2007-10-12
I'm thinking metacity themes can simply be added in System > Preferences > Themes (or Appearance if you are using Gutsy), without needing to extract it first. Of course, I could be wrong, it's been a long time since I've used a metacity theme.

If you can't extract the theme to your desktop/home folder, than you have a permissions issue. You can also launch the graphical tool to extract files as the super user like so:
```
sudo file-roller
```

---

### Post by jiminy82 on 2007-10-13
thanks for the help guys, but I guess I am just going to try an reinstall and only create a root. Just too much of a pain.

---

