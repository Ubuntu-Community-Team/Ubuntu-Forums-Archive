---
title: "&quot;Auto Adjusting ...&quot; window"
date: 2021-11-26
forum: General Help
---

### Post by rgirard1 on 2021-11-26
OS: Ubuntu 20.04.3 LTS

I do not have a microphone plugged into my desktop but I see that window "Auto Adjusting..." appear often and it blocks the view. I have pulseaudio re-installed. I tried the various solutions offered on Ubuntu Forums but no luck. Is there a way to **definitively** get rid of that window?

Thanks

---

### Post by dragonfly41 on 2021-11-26
Does this thread help ..

[https://askubuntu.com/questions/279407/how-to-disable-microphone-from-auto-adjusting-its-input-volume](https://askubuntu.com/questions/279407/how-to-disable-microphone-from-auto-adjusting-its-input-volume)

---

### Post by ActionParsnip on 2021-11-26
Does the system have a make and model?

---

### Post by rgirard1 on 2021-11-26
Thank you for the link to the tread. I went to the threadI tried the command line solution given ther but no luck. Next as the next proposed solution I installed "pavucontrol" and  ran it I set on the Configuration panel  for "Built-in audio the profile " Analog Stereo Output" i.e. a profile with no microphone. Also on the "Input Devices" panel  set the volume to zero (silence). We will see if this works.

---

### Post by rgirard1 on 2021-11-26
No, it is a system that my son has build several years ago. This problem is recent. Otherwise the system has run flawlessly for the last several years. I have 2 other desktops (one old and one quite recent) and 2 other laptops running  24/7 (doing numerical computations) under Ubuntu Linux as this one with no problems.

---

### Post by rgirard1 on 2021-11-27
The settings I implemented through "pavucontrol" as descrtibed in my previous post resulted in no changes: the "Auto Adjusting ..." window comes back. I do not know what to do next.  I saw there is another sound application "alsamixer". Can something be done to that "alsamixer" to make that window disappear? Thanks

---

### Post by rgirard1 on 2021-11-27
I just installed "alsamixergui" but there is nothing in there to set for the microphone input. Note again: I have no microphone plugged in to my Desktop. So why is the OS trying to adjust the microphone input level? Unless this "Auto Adjusting..." is for something else.

---

### Post by dragonfly41 on 2021-11-27
If you cannot beat it perhaps try making the window disappear?
To do this you need to have a script push the window elsewhere.
xdotool can drive window layers .. but if that does not work you can try
a more comprehensive automation tool. 
I use one (Actiona) quite often to orchestrate desktop views.

[P.S.]
Here is xdotool list of commands

[FONT=monospace][COLOR=#000000]```

$ xdotool
```[/COLOR]```

Usage: xdotool <cmd> <args>
Available commands:
  getactivewindow
  getwindowfocus
  getwindowname
  getwindowpid
  getwindowgeometry
  getdisplaygeometry
  search
  selectwindow
  help
  version
  behave
  behave_screen_edge
  click
  getmouselocation
  key
  keydown
  keyup
  mousedown
  mousemove
  mousemove_relative
  mouseup
  set_window
  type
  windowactivate
  windowfocus
  windowkill
  windowclose
  windowmap
  windowminimize
  windowmove
  windowraise
  windowreparent
  windowsize
  windowunmap
  set_num_desktops
  get_num_desktops
  set_desktop
  get_desktop
  set_desktop_for_window
  get_desktop_for_window
  get_desktop_viewport
  set_desktop_viewport
  exec
  sleep

```

And another source of ideas found here ...
[/FONT][https://www.codegrepper.com/code-examples/shell/stop+microphone+from+auto+adjusting+ubuntu](https://www.codegrepper.com/code-examples/shell/stop+microphone+from+auto+adjusting+ubuntu)

```

[FONT=monospace][COLOR=#000000]pacmd list-sources | grep name

```
[/COLOR]
[/FONT]

---

### Post by ajgreeny on 2021-11-27
I do not know **alsamixergui** but use command ***alsamixer*** in terminal.
This will open an ncurses view of all the inputs and playback devices, but in my case at least opens showing playback only.
Use Tab to move to inputs (ie, microphones) and you may see better what is available in your computer.

It may also be useful to see the output in terminal of command ***inxi -Fzx***

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

