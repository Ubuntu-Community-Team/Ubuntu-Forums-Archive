---
title: "How do I combine 2 commands in 1 launcher?"
date: 2006-10-26
forum: General Help
---

### Post by MetalMusicAddict on 2006-10-26
Hello. Im trying to put 2 commands in 1 launcher.

Currently I have to mount my network drives in Gnome *after* I log on. Not at boot because of some bug. I have to put **noauto** in the FSTAB or I get a HAL error and my desktop wont start.

So I have been making launchers to mount each drive. **gksudo mount /media/Multimedia** and **gksudo mount /media/Storage** are the 2 commands.

How can I combine the commands? I was thinking it would be like: **gksudo mount /media/Multimedia && mount /media/Storage** but that isnt it.

If anyone can type out the exact command that would be awesome.

---

### Post by aysiu on 2006-10-26
Create a shell script called *mountnetwork*

```
sudo nano /usr/local/bin/mountnetwork
``` In the new text file, put: ```
#!/bin/bash
gksudo mount /media/Multimedia
gksudo mount /media/Storage
``` Then save (Control-X, Y, Enter). ```
sudo chmod +x /usr/local/bin/mountnetwork
``` Then just use the command *mountnetwork* at startup, and you should be good.

---

### Post by gorded on 2006-10-26
OR 
```
<command> && <command>
```

---

### Post by MetalMusicAddict on 2006-10-26
As usual, you rock aysiu. [IMG]http://www.kerrazy-torrents.net/style_emoticons/default/punk.gif[/IMG]

---

### Post by aysiu on 2006-10-26
> **gorded said:**
> OR 
```
<command> && <command>
```
I'd say that, too, except the OP has already said: > How can I combine the commands? I was thinking it would be like: gksudo mount /media/Multimedia && mount /media/Storage but that isnt it.

---

### Post by aysiu on 2006-10-26
> **MetalMusicAddict said:**
> As usual, you rock aysiu. [IMG]http://www.kerrazy-torrents.net/style_emoticons/default/punk.gif[/IMG]
So... did it work... or not?

---

### Post by MetalMusicAddict on 2006-10-26
> **aysiu said:**
> So... did it work... or not?
Oh yea, sorry. I thought it was implied. :)

Though, now I wonder if I could get it to mount them without me putting in the password.:-k

---

### Post by aysiu on 2006-10-26
It's definitely possible. I'm not sure what the path is to the mount command, but let's say it's /usr/bin/mount (please double-check) and that your username is *metal*.

Do ```
sudo visudo
``` to edit the /etc/sudoers file, and add this line: ```
metal ALL = NOPASSWD: /usr/bin/mount
``` In which case you can also probably change the original command to *sudo mount* instead of *gksudo mount*.

---

### Post by MetalMusicAddict on 2006-10-26
Ok so heres how it worked using what aysiu said.

**1.** Create a shell script called *mountnetwork*
```
sudo nano /usr/local/bin/mountnetwork
```

**2.** In the new text file, put: [SIZE="1"][COLOR="Gray"](Or whatever your path is. This mounts 2 drives for me.)[/COLOR][/SIZE]
```
#!/bin/bash
sudo mount /media/Multimedia
sudo mount /media/Storage
```
Then save (Control-X, Y, Enter).

**3.** Then in a terminal we make it executable.
```
sudo chmod +x /usr/local/bin/mountnetwork
```

**4.** Add "mountnetwork" to sessions on startup.

**5.** Then in a terminal:
```
sudo visudo
```
to edit the /etc/sudoers file, and add this line: [SIZE="1"][COLOR="Gray"](Change "metal" to whatever your username is.)[/COLOR][/SIZE]
```
metal ALL = NOPASSWD: /bin/mount
```

Thanx aysiu. My only concern is now this gives sudo powers to "mount". It is just me on this machine though.

---

### Post by aysiu on 2006-10-26
*sudo* has always had the power to mount. The only difference is that if you're logged in as *metal*, you can mount without issuing your password.

---

### Post by MetalMusicAddict on 2006-10-26
> **aysiu said:**
> *sudo* has always had the power to mount. The only difference is that if you're logged in as *metal*, you can mount without issuing your password.
Yes.

Does that open me up to anything else though? Anything besides my own stupidity if I misuse "mount"? :)

---

### Post by tfm_copycat on 2008-07-13
Thanks Aysiu for the tutorial, it was really useful.
Now, I was wondering: If I want to run a command only after the second command is done, how do I do it?

I have:
```

#!/bin/bash
rejoystick -d
wine "/media/hd/IL-2 Sturmovik 1946/il2fb.exe"

```

And I would like to run "$killall -9 rejoystick" when I close il2fb.
I was guessing a while loop, but I couldn't find an example for my specific need.
Thanks in advanced.

---

### Post by Bachstelze on 2008-07-13
> **tfm_copycat said:**
> Thanks Aysiu for the tutorial, it was really useful.
Now, I was wondering: If I want to run a command only after the second command is done, how do I do it?

I have:
```

#!/bin/bash
rejoystick -d
wine "/media/hd/IL-2 Sturmovik 1946/il2fb.exe"

```

And I would like to run "$killall -9 rejoystick" when I close il2fb.
I was guessing a while loop, but I couldn't find an example for my specific need.
Thanks in advanced.

Just add it after the other command ;) Your script will only proceed to the next command when the previous one is complete.


```

#!/bin/bash
rejoystick -d
wine "/media/hd/IL-2 Sturmovik 1946/il2fb.exe"
killall rejoystick

```

(*kill -9* should be used only when the process refuses to terminate. In most cases, *kill* alone will do.)

---

### Post by tfm_copycat on 2008-07-13
Wow, that was fast! And it worked perfectly =)
Thanks a lot, HymnToLife!

---

