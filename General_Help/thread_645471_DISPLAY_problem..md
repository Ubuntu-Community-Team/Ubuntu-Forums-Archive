---
title: "DISPLAY problem."
date: 2007-12-20
forum: General Help
---

### Post by dchurch24 on 2007-12-20
Hi all,

For some reason when I VNC into my box and try to start Firefox or Nautilus, or anything to be honest, I get the following error:

GTK Warning - cannot open display.

I have done 'echo $DISPLAY' and it says 'localhost'

I changed this the IP of the machine: [IPAddress]:0.0
then exported the DISPLAY variable, but now I get "Client is not authorised to connect to server"

From what I have found by searching, this should have worked, but doesn't.

I'm still pretty much a newbie, and as such am now stuck.

I'm sure this is simple to put right for someone, if someone could point me in the right direction it would really be appreciated.

Thanks in advance,

---

### Post by aJayRoo on 2007-12-20
Usually manually setting the display variable shouldn't be necessary but since I am no expert on VNC I won't get into that. What is important to know is that if you are manually setting the DISPLAY variable then you will also need to tell the X server on your machine to accepts connections from the remote machine. This is done with the xhost command:
```
xhost + ip_address_of_remote_machine
```
type that into a terminal and try again. You will need to do this every time you log in I think. Hope that helps.

---

### Post by dchurch24 on 2007-12-20
Thanks for that.

Sadly it's made no difference.

It's such a pain - yesterday it worked fine, today (with no changes from myself - I haven't touched the machine since) it doesn't.

The machine I'm VNCed into is the same as the machine I want the display on, if that makes any difference.

---

### Post by aJayRoo on 2007-12-20
OK, just one thing then... I thought VNC was a graphical system so it would not work without a display? Sorry if I am being condescending but it sounds a lot like you are using SSH to connect to a remote machine and are trying to launch graphical apps from the command line, if this is the case then there is a simple solution. The ssh command has an X forwarding switch '-X' which when used will forward the display to your machine, you will not have to set the DISPLAY variable on the remote machine or use xhost on the local machine as this is all taken care of in a secure manner. How are you connecting to your remote machine, which app or command are you using to do it?

---

### Post by dchurch24 on 2007-12-20
Ahh - sorry, didn't make myself clear.

I've VNCed into the box, and when I do that, I get a terminal box show up.

From there I can start progams that need a graphical interface - Firefox for instance.

When I try to start firefox it tells me that it can't open the display.

The whole time I am in the VNC session - I'm not connected to the machine via SSH (although I can be if this helps in any way).

So it seems that it can display, because it is already displaying the terminal window (with titlebar, etc...).

---

### Post by aJayRoo on 2007-12-20
OK I'm still a bit unsure about your situation. I'm finding it hard to visualise what is going on when you have this terminal. Which application are you using for VNC, I mean what is its name or what command do you use to start it etc.?

---

### Post by dchurch24 on 2007-12-20
Hi,

I'm using TightVNC. When I open a session it defaults to just showing the terminal window, and from there I can start apllications "firefox &" etc...

But when I do that today, I just get the "Can't open display" message.  I'm not trying to send the display to a different IP, just want it to open on the same machine.

---

### Post by aJayRoo on 2007-12-20
OK it seems strange that it worked before and yet today it fails! Anyhow, I forgot one crucial piece of information. If the local machine is running the gnome desktop environment then you will also need to alter a setting in the login window settings. Go to System -> Administration -> Login Window then click on the security tab and uncheck the tickbox for Deny TCP connections to Xserver. Then logout and back in again (or restart xserver I'm not sure which) and use the xhost command I mentioned earlier. This is the procedure that needs to be used if you are manually forwarding a display connection.

---

