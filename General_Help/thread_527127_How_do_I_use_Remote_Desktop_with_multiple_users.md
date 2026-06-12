---
title: "How do I use Remote Desktop with multiple users?"
date: 2007-08-16
forum: General Help
---

### Post by sphim on 2007-08-16
I'm curious if there is a way to have people using remote desktop with different users at the same time. I would like it to be a way for me to use windows laptops as a thin client for an ubuntu server. Ideally, when you open a remote desktop connection, it would take you to ubuntu's login screen where different people can log in as different users. If this is possible, it think it would allow me to "run" ubuntu on my windows laptop without having to dual boot- because the ubuntu would really be running on a different computer, and the laptop is just viewing it. I hope its possible to run different users with different desktops, because I have a sneaking suspicion that this isn't exactly what remote destop is meant for. Thanks!

---

### Post by dannyboy79 on 2007-08-16
this is possible as far as I am aware. If you go into the System, Administration, Login Window, then there is a tab for remote. You just enable it. I am not sure what the various things are, like Plain or Same as local. At the bottom look for Configure XDCMP. then you can do more fine grained security. good luck
this allows you to remotely login to a new session. If you want to be able to login to a session that is already up and running. I use x11vnc for that. I don't have the x11vnc server running all the time but I always run a ssh server with public/private keys. Then I create a putty session (windows ssh client) and add a tunnel for port 5900 to my localhost:0, this will allow the vnc session to be encrypted within a ssh tunnel, which is way more secure. then from my windows, I open tightvncviewer, use localhost:0 and wahla, there's my ubuntu server sitting right in front of me secure and all.

good luck

---

### Post by sphim on 2007-08-16
Thank you! That's exactly what I wanted to hear. Although I don't really need to have this feature, do you know if that allows different people to be running different desktop sessions? If one person tried to connect while another person was already logged in, would it go strait to that other person's desktop session, or would it allow them to log in as a different user at the same time? (Does that make ANY sense?)

---

### Post by dannyboy79 on 2007-08-17
I don't use it (XDCMP) but I would imagine that since you're presented with a login screen, you're able to log into your own session not the session that's already going. I pointed out x11vnc only for times where you actually want to log into an X session that is already running.

---

