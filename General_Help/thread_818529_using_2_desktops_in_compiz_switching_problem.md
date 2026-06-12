---
title: "using 2 desktops in compiz switching problem"
date: 2008-06-04
forum: General Help
---

### Post by alwiap on 2008-06-04
Hi,

I'm using 2 workspaces with Compiz, and I have rotate cube enabled etc. 

When I go from one desktop to the other (example: I use expose and select something off of workspace 2 when I'm currently on workspace 1), I get a black flickering and it's really annoying. Or, if I drag a window from workspace 1 to 2 or vice versa, same problem.  I don't have this issue when I use 3 or more workspaces, only with 2.  

a) does anyone else have this problem? 

and 

b) can it be resolved easily or is it just a video card issue? 

FYI, my video card is a 7800GT and my processor is an Opteron 146 OC'd a bit.  Thanks!

---

### Post by Forlong on 2008-06-04
Are you on GNOME?

If so, what's the output of
```
gconftool-2 -g /apps/compiz/general/allscreens/options/active_plugins
```

---

### Post by alwiap on 2008-06-04
> **Forlong said:**
> Are you on GNOME?

If so, what's the output of
```
gconftool-2 -g /apps/compiz/general/allscreens/options/active_plugins
```

Hi Forlong, here is the output:

```
[place,winrules,imgjpeg,vpswitch,zoom,neg,extrawm,text,resize,move,svg,mousepoll,session,workarounds,core,firepaint,decoration,wobbly,water,dbus,regex,shift,png,resizeinfo,video,animation,fade,cube,showmouse,rotate,cubecaps,scale,trailfocus,scalefilter,expo,ezoom,scaleaddon,switcher]

```

Also, maybe it has something to do with the acceleration of the cube?

EDIT:  And yes, I am using Gnome.

---

### Post by Forlong on 2008-06-04
Switch from Cube to the **Wall** plugin.

Using Cube with two desktops results in a flat plane. Behind that plane is the black root window, which will be more visible (briefly) in that particular case.

---

### Post by alwiap on 2008-06-04
> **Forlong said:**
> Switch from Cube to the **Wall** plugin.

Using Cube with two desktops results in a flat plane. Behind that plane is the black root window, which will be more visible (briefly) in that particular case.

ok that works, albeit I can't use the cube anymore :(

thanks so much!

---

### Post by Forlong on 2008-06-04
What do you want me to say? :)

I already explained why you get that, with two desktops and Cube enabled.
I'm sorry, but you either have to live with it or change to Wall -- it's up to you what's more important.


P.S. if it's just the black that's bothering you, go to the **Appereance** tab of the **Desktop Cube** plugin and enable the **Skydome** -- then choose a colour that fits your wallpaper.

---

### Post by alwiap on 2008-06-04
> **Forlong said:**
> What do you want me to say? :)

I already explained why you get that, with two desktops and Cube enabled.
I'm sorry, but you either have to live with it or change to Wall -- it's up to you what's more important.


P.S. if it's just the black that's bothering you, go to the **Appereance** tab of the **Desktop Cube** plugin and enable the **Skydome** -- then choose a colour that fits your wallpaper.

Hi again,

Thanks for your help again, I'll just leave it as is, the black flickering is annoying enough that it's worth it to not use the cube.  One more question though, now when I switch workspaces, I have that thing in the middle come up briefly that shows which desktop I'm on (I believe it's default with Ubuntu), can I get rid of that?

---

### Post by alwiap on 2008-06-04
By the way, just so you know what I'm talking about, the attached picture is the thing I want to get rid of.

---

### Post by Forlong on 2008-06-04
In the **Desktop Wall** plugin, go to the **Viewport Switch Preview** tab and disable **Show Viewport Switch Preview**

---

### Post by alwiap on 2008-06-04
> **Forlong said:**
> In the **Desktop Wall** plugin, go to the **Viewport Switch Preview** tab and disable **Show Viewport Switch Preview**

thank you so much!!!

---

