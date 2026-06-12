---
title: "ubuntu VNC"
date: 2015-06-21
forum: General Help
---

### Post by zaazz on 2015-06-21
Posting this in general because I haven't had a response from the ubuntu-mate community on the off-chance someone here might be able to answer this. I think it's more of a VNC question than pi anyway. Here's my post ([https://ubuntu-mate.community/t/new-to-pi-quick-vnc-question/1641):](https://ubuntu-mate.community/t/new-to-pi-quick-vnc-question/1641):)    Question: When I VNC to the pi I get a desktop on the VNC client but the TV connected to the pi stays at the login page.  First off, great build. I've been a long time fan of the ubuntu distro but I've never gotten around to purchasing a raspberry pi until I got the pie 2 two days ago.  So my question is about vnc4server. I was playing with tightvncserver but ended up trying out this tutorial instead. ([https://www.howtoforge.com/how-to-install-vnc-server-on-ubuntu-14.04](https://www.howtoforge.com/how-to-install-vnc-server-on-ubuntu-14.04)).  I've moved the pie into a new area connected to a TV and I'd rather not scratch this VNC build to get it working. I was wondering if I've set it up to start a new session with each new VNC connection or not and if I can change that so that when I VNC in I get connected to the desktop displayed on the TV.  Thanks in advance.

---

### Post by steeldriver on 2015-06-21
AFAIK that's how vnc4server / tightvncserver are supposed to work - if you want to connect to a 'real' desktop (aka 'desktop sharing') you should probably be using vino-server (for gnome-based desktops) or x11vnc (or one of their younger brethren such as x2go)

---

### Post by QIII on 2015-06-21
Hello!

So, you have the R Pi connected directly to the TV with the HDMI cable?

If so, then that is the R Pi's "monitor" and you will need to log in with a mouse and keyboard connected to the R Pi to open a desktop being output to the TV.  Once you have done that, you will have an existing desktop session to log in to from a remote machine.

You'll have to read up one how to log in to an existing session with whatever vnc server/client you are using.  I occasionally remote into my R Pi (having started a tighnvncserver instance) from another machine (using remmina).  But my R Pi usually runs headless, so I have to initiate a desktop session over SSH from the terminal with 

```
tightvncserver -geometry 1920x1080 -depth 24
```

That returns 

```
New 'X' desktop is raspberrypi:1
```

That means I have a running X session, although I can't see it from the terminal.  Using remmina over SSH, I then use the machine I am working from to remote into that desktop (via SSH, with key authentication) with xx.xx.xx.xx:1 to get the right session.  That's still using the R Pi headless.

You would want to remote in to the existing session you are already seeing on the TV.  If I recall correctly, VNC needs a running session on the server to log in to from the client.

---

### Post by zaazz on 2015-06-23
If I understand your post correctly the pi is running a session for the HDMI out to the TV. When I VNC I connect to a new session. I had hoped that there would be a way to switch to the session that has it's current output to the TV so I could work on that desktop displayed to the TV for playing media.

> **QIII said:**
> Hello!

So, you have the R Pi connected directly to the TV with the HDMI cable?

If so, then that is the R Pi's "monitor" and you will need to log in with a mouse and keyboard connected to the R Pi to open a desktop being output to the TV.  Once you have done that, you will have an existing desktop session to log in to from a remote machine.

You'll have to read up one how to log in to an existing session with whatever vnc server/client you are using.  I occasionally remote into my R Pi (having started a tighnvncserver instance) from another machine (using remmina).  But my R Pi usually runs headless, so I have to initiate a desktop session over SSH from the terminal with 

```
tightvncserver -geometry 1920x1080 -depth 24
```

That returns 

```
New 'X' desktop is raspberrypi:1
```

That means I have a running X session, although I can't see it from the terminal.  Using remmina over SSH, I then use the machine I am working from to remote into that desktop (via SSH, with key authentication) with xx.xx.xx.xx:1 to get the right session.  That's still using the R Pi headless.

You would want to remote in to the existing session you are already seeing on the TV.  If I recall correctly, VNC needs a running session on the server to log in to from the client.

---

