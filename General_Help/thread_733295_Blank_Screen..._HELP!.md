---
title: "Blank Screen... HELP!"
date: 2008-03-23
forum: General Help
---

### Post by juanfran27 on 2008-03-23
Hello all.

I just installed Ubunu 7.10 on my Dell 1520, I had a hard time configuring the hardware, but in the end it all went well. I have not had a problem, until now. I was playing around with the compiz, setting backrounds and all. Suddenly the cube would not turn anymore. I proceeded to reboot my laptop, ubuntu loaded and asked for my username and password. When the desktop was loading nothing but a folder was on it (no taskbar, no dock bar, nothig), so I switched off the cmputer and back on. Again, I typed my username and password, then nothing, just a blank screen.

Now what?

I have Ubuntu installed on another partiotion, so I'm able to use Vista.

I'm a new user, and my computer skills are only windows related. I'm a biologist, not a coputer scientist, so please keep it simple and understandable.

Thanks in advance.

---

### Post by mali2297 on 2008-03-23
Press **Ctrl+Alt+F1** to get to a terminal. Enter this command:
```

sudo dpkg-reconfigure xserver-xorg

```
You will be asked some questions, answer them as best you can. If uncertain, choose the default (just press Enter).

Then, press **Ctrl+Alt+F7** followed by **Ctrl+Alt+Backspace**.

---

### Post by juanfran27 on 2008-03-23
Thanks for the quick sponse! I'l try it.

Why did this happen anyway?

---

### Post by juanfran27 on 2008-03-23
Ok, it worked. I-m on Ubuntu now. But something is wrong. Compiz won't work. When I choose my Visual Effects to be 'Custom' the window blocks for a few seconds and goes back to 'Normal'.

Any ideas?

---

### Post by mali2297 on 2008-03-23
If you haven't changed graphics driver or anything like that, try resetting your Compiz configuration. Open the file manager and show hidden files. Can you find any files/directories that seem to be connected to Compiz? Remove or rename them. 

Try to enable the desktop effects again.

---

### Post by juanfran27 on 2008-03-23
The Restricted Driver Manager says my Nvidia card is in use and enabled. I opened my file manager and shown the hidden files and found a file named 'config' in /<myname>/compiz/compizconfig/. Is this the one you are talking about? If I open it it says:

[gnome_session]
profile = 
plugin_list_autosort = true


BTW, I got a message after I could get Ubuntu running again, saying:

"There was an error starting GNOME settings daemon. Some things, such as themes, sounds, or backround setting may not work correctly. The las error message was: /tmp/d-bus OnhgFWLeF. GNOME will still try to restart the setting daemon next time you log in."

What does this all mean?

Sound is working, it is not affected.

**EDIT:** I changed the name of the file mentioned above and tried choosing costum visual effects again, I had the same result.

---

### Post by mali2297 on 2008-03-24
You could try moving all your personal configuration files. In the terminal, the following commands should suffice:
```

cd
mkdir backup
mv -v \.??* backup

```
You will then have all those files in a backup folder. 

To move them back:
```

mv -v ~/backup/\.??* ~

```

---

### Post by juanfran27 on 2008-03-24
It is fixed now. The problem occurs when I try to choose an image as a skydome image. As soon as I change it back to predetermined it works fine. Weird.

---

