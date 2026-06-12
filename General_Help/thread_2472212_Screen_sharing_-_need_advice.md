---
title: "Screen sharing - need advice"
date: 2022-02-21
forum: General Help
---

### Post by jakudo on 2022-02-21
Hello,

I've tried to manage the screen sharing to be able to connect to my Ubuntu (latest update) notebook from iMac (macOS Monterey).
I've enabled the screen sharing in Setting, then I read somewhere that I have to install vino, so I did and it still doesn't work. I tried to connect to this:
vnc://TM-Ubuntu.local (as it is mentioned in the setting in Ubuntu)
vnc://192.168.1.12
vnc?//192.168.1.12:5900 (read somewhere that adding the port might help, also read somewhere port 5901)
...and no luck at all.
I've always received this message:

[ATTACH=CONFIG]290078[/ATTACH]

Any idea what I'm doing wrong?

I can connect via SSH with no problem at all, but the screen sharing would be better.

Thanks,
Jakub

---

### Post by TheFu on 2022-02-21
Use **x2go**, not vnc.  There is a server and a client.  The clients run on Linux, Windows, and MacOS. I know the Windows and Linux clients are solid. A few years ago, I used the Windows one daily, all day, from Windows.  The server is only for Linux, but it doesn't care if it is running on real hardware or inside a VM.  Just be certain to have ssh working before you  setup x2go. ssh authentication and tunneling is used, so x2go is secure for use over the internet.

Also, don't use Gnome3+ as a DE. Use any other DE - kde, xfce, lxqt, mate, whatever, just not the Gnome3+ ones.
And lastly, choose X11, not Wayland. I know xorg/X11 works. I think Wayland might work, but I don't use it and it is common for screen capture tools not to work with Wayland.

I should say - x2go feels 2-3x faster than rdp or VNC.

---

### Post by ActionParsnip on 2022-02-21
What are you wanting to do on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to do

---

### Post by TheFu on 2022-02-21
> **ActionParsnip said:**
> What are you wanting to do on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to do

Sharing the screen with others.  x2go allows people on the same LAN to see what is happening on the desktop.

If the goal is just to allow others to see a full desktop, just use meet.jit.si.  That can share an entire desktop or just 1 window with anyone on the internet using a modern browser that supports webRTC.  My LUG uses meet.jit.si for all our meetings the last 2 yrs. It is free, but very democratic (which can be good and bad). We routinely have 20 attendees. Much easier to use than commercial (aka Zoom).

There are many other ways to record a desktop and share that video/audio with others later.

---

### Post by jakudo on 2022-02-21
I'm not a Linux pro, just playing with it (learning stuff etc). However, since the notebook with linux is in my rack and I use it primary as server for HomeBridge, It is complicated for me to try other things on it (the Rack is hidden and not well accessible). So I wanted to be able to share screen to my primary computer (iMac), so when I want to try something, it would be much easier for me.
So I need to access it only from local network and only on by one iMac. Nothing special.

Thanks for the advices you posted.

---

### Post by HermanAB on 2022-02-22
If you install Xquartz on the Mac (and XFCE on the Linux machine), then you can run graphical applications over SSH and have the screens pop up on the Mac.  Since SSH is already working, that would be the easiest.

---

### Post by ActionParsnip on 2022-02-22
> **jakudo said:**
> I'm not a Linux pro, just playing with it (learning stuff etc). However, since the notebook with linux is in my rack and I use it primary as server for HomeBridge, It is complicated for me to try other things on it (the Rack is hidden and not well accessible). So I wanted to be able to share screen to my primary computer (iMac), so when I want to try something, it would be much easier for me.
So I need to access it only from local network and only on by one iMac. Nothing special.

Thanks for the advices you posted.

Looks like you access homebridge via a web browser. Is that right please?

---

### Post by jakudo on 2022-02-22
@HermanAB - will check it, thanks

@ActionParsnip - yes, when I want to access HomeBridge, I do that via web browser (with no problem). However, when I want to test or learn something on Ubuntu or start an update or something, I cannot do that remotely (only via SSH, which is sometimes very complicated for me :) )

---

### Post by ActionParsnip on 2022-02-22
> **jakudo said:**
> @HermanAB - will check it, thanks

@ActionParsnip - yes, when I want to access HomeBridge, I do that via web browser (with no problem). However, when I want to test or learn something on Ubuntu or start an update or something, I cannot do that remotely (only via SSH, which is sometimes very complicated for me :) )

So... You are going to VNC (or similar) to a server... To open a Web browser to access [http://localhost](http://localhost)

Now, think about it.

It's a Web server listening on port 80 or 443 or whatever it uses. You can access this from any system on your network using the remote system IP on the same port. Try it. Does it connect?

---

### Post by jakudo on 2022-02-22
heh, no :) When I want to log in to HomeBridge, I use Safari /google chrome on my iMac and connect there with no problem.
What I need is to be able to connect to shared screen to the laptop, so I can do other stuff there (when I'm trying to install some apps, or want to update Ubuntu etc). I don't need to access the HomeBridge VNC :)

---

### Post by TheFu on 2022-02-22
> **HermanAB said:**
> If you install Xquartz on the Mac (and XFCE on the Linux machine), then you can run graphical applications over SSH and have the screens pop up on the Mac.  Since SSH is already working, that would be the easiest.

+100!

```
$ ssh -X remote-user@remote-ip  program-to-run  options to program
```
You get the fully integrated "program-to-run" being displayed on your Mac in a normal window.  Copy/paste works between windows.

So, when I want to open a terminal on a different system, I use:
```
$ ssh -X thefu@192.168.1.250  xterm -sb &
```
Well, that's one way. It is the general answer for GUI programs.  Obviously, change the IP or DNS-name, username, program to whatever is needed.

Terminals are a little special and it is possible to have the terminal start the remote X/Windows session so that any other programs run from that remote terminal are all sent through the same ssh-tunnel.
```
$ xterm -geometry 80x22+0+630 $XTERM_OPTS -e ssh -X regulus &
```

regulus is the remote DNS-name.  Because my usernames are the same on both machines, it isn't required.  Crazy flexible.  The remote and local program windows are fully integrated. In fact, the only way to know that it is running on a different system is in the window titlebar.  I do server management all day long. This is how I work.

---

### Post by ActionParsnip on 2022-02-22
You can run updates from the terminal using
```

sudo apt update
sudo apt -y full-upgrade

```

---

### Post by TheFu on 2022-02-22
> **jakudo said:**
> @HermanAB - will check it, thanks

@ActionParsnip - yes, when I want to access HomeBridge, I do that via web browser (with no problem). However, when I want to test or learn something on Ubuntu or start an update or something, I cannot do that remotely (only via SSH, which is sometimes very complicated for me :) )

Sorry to say this, but you need to learn server management from a CLI interface. There's no other option. Get used to it. The learning curve is steep, but trying to stick with only GUI methods gets you 20% of the options/commands. The other 80% is where the power all lies.  If you are new to Linux, you'll need to start learning CLI commands from the beginning. Learning things out of order wastes so much time, since Linux skills build on prior skills.  Start with chapter 1, then 2, 3, 4,  ... you can't skip to chapter 200 without chapter 1-50 first. For normal users: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

There are web-GUI tools for server management, but I find them much too limiting and just another attack vector.  You won't listen, so "Cockpit" is probably the tool you should use today.  **sudo apt install cockpit** - I think that is how to install it. [https://cockpit-project.org/running](https://cockpit-project.org/running) I played with it for about 20 minutes and decided it was too cumbersome.  WebGUIs are a security nightmare.  By the time an admin learns to properly secure a webGUI, they've either already been hacked or don't need it anymore.  I suppose if an experienced admin sets up the webgui and properly locks down access, then junior admins could make use if it. The problem with that is they'll never learn the more advanced methods and techniques using it and will always be stuck with junior admin skills (and salary).

BTW, I have no clue what HomeBridge is.

---

