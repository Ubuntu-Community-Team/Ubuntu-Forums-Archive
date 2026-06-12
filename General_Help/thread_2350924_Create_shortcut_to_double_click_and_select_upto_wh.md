---
title: "Create shortcut to double click and select upto white space"
date: 2017-01-29
forum: General Help
---

### Post by Salil_Surendran on 2017-01-29
Hello,
   I have double click set to select the word between special characters in the gnome terminal. so for eg. consider 'ls -ltr /user/root/folder'. If I double click on root then it will select only root. triple clicking selects the entire line 'ls -ltr /user/root/folder':
[LIST=1]
[*]Is there any way I can configure my system to select the word between whitespaces. so for eg. if I ctrl + double click on root then it should select /user/root/folder.
[*]Is there any way to expand the selection. for eg. I double click and select root and then ctrl + left arrow selects user?
[*]If the above is not possible are there any other terminal apps that allow for Ctrl + selection in the way  I mentioned?
[/LIST]

---

### Post by vanadium on 2017-01-31
Somewhat to my surprise, my terminal on stock Ubuntu 16.04 does exactly what you want: double clicking selects the entire path and not just something between /.../. What Ubuntu/terminal are you using?

---

### Post by Salil_Surendran on 2017-01-31
> **vanadium said:**
> Somewhat to my surprise, my terminal on stock Ubuntu 16.04 does exactly what you want: double clicking selects the entire path and not just something between /.../. What Ubuntu/terminal are you using? You can set up the terminal such that double click selects between certain characters. Use this command

 dconf write /org/gnome/terminal/legacy/profiles:/:<your-gnome-terminal-profile-id>/word-char-exceptions  '@ms "null"'

---

