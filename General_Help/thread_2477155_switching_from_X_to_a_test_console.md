---
title: "switching from X to a test console"
date: 2022-07-15
forum: General Help
---

### Post by Skaperen on 2022-07-15
while in X Windows one can press Ctrl+Alt+F1 (or F2 .. F6 or so) and X is disconnected from the physical console and (one of) the kernel's text console(s) become(s) active.  what i would like to know is how is the state that X is in is referred to.  **what terminology would this be referred to in X documentation?**

it is possible to run 2 or more instances of X Windows at the same time.  many years ago i would run 3 instances of X Windows in parallel on F10, F11, and F12.  i would always switch between them with Ctrl+Alt+F10 (or Ctrl+Alt+F11 or Ctrl+Alt+F12).  the instance of X i was switching away from could, in theory, see that i was switching away.  today, Xubuntu (and perhaps also Ubuntu) runs LightDM which can carry out the switch without any press of the keyboard.  both instances of X know it happens since they both need to act to carry out the details of making the switch happen.  this can be done with the command "dm-tool switch-to-user $username".  i'd like to know how the X servers get to know this.  i assume it is some kind of interrupt or signal but i don't know a way to trap or trace this.

also, it seems the Firefox web browser gets to know this, too.  it used to no act on it,such as when playing a YouTube video which would just keep on playing with no one watching.  recently, it was changed to pause the video.  i would like to know if there is a setting that can have it keep on playing without pausing when X does this.

when i am running *ffmpeg* to record the screen and i switch to viewing another user (which is always running a different X Windows server) the recording keeps running but all that is recorded is a black screen.  maybe capturing the screen uses a hardware buffer to do that.  so i may need to switch to using VNC to switch around with each user running an X-over-VNC server and me running a VNC client which will also do the switching.  as far as i am aware, sound has not been added to the VNC protocol.

---

