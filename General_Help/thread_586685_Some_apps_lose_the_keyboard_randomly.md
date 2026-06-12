---
title: "Some apps lose the keyboard randomly"
date: 2007-10-22
forum: General Help
---

### Post by dchenbecker on 2007-10-22
I had Feisty installed on my laptop and it worked flawlessly. I just upgraded to Gutsy and now apps randomly stop responding to the keyboard. They'll be working fine and then all of a sudden no more key events, although mouse still works fine. It most often happens in Thunderbird or Eclipse, but it has happened in gnome terminal just this morning. The strange thing is that sometimes if I switch away from a broken app and then switch back, it gets a burst of 5-10 of the last keys I typed when the app locked up. I'm going to try to grab xscope and xmon and see if the key events are still reaching the apps, but it seems like a general X issue since it's happened in both compiz (default after I upgraded) and metacity (tried to switch to see if it was a wm issue). At this point my laptop is not very usable.

Thanks,

Derek

---

### Post by tak1150 on 2007-11-01
I get the same problem. It's infrequent enough that my laptop is usable, but VERY annoying!
Thanks for the clue that it's not the window manager's fault.

Any input is appreciated.

Tak

---

### Post by dchenbecker on 2007-11-01
Actually, it turns out that it's SCIM (for me). I disabled SCIM with "im-switch -s none" and I haven't had any lockups since.

Derek

---

### Post by tak1150 on 2007-11-01
> **dchenbecker said:**
> Actually, it turns out that it's SCIM (for me). I disabled SCIM with "im-switch -s none" and I haven't had any lockups since.

Derek

Ah, I have SCIM running as well (every once in a while I use Japanese).
Maybe I'll need to file a bug against SCIM.

Thanks for the info.

---

### Post by dchenbecker on 2007-11-01
&#31169;&#12418;&#26085;&#26412;&#35486;&#12434;&#35441;&#12379;&#12414;&#12377;&#12290;In the meantime you can disable SCIM and when you need to use it just start your apps from the command line with the GTK_IM_MODULE env var set:

GTK_IM_MODULE=scim gedit

And SCIM will work for just that app.

Derek

---

### Post by tak1150 on 2007-11-01
> **dchenbecker said:**
> &#31169;&#12418;&#26085;&#26412;&#35486;&#12434;&#35441;&#12379;&#12414;&#12377;&#12290;In the meantime you can disable SCIM and when you need to use it just start your apps from the command line with the GTK_IM_MODULE env var set:

GTK_IM_MODULE=scim gedit

And SCIM will work for just that app.

Derek

Thank you Derek.

I just[ filed this bug against SCIM]("http://sourceforge.net/tracker/?group_id=108454&atid=650539"). Hopefully they can figure this out so we don't have to do what you suggested above forever.

---

### Post by tak1150 on 2007-11-03
> **dchenbecker said:**
> Actually, it turns out that it's SCIM (for me). I disabled SCIM with "im-switch -s none" and I haven't had any lockups since.

Derek

After I did "im-switch -s none" I can't seem to use SCIM any more.
If I do "scim" from Alt+F2, I get the icon in the system tray, but when I left-click it, the pull-down menu does not appear. How can I get SCIM back? Thank you!

Tak

---

