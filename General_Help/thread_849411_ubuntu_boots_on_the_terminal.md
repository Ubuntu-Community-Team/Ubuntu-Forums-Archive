---
title: "ubuntu boots on the terminal"
date: 2008-07-04
forum: General Help
---

### Post by hamzaB on 2008-07-04
i installed ubuntu a couple of days ago and when i was using it something happened and i couldn't access "i don't know what's its name" .it has the system files and drives.anyway ,i logged in and out to see if it fixes the problem but ubuntu booted directly in the terminal and nothing else on the screen.i accessed these forums from firefox by accessing the help section on the terminal.please can anyone help me ,i was really starting to like ubuntu and learn it when this happened .any help would be appreciated.

---

### Post by Mikecore on 2008-07-04
> **hamzaB said:**
> i installed ubuntu a couple of days ago and when i was using it something happened and i couldn't access "i don't know what's its name" .it has the system files and drives.anyway ,i logged in and out to see if it fixes the problem but ubuntu booted directly in the terminal and nothing else on the screen.i accessed these forums from firefox by accessing the help section on the terminal.please can anyone help me ,i was really starting to like ubuntu and learn it when this happened .any help would be appreciated.

after loggin in at the prompt type

```

startx

```

see what happen if it fail to bring up your gui you have an X server issue and we will have to go from there

---

### Post by hamzaB on 2008-07-04
i typed the message and the was :fatal error server already in use or something like that.even firefox didn't open this time i had to type thyis from windows xp.

---

### Post by JiminSD on 2008-07-04
Have you tried Ctrl+Alt+F7?

---

### Post by hamzaB on 2008-07-04
actually i'm new to ubuntu and i don't know much. what does that do?

---

### Post by hamzaB on 2008-07-04
@ jiminisd :i did what you said but nothing happened .what should i do?

---

### Post by hamzaB on 2008-07-04
here's the actual message i get when typing startx
X: warning: process set to priority -1 instead of requested priority 0

Fatal Server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again
i hope this helps

---

### Post by hamzaB on 2008-07-04
bump

---

### Post by reddox on 2008-07-04
> **hamzaB said:**
> here's the actual message i get when typing startx
X: warning: process set to priority -1 instead of requested priority 0

Fatal Server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again
i hope this helps

Try this before starting xserver:

sudo rm /tmp/.X0-lock

hit enter and enter your password.

now type 'startx'

---

### Post by l0fls on 2008-07-05
maybe the GUI aint loading
safemode possibly try pushing ESC when your computer first starts and goes threw the bios and all that good stuff.

---

### Post by hamzaB on 2008-07-05
@ reddox: i did that but when i typed startx again the screen goes blank for a moment and then the terminal appears again but this time i'm logged in as a root and the background becomes green .also the whole screen flickers.

---

### Post by hamzaB on 2008-07-05
@l0fls: i entered recovery mode ,checked for broken packages,checked x server and then continued to boot.after that ,the same thing happened ,it boots to the terminal with nothing else on the screen.

---

