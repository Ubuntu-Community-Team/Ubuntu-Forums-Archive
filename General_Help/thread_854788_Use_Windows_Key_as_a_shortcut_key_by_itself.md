---
title: "Use Windows Key as a shortcut key by itself"
date: 2008-07-09
forum: General Help
---

### Post by diogosales on 2008-07-09
I just arrived to Hardy from Vista, and I was really getting used to press the Windows Key and start typing so indexed stuff could be found.

I noticed, like in Gutsy, Hardy comes with that handy Deskbar as a panel widget. My only problem is that I can't make it recognize the Windows key by itself, it only works with some other key combined.

Now I read somewhere that Linux considers the Windows key as a meta-key, which could or should not do anything by itself.

Is this true? If so, is there any workaround on this?

Thanks in advance.

---

### Post by iaculallad on 2008-07-09
A workaround to make it pop the "Applications" menu in your Ubuntu:

System->Preferences->Keyboard Shortcuts, an option in the "Desktop" is your "Show the Panel Menu" (Default is Alt+F1), click on the Title then press the windows key (Value is **Super L**) on your keyboard to change its value.

Now, everytime you want to drop the Applications Menu, all you have to do is press the windows key.

---

### Post by diogosales on 2008-07-12
Indeed, I didn't try that before. So, why is Gnome able to recognize Super key as a shortcut by itself via Global Keyboard Shortcuts, and Tracker only allows its use as a meta-key to combine with some other key?

It's just that what I intended was to pop-up Tracker with the Windows Key, no the Menu.

Thanks.

---

### Post by ryanhaigh on 2008-09-17
I was just reading about a related issue and thought the info provided [on this page]("http://www.howtogeek.com/howto/ubuntu/use-the-windows-key-for-the-start-menu-in-ubuntu-linux/") may be useful to you. 

One of the comments suggests using xmodmap to map the windows key to a fictional F13, you should then be able to bind that key to bring up deskbar (although this will interfere with any other win key bindings for metacity/compiz).

---

### Post by core on 2008-09-17
I'll check it out as soon as I get home.

Although I got used to the Windows + Space combo for launching Gnome-Do.

Thanks!

---

