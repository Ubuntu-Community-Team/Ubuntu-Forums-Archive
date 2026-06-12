---
title: "Screen Problems"
date: 2008-03-31
forum: General Help
---

### Post by The Pinny Parlour on 2008-03-31
Hello

I can see the BIOS and also the Ubuntu, "Knight Rider" screen before it goes into standby mode.  I can actually hear the drums as Ubuntu enter the stage where the user is to enter their username and password.  Can anyone help me get my Ubuntu box working again?

Thanks

---

### Post by sancho panza on 2008-03-31
This MIGHT be a bug that hasnt been fixed in gutsy. Try this, when coming back from standby/suspend, after u hear the drums for login, press Ctrl+Alt+F3 (or Ctrl+Alt and any func key F1-F6) this should bring u to the text based terminal. Now press Alt+F7. Hopefully, you should now see ur login screen.

---

### Post by The Pinny Parlour on 2008-04-01
sancho panza   thanks mate.  That at least got me to a prompt.  Alt and F7 didn't work however.  The screen attempted to boot into GUI but failed into standby mode.  I then had to Ctrl, Alt, F3 to get back to prompt.  any ideas on how I can get my GUI back?  Desperate.

---

### Post by The Pinny Parlour on 2008-04-01
ok it continues.  When I attempt to use the command, 
```
startx
```
I get the following:
 xauth: creating new authorityfile /home/myusername/ .serverauth.5574
Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/ .X0-lock and start again.
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key giving up.
xinit: unable to connect to X Server
xinit: No such process (errno3): Server error.

PLEASE HELP  :(

---

### Post by The Pinny Parlour on 2008-04-01
Bump

---

### Post by sancho panza on 2008-04-01
Maybe if you provide more detail, someone else might help. Worst case, move the thread to another section.
Do you have the problem when you boot up or when u attempt to come back from standby/hibernate? Is this a new install or how long have you been running ubuntu without problems? What changes have you made to ur system before you started getting these problems?

---

### Post by The Pinny Parlour on 2008-04-02
Thanks mate.

Funnily enough, I just booted in a live cd and mounted a USB HDD. I then made a root user so I could copy my data from hdd to backup USB hdd. Upon rebooting the system, it all works.

anyway, I hope it holds out till the next release.
__________________

---

### Post by The Pinny Parlour on 2008-04-02
Ok the issue is back.

This happens when I boot the computer at the start of the day.

I turn it on, I see BIOS screen, I then see the Ubuntu progress bar.

After that, the PC monitor will go into standby mode.  I can however enter in my username and password without seeing it on the screen, and I can hear Ubuntu startup.  

I then press Ctrl+Alt+F3 to get to a prompt and attempt to restartx but it doesn't work.

Nvidia 7600GS


Any ideas?

Thank you

---

### Post by Crafty Kisses on 2008-04-02
> **The Pinny Parlour said:**
> Hello

I can see the BIOS and also the Ubuntu, "Knight Rider" screen before it goes into standby mode.  I can actually hear the drums as Ubuntu enter the stage where the user is to enter their username and password.  Can anyone help me get my Ubuntu box working again?

Thanks

Can you boot into verbose mode, and see what's actually happening? Possibly post the output.

---

### Post by The Pinny Parlour on 2008-04-04
Thanks mate.

I don't even know what Verbose mode is.   

I'm just nuking the entire installation and installing the hardy beta.

---

