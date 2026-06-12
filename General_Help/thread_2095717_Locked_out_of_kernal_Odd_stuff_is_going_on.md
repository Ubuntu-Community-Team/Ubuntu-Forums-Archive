---
title: "Locked out of kernal: Odd stuff is going on"
date: 2012-12-17
forum: General Help
---

### Post by FriedZebra on 2012-12-17
Went a few places for help (here included) to no avail, thought I'd try my luck in the general area.  

Right now I am locked out of my kernal.  When prompted for my password on log on this occurs: 

[http://s1190.photobucket.com/albums/z443/ReeferCheefer420/Tech/?action=view&current=Ubuntulockout.mp4](http://s1190.photobucket.com/albums/z443/ReeferCheefer420/Tech/?action=view&current=Ubuntulockout.mp4)

[http://s1190.photobucket.com/albums/z443/ReeferCheefer420/Tech/?action=view&current=2ndattempt.mp4](http://s1190.photobucket.com/albums/z443/ReeferCheefer420/Tech/?action=view&current=2ndattempt.mp4)


I've attempted to change it through the terminal in my guest account using varied commands, although all return with the same message saying I am not authorized to change the password.  

If anyone has any advice it would be more than dandy, I need to get back on my kernal ASAP and this has been bothering me for over 4 days now.  

Thanks, Zebra.

---

### Post by JKyleOKC on 2012-12-17
Since you can log into the guest account, the problem is almost certainly connected to your main account only. If you can get to the GRUB menu by pressing the left shift key while booting, select the second entry (the one marked "recovery") rather than the first. That will bypass normal login routines and show you a menu, and somewhere in that menu will be "drop to root shell" or words to that effect. Select that choice, which will automatically log you into a terminal with super-user privileges. From there you can type "man passwd" to get instructions on using the "passwd" command to change your password.

However, the look of the video you posted makes me think it's not a password error, but rather something much more drastic that has happened to the video configuration stored in your home directory -- and I'm not expert enough to tell you how to fix that!

When you're logged into the recovery terminal, be extremely careful. Mistakes there can totally destroy your system and all your files, and you won't be told about them in time to stop them.

To leave the recovery terminal, use the command "shutdown now" to make certain that everything is cleaned up before you power down. Most machines will power down automatically after doing the cleanup; the rest will tell you when it's safe to do so.

Hope this helps some!

---

