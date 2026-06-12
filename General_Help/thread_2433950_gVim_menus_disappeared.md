---
title: "gVim menus disappeared"
date: 2019-12-28
forum: General Help
---

### Post by engine on 2019-12-28
I'm fairly confident that up till a week or so ago, gVim opened with a menu bar and then a tool bar. Now all I get is the tool bar, just when I wanted the handy reminders and options the menu bar provides. Any [simple, step by hint] hints for getting the menu bar back? fwiw, a reinstall hasn't helped.

---

### Post by spjackson on 2019-12-31
As I understand it, there are 2 possible causes: menus are disabled in gVim settings or the window manager is "showing" the menu bar in some invisible place. For the first case, if you do:
```
:set guioptions
```
it will show you the current settings. You need 'm' in the list. If it's there, then this isn't the problem. If it's not, you can turn it on with:
```
:set guioptions+=m
```
and if that fixes it, add this to ~/.vimrc.

If the problem is the second case of the window manager showing the menu bar in an invisible/invalid place, then the solution may depend on which desktop you are using and which package your installed gVim from. There are some clues [here]("https://vim.fandom.com/wiki/Restore_missing_gvim_menu_bar_under_GNOME").

---

### Post by engine on 2019-12-31
Thanks!
':set guioptions' returns ' aegimLrT' ... I'll try and take a look at the second option.

---

