---
title: "log out without closing everything"
date: 2019-10-31
forum: General Help
---

### Post by rgsopedra on 2019-10-31
Hey guys, 

I'm using for the first time Ubuntu (18.04). I'm used to login out from my session whenever I stand up for security reasons. 
However, when I log out (ctr+alt+supr, etc), as soon as I'm back everything is closed, like if I had turned off my computer. 

Is there any way, additional software or configuration I can work with to log out from my computer (meaning that it will be necessary to put my password to log back in) without having everything closed?

Thanks a ton!

---

### Post by ajgreeny on 2019-10-31
You can lock the screen, as I do.

The keyboard shortcut for this will probably depend on the DE version of *ubuntu you use, but may already be set to either Ctrl+L or Winkey+L so have a look in the settings for your current keyboard shortcuts.

---

### Post by deadflowr on 2019-10-31
Ubuntu's desktop: gnome, has had a broken save session feature for a while now.
(Other desktop environments like Kubuntu or Xubuntu have functional and very robust session saving features.)

One option to get that function in Ubuntu with gnome is to install an extension (and the trimmings it requires) following the guidance here:
[https://www.linuxuprising.com/2018/04/gnome-save-and-restore-running.html]("https://www.linuxuprising.com/2018/04/gnome-save-and-restore-running.html")

A second option to lock it like what ajgreeny posted.

Another option is, of course, to forego the gnome desktop ( and all it's fickleness) and install a different desktop like one of the two I mentioned above.

---

### Post by TheFu on 2019-10-31
If you care about security, then using full disk encryption and fully shutting down when the system isn't in your hands is required. Standby, hibernation are not sufficient.
A Linux system that is running can be attacked using USB devices with special device driver cargo.  I've seen red-team hackers make these devices during a security conference "hands on" session.  Different payloads depending on the target OS.

If you don't need to be that serious, then use the screen saver lock. It will work with standby.

But if you need real security, don't leave the computer powered on and definitely don't leave anything unencrypted.

---

### Post by rgsopedra on 2019-11-04
This was exactly what I was looking for, I feel a little bit stupid for not being able to find this solution hahaha. Anyway, thanks a lot for your help!

---

