---
title: "Application Menu - shortcuts missing"
date: 2008-06-05
forum: General Help
---

### Post by hughstephens on 2008-06-05
Hello
I recently updated my (linux mint) install of ubuntu to hardy heron.
Now I have no icons in my main menu, although I can see them all in alacarte.
I have tried several things...
1. copying the contents of /etc/xdg/applications.menu to ~/.config/menus/applications.menu
2. deleting the ~/.config/menus/applications.menu file using root shell access and then restarting
3. setting the ~/.config/menus/applications.menu file to the 'right' settings according to [here]("http://ubuntuforums.org/showthread.php?t=815172")
4. creating a new user - no help. other user also has no icons :-( according to [here]("http://ubuntuforums.org/showthread.php?t=432912")
5. several terminal instructions:
```
sudo update-desktop-database
```
and also something else that involved installing a couple of packages then running 'update-menus' (can't find the link)

so yeah. thats what I've tried so far, and if I manage to find something that works then ill post :)
thanks
hughstephens

---

### Post by rune0077 on 2008-06-05
What happens if you try to add a new item manually? Right-click the menu, select "Edit Menus" and try adding a new one. Does it show up?

---

