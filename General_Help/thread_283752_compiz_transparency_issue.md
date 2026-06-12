---
title: "compiz transparency issue"
date: 2006-10-24
forum: General Help
---

### Post by spvo on 2006-10-24
I have been using compiz for a while now, and I absolutely love it.  I have it set up so that inactive windows are slightly transparent.  However, this is REALLY freaking annoying when your trying to get work done in gimp.  Today I was trying to do slight adjustments using a few gimp filters (like gaussian blur).  But since gimp uses multiple windows every time I clicked on the settings window the preview window would fade.  Anyway, is there a way to tell compiz to never fade windows owned by gimp, but still do it for all the other ones?  Thanks.

John

---

### Post by dbott67 on 2006-10-24
Yes (I think).  Take a look at this [thread]("http://www.ubuntuforums.org/showpost.php?p=1598741&postcount=5") & the attached screenshots.

You'll need to change the 'window' title to reflect the name of the gimp window.  There is a command to identify the window in question... I'm not in front of my home computer right now, but I'll post the command when I get home.  Just replace the 'Gnome-terminal' with the name of the Gimp window.
```
c:Gimp-window-name:100
```


Oops... maybe I have to take a closer look.  I was thinnking about 'active window' & of course you want the inactive window.  It's got to be around there somewhere... Again, I'll take a look when I get home.

**_UPDATE #1_**

Okay the command to identify windows is 'xprop'.  Open a terminal & type:
```
xprop
``` or better yet
```
xprop | grep WM_CLASS | cut -d \" -f 4
```
The part you're looking for is **WM_CLASS(STRING) =** which is the value you enter after the c:
```
dbott@dapper:~$ xprop
_NET_WINDOW_DECOR(INTEGER) = 39945571, 5, 5, 21, 5, 0, 0, 36949, -12, -28, 0, 0, 12, 28, 0, 0, 40037, 0, -28, 0, 0, 596, 28, 12, 0, 36966, 0, -28, 14, 0, 14, 28, 608, 0, 37017, -12, 0, 0, 13, 12, 14, 0, 34, 40105, 0, 0, 0, 13, 596, 14, 12, 34, 37034, 0, 0, 14, 13, 14, 14, 608, 34, 40085, -12, 0, 0, 0, 12, 6, 0, 28, 40102, 0, 0, 14, 0, 14, 6, 608, 28
_NET_WM_ICON_GEOMETRY(CARDINAL) = 966, 776, 155, 24
XKLAVIER_STATE(INTEGER) = 0, 0
WM_STATE(WM_STATE):
                window state: Normal
                icon window: 0x0
_NET_FRAME_EXTENTS(CARDINAL) = 5, 5, 21, 5
_NET_FRAME_WINDOW(WINDOW): window id # 0x8007fd
_NET_WM_DESKTOP(CARDINAL) = 0
WM_HINTS(WM_HINTS):
                Client accepts input or input focus: True
                Initial state is Normal State.
                bitmap id # to use for icon: 0x3403f25
                bitmap id # of mask for icon: 0x3403f29
                window id # of group leader: 0x3400001
XdndAware(ATOM) = BITMAP
_MOTIF_DRAG_RECEIVER_INFO(_MOTIF_DRAG_RECEIVER_INFO) = 0x6c, 0x0, 0x5, 0xb7, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x39, 0x8, 0x10, 0x0, 0x0, 0x0
_NET_WM_ALLOWED_ACTIONS(ATOM) = _NET_WM_ACTION_MOVE, _NET_WM_ACTION_RESIZE, _NET_WM_ACTION_STICK, _NET_WM_ACTION_MINIMIZE, _NET_WM_ACTION_MAXIMIZE_HORZ, _NET_WM_ACTION_MAXIMIZE_VERT, _NET_WM_ACTION_FULLSCREEN, _NET_WM_ACTION_CLOSE, _NET_WM_ACTION_SHADE
_NET_WM_ICON(CARDINAL) = 32, 22, 4294967295, 
... <snip> ...
_NET_WM_WINDOW_TYPE(ATOM) = _NET_WM_WINDOW_TYPE_NORMAL
WM_WINDOW_ROLE(STRING) = "gimp-image-window"
_NET_WM_SYNC_REQUEST_COUNTER(CARDINAL) = 54540643
_NET_WM_USER_TIME(CARDINAL) = 2085390646
WM_CLIENT_LEADER(WINDOW): window id # 0x3400001
_NET_WM_PID(CARDINAL) = 26808
WM_LOCALE_NAME(STRING) = "en_CA.UTF-8"
WM_CLIENT_MACHINE(STRING) = "dapper"
WM_NORMAL_HINTS(WM_SIZE_HINTS):
                program specified minimum size: 1 by 1
                window gravity: NorthWest
WM_PROTOCOLS(ATOM): protocols  WM_DELETE_WINDOW, WM_TAKE_FOCUS, _NET_WM_PING, _NET_WM_SYNC_REQUEST
[COLOR="Red"]WM_CLASS(STRING) = "gimp", "Gimp"[/COLOR]
WM_ICON_NAME(STRING) = "Untitled-1.0 (RGB, 1 layer) 420x300"
_NET_WM_ICON_NAME(UTF8_STRING) = 0x55, 0x6e, 0x74, 0x69, 0x74, 0x6c, 0x65, 0x64, 0x2d, 0x31, 0x2e, 0x30, 0x20, 0x28, 0x52, 0x47, 0x42, 0x2c, 0x20, 0x31, 0x20, 0x6c, 0x61, 0x79, 0x65, 0x72, 0x29, 0x20, 0x34, 0x32, 0x30, 0x78, 0x33, 0x30, 0x30
WM_NAME(STRING) = "Untitled-1.0 (RGB, 1 layer) 420x300"
_NET_WM_NAME(UTF8_STRING) = 0x55, 0x6e, 0x74, 0x69, 0x74, 0x6c, 0x65, 0x64, 0x2d, 0x31, 0x2e, 0x30, 0x20, 0x28, 0x52, 0x47, 0x42, 0x2c, 0x20, 0x31, 0x20, 0x6c, 0x61, 0x79, 0x65, 0x72, 0x29, 0x20, 0x34, 0x32, 0x30, 0x78, 0x33, 0x30, 0x30
dbott@dapper:~$
```

In your case, you would enter
```
c:Gimp:100
```

Now, to figure out where to put the setting... back in a while... 

**_UPDATE #2_**

Okay... I'm back.  It appears as though the settings above only affect the active window.  However, I have found a great little resource here: [https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz](https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz)

There's a section on 'Trail Focus' [https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz#trailfocus](https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz#trailfocus) that allows you to configure settings on background windows & such.  I haven't played with it, but it look promising.

-Dave

---

### Post by HydroDiOxide on 2007-04-24
Sorry for the bump.

I'm using Feisty with Compiz and I was wondering how I can make my inactive windows slightly transparent. Got GL Desktop installed as well, but I don't seem to be able to set it from there.

Also, I was wondering how to use the blur effect found in the screenshots (terminal) [here]("http://www.gnome-look.org/content/show.php?content=45402&forumpage=1").

---

