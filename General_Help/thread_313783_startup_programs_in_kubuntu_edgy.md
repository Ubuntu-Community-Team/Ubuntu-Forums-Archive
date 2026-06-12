---
title: "startup programs in kubuntu edgy"
date: 2006-12-06
forum: General Help
---

### Post by blar on 2006-12-06
Greetings,

Okay, I'm still somewhat new to kubuntu, so I probably just don't know where to look, but this is *really* frustrating me right now.  I just did a clean install of Kubuntu 6.10 Edgy last night, and I've been going through the process of getting my setup back the way I like it.  I've installed conky 1.4.4 and I'm trying to figure out how to get it to start up automatically when i log into linux.  But every search I run thru linuxquestions, ubuntu forums, google, and askjeeves just returns garbage.

My question is: where in Kubuntu can I set up startup programs?  (and why is it so hard to find!?!)


thanks,
blar

---

### Post by ajgreeny on 2006-12-06
Add a link to it in your .kde/autostart folder.  Its a hidden folder so you may need to show hidden files in konqueror first.

---

### Post by Ksmith3637 on 2007-01-02
> **ajgreeny said:**
> Add a link to it in your .kde/autostart folder.  Its a hidden folder so you may need to show hidden files in konqueror first.

in kubuntu

nice -so where is the file located (sorry i found it)  but i do not see anylinks in it or how to do it.... and how do you get conky in the right corner...???

thanks
ksmith

---

### Post by NZ-Wanderer on 2007-01-16
Real silly question, but how do I add a link???

I am wanting to have:

[COLOR="Red"]sudo g15daemon[/COLOR]

and

[COLOR="Red"]xbindkeys[/COLOR]

added to my startup, but have never been able to figure out how to do it..

> **ajgreeny said:**
> Add a link to it in your .kde/autostart folder.  Its a hidden folder so you may need to show hidden files in konqueror first.

---

### Post by armware on 2007-01-16
to have kde issue commands automatically at startup, you basically create a text file with:

```
#!/bin/bash
```

as the very first line, then whatever commands you'd like it to run, so it should look like:

```
#!/bin/bash
xbindkeys
```

as for g15daemon (i have no idea what that is, so bear (or is it bare?) with me) requiring sudo, it's not gonna work too well as an automated script unless the program executing it has sudo-like permissions, so i'd recommend changing it to  kdesu g15daemon  so that kde will pop up a password box giving it sudo permissions.
to  make it real easy, copy-paste this into a new text file:

```
#!/bin/bash
kdesu g15daemon
xbindkeys 
```

and save it to:  ~/.kde/Autostart/autoexec

don't forget to make it executable. 
right click autoexec->properties->permissions tab->check 'is executable'

that should work.

---

### Post by NZ-Wanderer on 2007-01-17
Hehe, G15daemon lets me have an LCD display on my Logitech G15 keyboard :) - To start it now, I have to issue the sudo g15daemon command in a normal terminal, so that's why I put the sudo in my message :)

Thanks for the reply, I will give it a go and see what happens..

> **armware said:**
> as for g15daemon

---

### Post by kogber on 2007-01-18
slightly more detailed version of adding startup program:

you can create a separate text file for each program or group of programs to keep things neat:

[INDENT]```
kate ~/.kde/Autostart/start-**programName**
```


Insert this into the file:
```
#!/bin/sh **programName**
```
Make the file executable:
```
chmod +x ~/.kde/Autostart/start-**programName**
```[/INDENT]

Ubuntu has a gui for this, Kubuntu should too, but as far as I know Edgy does not.

---

