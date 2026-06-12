---
title: "Fractional scaling: actually changing screen resolution?"
date: 2022-03-02
forum: General Help
---

### Post by username2758 on 2022-03-02
Hiya,

My laptop has a 15" Full-HD screen so it's kinda hard to read in native 1920x1080 resolution.

The problem is when I try to do fractional scaling to 125%, Ubuntu 20.04.4 (on Wayland) is actually changing the screen resolution to 1536x864 according to "inxi -G" command, losing considerable sharpness.

Is that how fractional scaling is supposed to work? It's the first time I use it.

```
$ inxi -G
Graphics:
Device-1: AMD driver: amdgpu v: kernel 
Display: wayland server: X.Org 1.20.13 driver: amdgpu 
resolution: 1920x1080~60Hz 
OpenGL: renderer: AMD RENOIR (DRM 3.41.0 5.13.0-30-generic LLVM 12.0.0) 
v: 4.6 Mesa 21.2.6
```

---

### Post by #&amp;thj^% on 2022-03-02
This question is kind of a double edge sword, I'm assuming of course your using ubuntu 21.10, because you don't mention it here.
1st is Fractional scaling enabled?
For X11 Display Server:
```
 gsettings set org.gnome.mutter experimental-features “[‘x11-randr-fractional-scaling’]”
```

For Wayland Display Server:
```
gsettings set org.gnome.mutter experimental-features “[‘scale-monitor-framebuffer’]”
```

Having done that, go back to display settings by navigating to Settings > Display.

There should now be a variety of scales to choose from.
The following command should help you reset the changes:
```
gsettings reset org.gnome.mutter experimental features
```
These settings are meant to be applied for HighDPI displays. This means that fractional scaling options will not be available if you are using low resolutions. For example, a resolution scale of 800×600.

Ubuntu does not automatically find the correct fractional scaling value for you, rather it is up to the users to find it themselves. In most cases, 125% or 1.25x gets the job done. However, in the end, it all depends on your personal preference.
Also worth mentioning Font DPI is worth a look as well.

---

### Post by username2758 on 2022-03-02
I don't know. I just fiddled around the screen options under 'Display' settings (screenshot below).

I am using Ubuntu 20.04.4 as already said in my first post, but the same behavior happens in Ubuntu 21.10 (screen resolution goes to 1536x864 after applying fractional scaling of 125%).

I tried your suggested command "gsettings set org.gnome.mutter experimental-features &#8220;[&#8216;scale-monitor-framebuffer&#8217;]&#8221;" and it did nothing. What does that do?

How do I change Font DPI in Ubuntu?

---

### Post by #&amp;thj^% on 2022-03-02
have a look: [https://vitux.com/how-to-change-text-size-in-ubuntu/](https://vitux.com/how-to-change-text-size-in-ubuntu/)
BTW I saw nothing wrong in your screenshot.

---

### Post by username2758 on 2022-03-02
Thanks for the article!

Yeah. When I change the fractional scaling to 125% from the screenshot, the resolution changes to 1536x864. Just wanted to show you what display settings I meant.

How do I use your suggested command?
```
gsettings set org.gnome.mutter experimental-features &#8220;[&#8216;scale-monitor-framebuffer&#8217;]&#8221;
```

I am on 20.04.4 and Wayland.

---

### Post by #&amp;thj^% on 2022-03-02
Not my command, best check with>> This can be done by navigating to Fonts > Scaling Factor in Gnome Tweaks, or using gsettings.
I'm not yet a wayland fan so your mileage may vary.
EDIT: best to see what dpi you are now using with:
```
xdpyinfo | grep dots
  resolution:    96x96 dots per inch

```
Is what mine shows.

---

### Post by username2758 on 2022-03-04
It shows the same value on my laptop too:
```
$ xdpyinfo | grep dots
  resolution:    96x96 dots per inch
```
But my question: is fractional scaling really supposed to work by actually changing the screen resolution or not?

Like I said I've never used fractional scaling before.

---

### Post by #&amp;thj^% on 2022-03-05
The two work hand in hand.
> But my question: is fractional scaling really supposed to work by actually changing the screen resolution or not?

Probably not how you would think it should, Fractional scaling and font scaling, but the clarity was never sharp.
There's some needed work to hone it, for a better experience
More of the same here: [https://www.dedoimedo.com/computers/linux-mint-cinnamon-hd-scaling.html](https://www.dedoimedo.com/computers/linux-mint-cinnamon-hd-scaling.html).

---

### Post by mkay581 on 2022-03-05
Yes. The currrent experience is not so great. Great article! Thanks

---

