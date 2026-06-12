---
title: "Jumpy Mouse"
date: 2008-04-28
forum: General Help
---

### Post by Kamenoitte on 2008-04-28
Dear Community,

I installed Hardy Heron yesterday and am now experiencing a befuddling problem.  If I move my mouse rapidly around the screen its motion appears smooth and accurate.  If I move my mouse slowly, however, it loses all accuracy and sort of jumps around.  This makes my experience unpleasant because I am constantly missing buttons, fields, menus, etc. when I slow down to approach them.

Here is an illustrative example.

If I slowly move my mouse like this:
[HTML]
          /
         /
        /
       /
      /
     /
    /
   /
  /
 /
/[/HTML]
my cursor appears to move like this:
[HTML]
           |--
           |
       /---|
      /
     | 
     |-\
        \ 
   |--\  |
   |   \-|
---|
[/HTML]


1. My first thought was that the surface was bad for an optical mouse, but I have used the surface with that mouse for years.  I also observed the same problem on a different surface, on a mouse pad designed for optical mice.

2. My second thought was that the mouse I use wasn't playing nice with Ubuntu.  I use a Razer Copperhead.  But I swapped in my old Logitech MX300 and observed exactly the same phenomenon.  Just for reference, here is the relevant section of my xorg.conf file:

```
Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option      "Name"          "Razer Copperhead"
    Option      "Vendor"        "Razer"
    Option      "CorePointer"
    Option      "Protocol"      "ExplorerPS/2"
    Option      "ZAxisMapping"  "4 5"
    Option      "Device"        "/dev/input/mice"
    Option      "Buttons"       "7"
    Option      "ZAxisMapping"  "6 7"
    Option      "ButtonMapping" "1 2 3 6 7"
    Option      "Resolution"    "2000" 
    Option      "SampleRate"    "1000Hz" 
EndSection
```

3. My third thought was that I could have a low acceleration threshold and be arbitrarily triggering a large acceleration, but I still see the problem when I have set acceleration to 0 and threshold to 10.

4. My fourth thought was that it could be a conflict with something on my motherboard: MSI P35 Platinum.  I disabled everything I didn't need in the BIOS, but the problem persists.


Please help me to solve this problem so I can actually enjoy my new OS.  Thank you.

---

### Post by GroteBozeWolf on 2008-05-01
Got the same problem! First it works normally, then it starts behaving weird. I installed the nvidia-glx drivers(i hoped that solved the problem of an unstable laptop). First i had the new drivers and i had no problems.

The mouse is working OK now, if it starts behaving weird, i'll post an update if the nvidia-glx-new drivers solve the problem.

---

### Post by jimv on 2008-12-08
Kind of a late reply, but try blowing off the laser lens on the bottom of the mouse.

---

### Post by 3startuna on 2009-05-02
MInes doing the same thing and I have a ball mouse. I was just abou to go buy an optical one. 

Thinking the hardware might be bad. 

Mine when I use the scroll wheel or whenever it feels like it, will start moving all over the screen and clicking stuff. It will move t the bottom of the screen and open up several trash can windows.then it will chill out, and when i try to move it it will either freeze and do nothing or behave normally.

When it freezes nothing works. unplug nope

 Alt+ ctrl +f1 then log in then exit works sometimes, alt+ctrl+backspace then log in sometimes works.

But most times nothing happens and I need to do a complete restart. Its really annoying me.

---

