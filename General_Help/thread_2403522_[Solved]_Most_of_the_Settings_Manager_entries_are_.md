---
title: "[Solved] Most of the Settings Manager entries are gone"
date: 2018-10-12
forum: General Help
---

### Post by Qd64erK on 2018-10-12
Hi,

I had a problem with one on the updates of xubuntu-artwork and I had to uninstall it. I resolved the problem by reinstalling the elementary-xfce-icon-theme package. But by uninstalling xubuntu-artwork I had to remove xubuntu-default-settings. Now most of the entries on the xfce4-setting-manager are gone, even after I reinstalled everything. I have a backup of my home folder prior to this error and I have been searching if there's something I should copy back to $HOME, like the ~/.config/menu/ folder but no luck.  

So, any idea how I could revert back my Settings Manager?

  Thanks in advance for your help,
 Cheers

---

### Post by again? on 2018-10-12
First thing I would do is create and test a new user account.
This will tell you if it is a $HOME/config problem.

---

### Post by ajgreeny on 2018-10-12
Most of those xfce4 desktop settings, if not all of them, will have been in ~/.config/xfce4 and ~/.config/xfce4-session but if you have other folders starting with xfce4 restore them as well, though I would be very surprised if they are not still present in your home as removing installed packages will never remove configuration files or folders from your home.

Good luck!

---

### Post by Qd64erK on 2018-10-12
That's it, **thank you!**

I copied everything inside the ~/.config/xfce4, ~/.config/xfce4-session and ~/.local/share/xfce4 folders and it's all normal now. Afterwards I open every file and I still don't know which one (maybe several?) is setting the entries. No matter, all is well now :)

Again, thank you for your help.
Cheers.

---

### Post by ajgreeny on 2018-10-13
Great news! 

Please mark as SOLVED using the Thread Tools menu up-top if this is now solved to your satisfaction; I see you have already edited the thread title, but it is much clearer if you use the forum to do that for you and it is a great help to users searching the forum.

---

