---
title: "alt maximizes and grabs current window"
date: 2008-04-28
forum: General Help
---

### Post by jettjunker on 2008-04-28
Odd problem.. I'm not sure what to make of it.  It wasn't doing this last night, and I don't recall making any changes.

More detail:
Pressing alt, and nothing else, maximizes and grabs (makes it so moving the mouse moves the window) the current window.  This only happens with compiz as my window manager -- metacity works fine.  I don't have any special commands in the "General Options -> Commands(tab)" section of ccsm.

Things I tried:
1) Rebooting.
2) Disabling the various plugins a few at a time then trying again.  I went through them all, without the behavior stopping.
3) setting metacity as WM, then:
mv ~/.config/compiz ~/.config compizBak
then, set compiz back as WM.  Problem persisted (and I was surprised to find that most of my compiz settings remained... I didn't want to tinker with gconf-editor, since I never had before [for compiz])
4) xev, then pressing alt gives (cropping what came before):
```
PropertyNotify event, serial 26, synthetic NO, window 0x4600001,
    atom 0x1d8 (_NET_WM_ICON_GEOMETRY), time 2454624, state PropertyNewValue

PropertyNotify event, serial 30, synthetic NO, window 0x4600001,
    atom 0x1c4 (_COMPIZ_WINDOW_DECOR), time 2454660, state PropertyNewValue

PropertyNotify event, serial 31, synthetic NO, window 0x4600001,
    atom 0x1c4 (_COMPIZ_WINDOW_DECOR), time 2454690, state PropertyNewValue

FocusOut event, serial 31, synthetic NO, window 0x4600001,
    mode NotifyGrab, detail NotifyAncestor

ConfigureNotify event, serial 31, synthetic NO, window 0x4600001,
    event 0x4600001, window 0x4600001, (5,24), width 178, height 178,
    border_width 2, above 0x260029a, override NO

PropertyNotify event, serial 31, synthetic NO, window 0x4600001,
    atom 0x124 (_NET_WM_STATE), time 2455893, state PropertyNewValue

ConfigureNotify event, serial 31, synthetic NO, window 0x4600001,
    event 0x4600001, window 0x4600001, (0,24), width 1276, height 771,
    border_width 2, above 0x38002ca, override NO

Expose event, serial 31, synthetic NO, window 0x4600001,
    (0,0), width 1276, height 10, count 3

Expose event, serial 31, synthetic NO, window 0x4600001,
    (0,10), width 10, height 58, count 2

Expose event, serial 31, synthetic NO, window 0x4600001,
    (68,10), width 1208, height 58, count 1

Expose event, serial 31, synthetic NO, window 0x4600001,
    (0,68), width 1276, height 703, count 0

PropertyNotify event, serial 31, synthetic NO, window 0x4600001,
    atom 0x190 (_NET_FRAME_EXTENTS), time 2455901, state PropertyNewValue

ConfigureNotify event, serial 31, synthetic YES, window 0x4600001,
    event 0x4600001, window 0x4600001, (0,24), width 1276, height 771,
    border_width 2, above 0x38002ca, override NO

ConfigureNotify event, serial 31, synthetic YES, window 0x4600001,
    event 0x4600001, window 0x4600001, (0,24), width 1276, height 771,
    border_width 2, above 0x38002ca, override NO

PropertyNotify event, serial 32, synthetic NO, window 0x4600001,
    atom 0x1c4 (_COMPIZ_WINDOW_DECOR), time 2456101, state PropertyNewValue
```

Any ideas?  It's really annoying since so many shortcuts use alt.

EDIT1: perhaps related problem... a few times now my computer has locked up in that the keyboard and trackpad stopped working (except the icons for brightness showed up for those buttons, without actually changing the brightness).  But, even while locked up like that gkrellm continues to display updated system data.  Might not be a compiz thing after all.

EDIT2: Oh my, stupid mistake.  I copied over sever config files from an old installation a few days ago, one of which was ~/.xmodmap for a different machine that remaped my f7 and f10 keys. (or, more precisely, mapped something new to them).  The problem must have been around since then, but I just must have never hit alt to find out.  I'll make a new thread, in a different forum, if the EDIT problem persists.

---

