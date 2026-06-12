---
title: "Need help with remote connection"
date: 2007-05-14
forum: General Help
---

### Post by johnnyphive on 2007-05-14
I'm basically trying to setup my machine so i can remote into it from a windows xp machine from work (over the internet)

I've read so many different things, suggestions, howto's, etc I think i've go too much info in my head and it's starting to hurt :confused:

I've got xdmcp setup and working on my local network using xming on the xp machine, but i can't seem to connect from outside.

I've got port 177 (UDP) forwarded on my router (running pfSense) but don't know if I missing something.

Please help!

---

### Post by mssever on 2007-05-15
> **johnnyphive said:**
> I'm basically trying to setup my machine so i can remote into it from a windows xp machine from work (over the internet)

I've read so many different things, suggestions, howto's, etc I think i've go too much info in my head and it's starting to hurt :confused:

I've got xdmcp setup and working on my local network using xming on the xp machine, but i can't seem to connect from outside.

I've got port 177 (UDP) forwarded on my router (running pfSense) but don't know if I missing something.

Please help!
I wouldn't recommend running XDMCP over the Internet since it's really insecure unless you use an SSH tunnel.

If it were my machine, the first thing I'd do would be to install openssh-server on the box I want to connect to and then on my XP machine, I'd install Cygwin with the X server. Then, I'd forward the SSH port on my router and after starting cygwin's X server, SSH from the XP box to the Linux box (using either Cygwin or PuTTY), making sure I enabled X forwarding. At this point, you can start any program from the command line and its window will open on your XP box's screen. Alternatively, you can start gnome-panel to get the menus on your screen.


Once that was working, I might consider VNC if I felt it was worth it.

---

### Post by johnnyphive on 2007-05-15
> **mssever said:**
> I wouldn't recommend running XDMCP over the Internet since it's really insecure unless you use an SSH tunnel.

If it were my machine, the first thing I'd do would be to install openssh-server on the box I want to connect to and then on my XP machine, I'd install Cygwin with the X server. Then, I'd forward the SSH port on my router and after starting cygwin's X server, SSH from the XP box to the Linux box (using either Cygwin or PuTTY), making sure I enabled X forwarding. At this point, you can start any program from the command line and its window will open on your XP box's screen. Alternatively, you can start gnome-panel to get the menus on your screen.


Once that was working, I might consider VNC if I felt it was worth it.

Ok, i've got the ssh server up and running, and can access it remotely.  I installed Cygwin yesterday, but now sure if i did that correctly.  There was A LOT of stuff to choose to install / not install.  I went with the default selections and let it do it's thing.  Once it was done, I ran Cygwin, but all i got was a bash shell.  What do i do from here?

If i got ssh + cygwin working, why would i need VNC?  Should i be able to see my desktop without the VNC?

Thanks for the reply by the way, it's been like pulling teeth trying to get some help.

---

### Post by mssever on 2007-05-15
> **johnnyphive said:**
> Ok, i've got the ssh server up and running, and can access it remotely.  I installed Cygwin yesterday, but now sure if i did that correctly.  There was A LOT of stuff to choose to install / not install.  I went with the default selections and let it do it's thing.  Once it was done, I ran Cygwin, but all i got was a bash shell.  What do i do from here?

If i got ssh + cygwin working, why would i need VNC?  Should i be able to see my desktop without the VNC?

Thanks for the reply by the way, it's been like pulling teeth trying to get some help.

With Cygwin, you need to have X installed. I don't know whether it's the default. It's been a year since I've done this, so I don't remember the details. From the bash prompt, type ```
startx &
``` You should get a tray icon after a while and an xterm. If you get a command not found error from startx, then you don't have X installed.

Once you've got X running, SSH into your Linux box with X11 Forwarding enabled. PuTTY is a great Windows SSH program. Then, test it by typing gcalctool. Your Linux calculator should show up on your screen.

The difference between this and VNC is that VNC shows you your desktop and work area as if you were logged in locally. X forwarding makes remote windows open on your machine as if they were local windows. You'll either have to start your programs from the command line or run gnome-panel to get your menus.

---

### Post by johnnyphive on 2007-05-15
Ok, i reinstalled cygwin and when i type  "startx &" at the bash prompt this is what i get

bash-3.2$ startx &
[1] 3244
bash: startx: command not found
[1]+  Exit 127
bash-3.2$

When i reinstalled cygwin i made sure everything under X11 was selected for install.

Is there something i'm missing?

---

### Post by johnnyphive on 2007-05-15
Ok, just noticed something

should i be installing cygwin or cygwin/x ???

---

### Post by mssever on 2007-05-15
You might need cygwin/x, then. It's been so long since I've done this, that I don't remember the specifics. There's probably something on the cygwin website that tells how to get X working.

---

### Post by johnnyphive on 2007-05-16
every time i try to run "startx" in the cygwin bash, i get the following.

```

$ startx
C:\cygwin\usr\X11R6\bin\xinit.exe (4036): *** system shared memory version misma
tch detected - 0x2D1E009C/0x75BE0081.
This problem is probably due to using incompatible versions of the cygwin DLL.
Search for cygwin1.dll using the Windows Start->Find/Search facility
and delete all but the most recent version.  The most recent version *should*
reside in x:\cygwin\bin, where 'x' is the drive on which you have
installed the cygwin distribution.  Rebooting is also suggested if you
are unable to find another cygwin DLL.

```

I've already searched, and only 1 cygwin1.dll file lives on my computer and it is in the correct location.  I've also restarted the computer and still get this error.

What am I missing?

---

### Post by johnnyphive on 2007-05-16
Ok, i got startx working now, but now i have another problem.

Once i get ssh'ed in using putty none of my commands work.  Everything seems to be wanting to run on screen 10, while my xserver (cygwin) is running on 0

What now?

---

### Post by mssever on 2007-05-16
> **johnnyphive said:**
> Ok, i got startx working now, but now i have another problem.

Once i get ssh'ed in using putty none of my commands work.  Everything seems to be wanting to run on screen 10, while my xserver (cygwin) is running on 0

What now?

Did you configure PuTTY to forward X11 connections?

---

### Post by johnnyphive on 2007-05-16
yup

---

### Post by mssever on 2007-05-16
Hmmm... I don't remember having those kinds of problems, and my Windows machine isn't available right now for testing.

It's possible that $DISPLAY might be set incorrectly. What's its value? ```
echo $DISPLAY
``` It might be worthwhile to toggle its value, e.g., ```
export DISPLAY=":0.0"
```Here's another thought: What happens when you SSH from the xterm that comes up when you start Cygwin's X server? ```
ssh -o ForwardX11=yes hostname
```

---

### Post by johnnyphive on 2007-05-17
$ xclock
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: Can't open display: :0.0

this is from the bash shell in cygwin after using it (cygwin) to ssh in.

---

### Post by mssever on 2007-05-17
> **johnnyphive said:**
> $ xclock
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: Can't open display: :0.0

this is from the bash shell in cygwin after using it (cygwin) to ssh in.

If you've SSHed with X forwarding properly enabled, then I have no idea what your problem is. I never had those kinds of problems.

---

### Post by fanatik on 2007-05-18
you should leave the DISPLAY value alone, it is usually set correctly. it's refusing you on :0.0 as it should (probably) be localhost:10.0

So, start your X server on your windows box, then ssh in via putty with X11 forwarding enabled. **echo $DISPLAY** to show that it is set up correctly then **xclock &** to run xclock. it works for me!

---

