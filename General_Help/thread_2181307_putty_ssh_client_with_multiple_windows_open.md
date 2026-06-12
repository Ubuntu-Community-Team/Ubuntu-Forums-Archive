---
title: "putty ssh client with multiple windows open"
date: 2013-10-17
forum: General Help
---

### Post by tony-ynotsoftware on 2013-10-17
i use putty ssh client. works great. but how can i run multiple windows or sessions?

---

### Post by The Cog on 2013-10-17
I suggest you use screen. Screen is an application that you start after logging into the server. It runs on the server, but allows you to start extra command-prompt sessions within itself, and to switch between them. It also has the advantage that if the SSH breaks, screen is still there and all the command prompts inside it carry on. You can reconnect you ssh (or connect from elsewhere if you like) and run the command "screen -r" to reconnect to screen and resume using the sessions. I often use it when doing remote admin such as upgrades because an unexpected network failure won't interrupt the upgrade.

---

### Post by Doug S on 2013-10-17
On my PuTTY client, if I right click in the top of the window a menu opens with "Duplicate Session" as an option that will create another session with the same host. Alternatively, you can just start another occurrence of putty and connect that way. I typically have 3 or 4 PuTTY sessions open at any given time.

I do not use "screen", as The Cog recommended, but I do see it highly recommended often.

---

### Post by Lars Noodén on 2013-10-17
screen is very useful and there is a lot of documentation for its many functions.  If you are just getting started then you might look at [tmux](http://sourceforge.net/p/tmux/tmux-code/ci/master/tree/FAQ) instead, like screen it is also in the repository.  It's a cleaner rewrite of screen and has all the capabilities you would need in a terminal multiplexer.  Though I started out on screen, I find myself using only tmux of late.  Look at the manual page for the list of default key bindings.  With tmux you can have multiple windows within a session or even split a window into panes.

---

### Post by The Cog on 2013-10-17
Sounds interesting. I'll have to take tmux for a test drive.

---

### Post by Newbunto on 2013-12-02
> **tony-ynotsoftware said:**
> i use putty ssh client. works great. but how can i run multiple windows or sessions?

It depends on how you are starting PuTTY.

I start it from the launcher bar and I use right-mouse-click to control exactly what happens (new window and session, which remote host). To do this you need to set up a .desktop file.

So how are you starting PuTTY and what does your .desktop file look like, if relevant?

---

### Post by pbrane on 2013-12-03
A nice alternative to puTTY is Gnome Connection Manager. Available in the repos. It offers tabbed multiple sessions. You can also sent commands to multiple devices simultaneously.

---

