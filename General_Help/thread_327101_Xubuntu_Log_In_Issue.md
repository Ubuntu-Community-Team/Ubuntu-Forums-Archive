---
title: "Xubuntu Log In Issue"
date: 2006-12-28
forum: General Help
---

### Post by gfaux on 2006-12-28
Hi,

I have Xubuntu installed on a Compaq Armada 100s laptop for a friend. Somehow they have buggered it up so that on logging in you don't see a desktop, just a blank screen. Upon log in (after entering username and password in login screen), the splash screen for AbiWord shows and then nothing, just the blank screen. I can get a terminal window up, but am not sure where to go from there. I think AbiWord is set to run on startup but I have no way to tell.

Can anyone advise how to list startup programs / edit startup configuration files just using console commands /  editors.  X seems to start, as I can type the names of programs to run (such as mousepad, abiword etc), but no Desktop menus, windows managers etc.

Thanks in advance

---

### Post by kerry_s on 2006-12-28
You can try resetting it to stock.

in terminal->
rm -rf ~/.config
ctrl + alt + backspace

or

alt + F2
type thunar
view>show hidden files> delete ".config "
ctrl + alt + backspace

edit: I forgot in xubutu, you also need to delete the ".cache" folder to.

---

