---
title: "Compiz doesn't start automatically."
date: 2008-05-11
forum: General Help
---

### Post by detroit/zero on 2008-05-11
Hi all,

I have a fresh install of 8.04 with compiz-fusion installed. Everything worked fine the first few times I rebooted, but the last few times compiz doesn't start on its own.

I have metacity disabled via ubuntu-tweak. I have added *compiz --replace &* and *emerald --replace &* to Sessions>Startup, along with AWN.

After logging in, I'm at my desktop with default metacity settings. If I put the Compiz icon in the panel and select reload window manager, everything comes up the way it should, including AWN.

I have a main-menu sitting in my top panel just so I can grab the Compiz icon every time and do this. It's quite a pain, as you can imagine.

Any ideas on why compiz won't start on its own?

---

### Post by detroit/zero on 2008-05-12
bump.

---

### Post by prshah on 2008-05-12
> **detroit/zero said:**
> Hi all,
After logging in, I'm at my desktop with default metacity settings. If I put the Compiz icon in the panel and select reload window manager, everything comes up the way it should, including AWN.


I'm having the same problem; the workaround I have is to add ONLY the ```
compiz --replace
``` command to my System-Preferences-Sessions, so that it will start automatically. I _have not_ added emerald --replace. While metacity was the default desktop in Ubunt 7.10, in 8.04 it's supposed to be compiz; any chance that your ubuntuTweak is not allowing the default desktop to load (in this case, compiz?)

what is the output of ```
ps -e | grep metacity
ps -e | grep compiz
``` at bootup?

Is your "compiz --replace" command correctly set in Sessions? Eg, spelling mistakes, typing in the description box instead of command box, etc.

Have compiz in Sessions does extend bootup->desktop time by a few seconds, and causes a couple of unseemly "black" desktops, but short of that, works fine.

---

### Post by detroit/zero on 2008-05-12
Yes, it should be entered into Sessions correctly. I checked, and no spelling errors or anything like what you say.

The only difference between what you have entered and what I have entered is a & sign; e.g.:

```
compiz --replace &
```

i read somewhere on here that the & sign was necessary on both the compiz and emerald startup commands.. I don't know enough about it to question it, and it worked up until a few days ago.

I do think UbuntuTweak has something to do with all of this. This time when I booted up, all my desktop icons are missing, even though in both UbuntuTweak and Config Editor, it's set to show a number of them.

My output for *ps -e | grep metacity* was nothing. For *ps -e | grep compiz* i got the following:
```
zero@zero-laptop:~$ ps -e | grep compiz
 6849 ?        00:00:14 compiz
```

I'm toying with the idea of another fresh install.. I have my home directory on a separate partition, so it's not that big of a deal. It's kind of a pain and does eat up some time, doing all the updates and getting all my software packages right.. But I think I'll get it right this time and leave ubuntutweak off the list of things to get.

Maybe if they had an "undo" feature...

---

### Post by prshah on 2008-05-13
> **detroit/zero said:**
> 
```
compiz --replace &
```


Good news, you don't need to uninstall/reinstall/whatever.

In the sessions command box, you do not need to append the "&". You need to do this when you are in a terminal.

The & "backgrounds" the process. But processes from the sessions are already forked; eg, no need to "background" them specifically.

---

### Post by detroit/zero on 2008-05-13
I wondered what the "&" was all about.. thanks.

I did go through my startups. I removed emerald, compiz, and AWN. For giggles' sake, I did a reboot and verified that they didn't start up or land on the processes list.

I went to the Sessions>Startup and re-added compiz, thusly:
```
compiz --replace
```

I also re-added AWN.

Still, neither of these will start when my system boots.

I realize AWN relies on compiz, so that explains that one.

Why do I, every single time my computer starts, have to go into my main menu, select the Compiz Icon, then go to the Compiz icon in my notification area, right-click, and select "Reload Window Manager"?

It works flawlessly when I do that. The screen blanks for about three or four seconds, and the AWN bar slides across the screen into its resting place. All the effects, all the animations, all of everything (well, [almost everything]("http://ubuntuforums.org/showpost.php?p=4926595&postcount=5")) is there.. it just won't start automatically.

---

### Post by prshah on 2008-05-13
> **detroit/zero said:**
> I did a reboot and verified that they didn't start up or land on the processes list.
I went to the Sessions>Startup and re-added compiz, thusly:
```
compiz --replace
```


Very thorough of you. I'm now just clutching at straws; 

a) In the sessions window, is the checkbox next to your compiz command ticked?

b) I have AWN loading up in the Sessions list _before_ Compiz... maybe that can help?

c) if all else fails, remove all Compiz and AWN related entries in the Session manager, reboot, open a terminal and give the "compiz --replace" command; it will dump a few lines of output; can you post that here?

---

### Post by detroit/zero on 2008-05-13
OK. As requested, here is what I get when I remove both compiz and AWN from my startups and type *compiz --replace* in a terminal:```
zero@zero-laptop:~$ compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
zero@zero-laptop:~$ 
```It's sort of telling. I'm not sure what it's telling me. I also have no idea what to do about it.

Why will it start from the icon but not in a terminal?

---

### Post by alsamman on 2008-05-13
I have the exact same problem as you. I have compiz on sessions but it won't load and goes to metacity but if I reload it works fine. I have compiz tray icon on startup and window manager selected is compiz but it still wont work. The weird thing is that before everything boots 100%, you can see awn on but when the desktop refreshes, it goes away.

---

### Post by anuban on 2008-05-13
I also have the same issue.  If you guys find out any solution, I will be very much interested to know.  As it is a nuissance to reload windows manager everytime I login.
I have been living with this issue for quite sometime.  Even reinstall didn't help.
May be it is because of NVIDIA.  Not sure though..
Will appreciate if the solution exist.
I can confirm the exact same steps as the OP to be followed to bring back the life of the desktop.

Please help.

---

### Post by Superevil on 2008-05-13
I had the same issue and all I did to fix mine was add compiz icon to startup

---

### Post by prshah on 2008-05-14
> **detroit/zero said:**
> ```
zero@zero-laptop:~$ compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
zero@zero-laptop:~$ 
```

> **alsamman said:**
> I have the exact same problem as you. 

> **anuban said:**
> I also have the same issue.  
I can confirm the exact same steps as the OP to be followed to bring back the life of the desktop.


Try this; add ```

LD_LIBRARY_PATH=/usr/lib
```

to your /etc/profile, log out and then log back in (or restart); did it help?

_if not_ try (solution 2):
[http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#GLX_EXT_texture_from_pixmap_is_missing](http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#GLX_EXT_texture_from_pixmap_is_missing)

Summary: > $ LIBGL_ALWAYS_INDIRECT=true compiz --replace --indirect-rendering

---

### Post by detroit/zero on 2008-05-14
No luck with either one of those fixes. No matter what I do I still have to go to System Tools> Compiz Icon and manually select that thing in order for my effects to work.

I'm not sure if it caused a conflict, but when I did my install of 8.04 I left my old home directory intact, including the .compiz and .config folders. Since I have some buggy behavior with AWN as well (when it's up and running) I'm thinking of deleting both these folders and starting from scratch with the two of them.

I don't know, though.. Like I said: Everything worked fine for a couple days, until I installed UbuntuTweak and started messing around with that.

---

### Post by detroit/zero on 2008-05-16
Well, it wasn't the fix I was hoping for but I did change my Startup from *compiz --replace* to *fusion-icon* and now everything comes up at system start.

---

### Post by vishnumrao on 2008-05-20
> **prshah said:**
> I'm having the same problem; the workaround I have is to add ONLY the ```
compiz --replace
``` command to my System-Preferences-Sessions, so that it will start automatically. I _have not_ added emerald --replace. While metacity was the default desktop in Ubunt 7.10, in 8.04 it's supposed to be compiz; any chance that your ubuntuTweak is not allowing the default desktop to load (in this case, compiz?)


prshah,

Adding ```
 compiz --replace 
``` to my sessions worked for me. thanks.

---

