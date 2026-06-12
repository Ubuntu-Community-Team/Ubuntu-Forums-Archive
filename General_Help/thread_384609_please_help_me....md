---
title: "please help me..."
date: 2007-03-14
forum: General Help
---

### Post by olynth on 2007-03-14
Today is my first day on Ubuntu, but I made a stupid mistake...

I went in User Account Editor, and changed /HOME/user in /root
Now, when i`m trying to login, i receive this error:

**User`s $Home/.dmrc file is being ignored. This prevent the default session and language from being saved. File should be owned by user and have 644 permissions. User`s $HOME directory must be owned by user an not writable by other users.**

After I push OK:

**Your session only lastd less than 10 seconds. If you have not logged out yourself, this could  mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you cand fix this problem.**

Under that message: 

**/etc/gdm/PreSession/Default:Registering your session with wtmp and utmp**

plus another 5 lines, but are too long to write.

please help me....

---

### Post by Adam_GUI on 2007-03-14
If this is your first install, and you don't have any configurations to save--I'd say to just reinstall and make a sticky note about what you did in red ink with the words "Do Not Attempt" in big bold letters.

At least, that's what I'd do.

---

### Post by tribaal on 2007-03-14
Can you boot into recovery mode?
If yes, then from the recovery mode desktop you should be able to make the change back to normal.

Otherwise, things will get a little more complicated.
If you installed Ubuntu just yesterday and your system is still pretty "vanilla" (nothing much has changed since the original install), then maybe a reinstall will save you headaches? But next time don't change the same setting :)

Please post back if the recovery mode changed anything.

- trib'

---

### Post by kelbizzle on 2007-03-14
yea reinstalling ins't so bad. The more you fool around, tinker, and break stuff. The better you'll get at understanding how things are working.

---

### Post by olynth on 2007-03-14
yes, I can boot in recovery mode, but what should I do?

Now I`m stuck on this:

[b] Give root password for maintenance
(or type Control-D to continue):[/b]

If i give my password, then i`m here:

**root@olynth:~#**


PS: Sorry if my english is bad...

---

### Post by tribaal on 2007-03-14
If you want to fix this yourself, then this is the way to do it without a reinstall (I guess):
[COLOR="Red"]EDIT: From recovery mode start with point 2 (consider you're already at the terminal)[/COLOR]
[LIST]
[*]Boot using the LiveCD.
[*]Mount your Ubuntu partition: launch a terminal, and then type in "mount /dev/hda1 /mnt"(replace /dev/hda1 by the correct partion name)
[*]type in "cd /mnt/etc/"
[*]type in "nano passwd" ( this will open a text editor in command line mode - don't freak out, it's much easier than it seems: most commands are visible on the bottom of the screen).
[*]Find the line that contains your username, and change the part where it says "/root", to "/home/username"
[*]Press Ctrl-w (save) then ctrl-x (quit)
[*]Quit and reboot without the liveCD.
[/LIST]

Does it work?

- trib'

---

### Post by olynth on 2007-03-14
> **tribaal said:**
> If you want to fix this yourself, then this is the way to do it without a reinstall (I guess):
[COLOR="Red"]EDIT: From recovery mode start with point 2 (consider you're already at the terminal)[/COLOR]
[LIST]
[*]Boot using the LiveCD.
[*]Mount your Ubuntu partition: launch a terminal, and then type in "mount /dev/hda1 /mnt"(replace /dev/hda1 by the correct partion name)
[*]type in "cd /mnt/etc/"
[*]type in "nano passwd" ( this will open a text editor in command line mode - don't freak out, it's much easier than it seems: most commands are visible on the bottom of the screen).
[*]Find the line that contains your username, and change the part where it says "/root", to "/home/username"
[*]Press Ctrl-w (save) then ctrl-x (quit)
[*]Quit and reboot without the liveCD.
[/LIST]

Does it work?

- trib'

I didn`t boot from the cd, is ok? 

the only line with my name is this:

```
**olynth:x:1000:1000:olynth,,,:/HOME/olynth:/bin/bash **
```

---

### Post by olynth on 2007-03-14
up

---

### Post by tribaal on 2007-03-14
Hum... then I'm afraid I didn't understand the problem properly...

I suggest reinstalling then, except if someone has a better idea of how to fix your problem here. 
Really sorry about that mate, I though this could have been the cause of it all :(

Hope this won't pull you off :(

- trib'

---

### Post by olynth on 2007-03-14
> **tribaal said:**
> Hum... then I'm afraid I didn't understand the problem properly...

I suggest reinstalling then, except if someone has a better idea of how to fix your problem here. 
Really sorry about that mate, I though this could have been the cause of it all :(

Hope this won't pull you off :(

- trib'


Anyway, thanks for the help. :)

Ok, i must reinstall Ubuntu. How can I do that? The same as installing? (format partition, etc)

---

### Post by Adam_GUI on 2007-03-14
> **olynth said:**
> Anyway, thanks for the help. :)

Ok, i must reinstall Ubuntu. How can I do that? The same as installing? (format partition, etc)

Yup.  The Same Yellow-Brick-Road you took gettin' there the first time.  :)

---

