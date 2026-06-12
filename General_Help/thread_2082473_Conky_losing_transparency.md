---
title: "Conky losing transparency"
date: 2012-11-09
forum: General Help
---

### Post by CrucifiedEgo on 2012-11-09
Experiencing a strange issue with conky -- hope this is the right forum.  If i use any kind of transparency in .conkyrc, it starts off fine, but will suddenly lose the transparency and go to a white background. If i kill the process and restart it's fine for a few minutes.  Usually I can get it to turn white by clicking on the desktop, minimizing the terminal window I ran it from, etc. I can't seem to figure out the cause -- google hasn't been much help.  Nothing in the output from Conky -DD seems to show that it knows anything about it, it just has the normal updates.  Where should I begin looking?

---

### Post by QIII on 2012-11-09
Are you using old school pseudo-transparency or real transparency?

---

### Post by CrucifiedEgo on 2012-11-09
> **QIII said:**
> Are you using old school pseudo-transparency or real transparency?

TBH, not 100% sure how I'd tell.  I haven't used conky in a couple of years.  Relevant snippets from .conkyrc...

```

# Window specifications #

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

```

---

### Post by timgood on 2012-11-09
This worked for me - thanks to VinDSL for the pointers...

```
####
## Create 'own_window' type. Makes Conky behave like other panels.
#
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
####
## Some distros require the following lines for true transparency.
#
# own_window_argb_visual yes
# own_window_argb_value 255
```

I had to uncomment the last two lines to get true transparency.

Hope this helps.

---

### Post by stinkeye on 2012-11-09
timgood's config should fix.
Quantal doesn't seem to like 
```
own_window_type **override**
```

---

### Post by CrucifiedEgo on 2012-11-09
> **stinkeye said:**
> timgood's config should fix.
Quantal doesn't seem to like 
```
own_window_type **override**
```

This works.  It leaves me with a bit of a line around the conky window, but I can deal with that for now.  Thanks!

---

### Post by stinkeye on 2012-11-09
> **CrucifiedEgo said:**
> This works.  It leaves me with a bit of a line around the conky window, but I can deal with that for now.  Thanks!
```
sudo apt-get install compizconfig-settings-manager
```

Enter ccsm in the dash.

In the Window decoration plugin, change the shadow windows box to read...
```
(any) & !(class=Conky)
```

---

### Post by HiImTye on 2012-11-10
**override** hasn't worked well for a few releases, I had to switch to **normal** in 11.10 or it didn't work for me, not that it makes any sort of difference to me either way

---

### Post by stinkeye on 2012-11-10
> **HiImTye said:**
> **override** hasn't worked well for a few releases, I had to switch to **normal** in 11.10 or it didn't work for me, not that it makes any sort of difference to me either way
I think it may be a gfx driver issue as it only affects
```
own_window_type override
```
when used with
```
own_window_transparent yes
```

I always use own_window_type normal except for 1 conky.
own_window_type override allows it to be placed under the unity panel.
It doesn't use transparency so displays fine.

---

### Post by HiImTye on 2012-11-10
> **stinkeye said:**
> own_window_type override allows it to be placed under the unity panel.
It doesn't use transparency so displays fine.
I use GnomeShell, so it isn't an issue for me ;), but I suspect that you're right, regarding transparency. I think I discovered that before, but all my conky windows sit in front of my wallpaper on the desktop, so transparency is a necessity, or they look silly

---

### Post by timgood on 2012-11-10
> **CrucifiedEgo said:**
> This works.  It leaves me with a bit of a line around the conky window, but I can deal with that for now.  Thanks!

Try to uncomment the lines at the bottom of my config and see what happens. I needed to do that to get rid of the line. Now my conky works flawlessly.

own_window_argb_visual yes
own_window_argb_value 255

---

### Post by AlexDonald on 2012-11-12
> **stinkeye said:**
> ```
sudo apt-get install compizconfig-settings-manager
```

Enter ccsm in the dash.

In the Window decoration plugin, change the shadow windows box to read...
```
(any) & !(class=Conky)
```

If you don't want to install CCSM, you can use the dconf-editor which I believe is installed by default.

Open dconf-editor from the dash,

Navigate to org > compiz > profiles > unity > plugins > decor

Change the "shadow-match" field from
```
any
```
to
```
(any) & !(class=Conky)
```

---

### Post by quyvuong00 on 2013-10-17
> **timgood said:**
> Try to uncomment the lines at the bottom of my config and see what happens. I needed to do that to get rid of the line. Now my conky works flawlessly.

own_window_argb_visual yes
own_window_argb_value 255

i'm using ubuntu 13.10. 
after follow this, it worked for me. Thanks

---

