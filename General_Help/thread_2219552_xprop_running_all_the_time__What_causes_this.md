---
title: "xprop running all the time?  What causes this?"
date: 2014-04-24
forum: General Help
---

### Post by zombienerd1 on 2014-04-24
I am running a relatively fresh install of Xubuntu 13.10  x64

In my task manager, I noticed the following command running all the time:

xprop -id 0x0140004e -spy


I was wondering what would spawn this process...  xwininfo was no help...

Output of xwininfo -id 0x0140004e -all

```
xwininfo: Window id: 0x140004e (has no name)


  Root window id: 0x153 (the root window) (has no name)
  Parent window id: 0x1400048 (has no name)
     1 child:
     0x4200000 (has no name): ()  1680x924+0+63  +0+63


  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1680
  Height: 1050
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -1680+0  -1680-0  +0-0
  -geometry 1680x1050+0+0


  Bit gravity: NorthWestGravity
  Window gravity: NorthWestGravity
  Backing-store hint: NotUseful
  Backing-planes to be preserved: 0xffffffff
  Backing pixel: 0
  Save-unders: No


  Someone wants these events:
      KeyPress
      KeyRelease
      ButtonPress
      ButtonRelease
      EnterWindow
      LeaveWindow
      PointerMotion
      ButtonMotion
      KeymapState
      Exposure
      StructureNotify
      SubstructureNotify
      FocusChange
      PropertyChange
  Do not propagate these events:
  Override redirection?: No


  No window manager hints defined
  Window manager hints:
      Process id: (unknown)


  No normal window size hints defined
  No zoom window size hints defined


  No window shape defined
  No border shape defined



```

I'm still relatively new with linux, and I don't like having processes run if I don't need them...  I'll admit the -spy is what caught my attention, but since reading the MAN page I don't think anyone is spying on me :)

---

### Post by antofthy on 2014-07-21
> **zombienerd1 said:**
> I am running a relatively fresh install of Xubuntu 13.10  x64

In my task manager, I noticed the following command running all the time:

xprop -id 0x0140004e -spy

I was wondering what would spawn this process...  xwininfo was no help...

...

I'm still relatively new with linux, and I don't like having processes run if I don't need them...  I'll admit the -spy is what caught my attention, but since reading the MAN page I don't think anyone is spying on me :)

The "xprop -spy" basically watches for any changes to that window and reports them to its stdout.  Presumably the parent process is a script that is using it to watch for changes.

  I do not know if it is in a I/O or signal wait state (no process time until something happens), or it wakes up a 'polls' the window for changes every so often.  The manual is highly deficent on details, and usage information.

---

### Post by ian-weisser on 2014-07-22
Try looking at a process tree to see what launched xprop.
```
ps -ejH
```

Or, if you know the PID of xprop, you can use /proc. The parent PID is the fourth field of /proc/$PID/stat.
```
cat /proc/$PID/stat | cut -d' ' -f4
```

---

