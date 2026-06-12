---
title: "Shutdown after logout"
date: 2007-05-01
forum: General Help
---

### Post by truptrup on 2007-05-01
This probably has a very simple answer but
Is it possible to shutdown the pc after i logout. When i exit mythtv it logs me out but i want it to shutdown the pc is the possible any way?

---

### Post by HunterK on 2007-05-01
Does it log you out of the GUI right to a command line screen?  If its still at the GUI login, there should be a button on the bottom left with all of the options.

---

### Post by truptrup on 2007-05-01
> **HunterK said:**
> Does it log you out of the GUI right to a command line screen?  If its still at the GUI login, there should be a button on the bottom left with all of the options.

It takes me to the gui but im working with a remote so i was hoping i could have it shutdown when i logout. I would need to hookup a mouse to shutdown taht way or maybe there is a script i could change to make it shutdown instead of logout.

---

### Post by Titus A Duxass on 2007-05-02
You can add a "button" to the main Mythtv screen labelled "Shutdown".
Take a look on the mythtv forums (google "mythtv talk") and search for menu editing.

---

### Post by superm1 on 2007-05-02
Either that or configure mythtv to use the option that would shut the system down in mythfrontend.  You just need to provide it a command to do on mythtv exit.  Say "sudo shutdown" or something to that effect.

Note you will need to set up sudo properly to allow this command to run without asking for a password.

---

### Post by wjston on 2007-05-02
> **truptrup said:**
> This probably has a very simple answer but
Is it possible to shutdown the pc after i logout. When i exit mythtv it logs me out but i want it to shutdown the pc is the possible any way?

I wrote a howto on shutting down the computer in mythtv  at this URL:
[http://ubuntuforums.org/showthread.php?t=351184&highlight=shutdown+button+%2B+mythtv](http://ubuntuforums.org/showthread.php?t=351184&highlight=shutdown+button+%2B+mythtv)

It has worked for me in Edgy. The only problem I've had is if I reboot instead of shutting down, my system stops with a kernel panic warning. I just power the system off by holding in the power button, and then I restart and everything is good to go. 

Hope this works for you.

---

