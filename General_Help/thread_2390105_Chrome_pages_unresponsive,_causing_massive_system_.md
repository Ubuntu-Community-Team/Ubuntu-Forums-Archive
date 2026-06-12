---
title: "Chrome pages unresponsive, causing massive system slowdown"
date: 2018-04-25
forum: General Help
---

### Post by MgFrobozz on 2018-04-25
This has been a problem with chrome for about a year now, usually occurring when I open a page with a lot of advertising. As the page is loading, the mouse cursor becomes less and less responsive, sometimes grinding completely to a halt, and the page goes gray. At the same time, the disk access led comes on and stays on. Most of the time, a dialog will appear, but it takes 20-30 seconds to show the dialog contents, which report that the page is unresponsive. If I'm lucky, I can _very_ slowly move the cursor, pull up my console window, and issue "killall chrome". Running the killall usually causes the disk access led to go out, and the system becomes responsive again. About 25% of the time, killall doesn't work, and I have to locate the remaining chrome processes (using "ps aux | grep chrome") and kill them by process id instead. 

The chrome page-hang occurs about twice an hour. Rarely (once every few weeks), the system is completely unresponsive to mouse or keyboard when it happens, and I'm unable to ssh in and kill chrome because the system is so busy. I then have to cold-reboot it.

I've tried restricting chrome to only cpu 2 and 3, by doing this in ~/.config/gnome-panel/launchers/taskset.desktop ...

```

    [Desktop Entry]
    ...
    Exec=taskset 0xc /usr/bin/google-chrome-stable %U
    ...
    [Desktop Action new-window]
    ...
    Exec=taskset 0xc /usr/bin/google-chrome-stable
    ...
    [Desktop Action new-private-window]
    ...
    Exec=taskset 0xc /usr/bin/google-chrome-stable --incognito

```

... but it doesn't seem to help.

I also get frequent webgl-related "aw, snap" messages, but clicking "ignore" seems to work (none of the suggestions for fixing webgl that I've found have eliminated this).

Thanks in advance for any suggestions.

Setup:
chrome Version 64.0.3282.186 (Official Build) (64-bit)
Ubuntu 16.04.4 LTS

---

### Post by kerry_s on 2018-04-25
chrome://flags/

top 2 enable

---

### Post by MgFrobozz on 2018-05-18
Thanks for the reply. I'm assuming this is a flag that controls which cpu(s) is(are) used ... could you tell me the name of the flag?

---

