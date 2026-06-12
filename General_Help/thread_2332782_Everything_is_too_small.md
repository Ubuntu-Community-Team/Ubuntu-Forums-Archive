---
title: "Everything is too small"
date: 2016-08-03
forum: General Help
---

### Post by napostrophe on 2016-08-03
Hello, I have been setting up Kubuntu on my laptop and have run into something really annoying; everything is too small.
This is very likely to be caused by the fact that it is a 1440p screen which is only 12.5" and Kubuntu expects the physical size to be much larger. 
Is there any way to fix this without making everything look disgusting? (I found one way but it only worked on a few apps and it caused texts to be blurry and everything looked generally bad)

And before anyone says anything, I would just like to say that I do NOT mean font size, I mean the size of literally everything in Kubuntu.

Any help would be greatly appreciated

---

### Post by QIII on 2016-08-03
Hello!

Your OS does not know, much less care, about the physical size of the screen.  It goes by resolution.  It something at 1440p is 10 pixels wide, it's ten pixels wide on a 12 inch screen and a 36 inch screen.

What was the method you tried previously so people don't try to cover the same ground?

---

### Post by napostrophe on 2016-08-03
> **QIII said:**
> Hello!

Your OS does not know, much less care, about the physical size of the screen.  It goes by resolution.  It something at 1440p is 10 pixels wide, it's ten pixels wide on a 12 inch screen and a 36 inch screen.

What was the method you tried previously so people don't try to cover the same ground?

I have tried changing the font size in settings (which did have a positive effect on the system settings, konsole, and other similar apps, but did not effect things like chrome, which is the biggest thing i want to get fixed) and I tried going into the "Scale Display" option under Display Settings>Display Configuration>Scale Display which had no effect on chrome either.

I also tried just making the resolution 1080p instead of 1440p but that just made it look disgusting.

---

### Post by QIII on 2016-08-03
On my cell so I can't look, but Chrome does allow you to change the size at which content is displayed.

---

### Post by napostrophe on 2016-08-03
> **QIII said:**
> On my cell so I can't look, but Chrome does allow you to change the size at which content is displayed.

It does but that only changes font size, it doesn't effect the overall interface and the titlebar

---

### Post by papibe on 2016-08-03
Some desktops have tools to make adjustments to the size of titles bars and menus, so it can work better on a high dpi display.

Vanilla Ubuntu, uses Unity, and it can adjust those settings on 'Displays'. Since it is based on Gnome, I imagine the latter have a setting too.

As far as I can tell, KDE does not have such feature, although you may try this: [Kubuntu and HiDPI Screen]("https://www.girialam.com/2016/02/kubuntu-and-hidpi-screen/").

However, KDE plasma 5 have something:
```
System Settings &#8594; Display and Monitor &#8594; Display Configuration &#8594; Scale Display
```
then logout and login again.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by QIII on 2016-08-03
By that, do you mean the window decorations or elements of the Chrome GUI inside?

---

### Post by napostrophe on 2016-08-03
Here is a picture to show you what I mean. 
The Size of everything on the right is fine while everything on the left (chrome) is too small. Additionally, I have manually adjusted the top bar and the dock to be the correct sizes, so if any changes need to be made system wide I can fix things.

---

### Post by QIII on 2016-08-03
Again:  What about that is too small?  The content?  The window decorations, the Ubuntu menu elements?

We have to establish something here so we are on the same sheet.  My monitors are 24".  Yours is 12.  That means that the physical area of yours is roughly a quarter of mine.  My monitors are 1080p, yours 1440p.  That means your pixel density is probably slightly greater than 4x mine.  An item on your screen will be physically about one fourth the size of mine.  There is nothing we can do about that.

From what I see in your images, the scale looks fine.  If it is physically too small, I'm not going to be able to tell.

---

### Post by napostrophe on 2016-08-03
The interface is too small, specifically the tabs, search bar, the buttons to close, maximize, and minimize the window. That whole jam.

What i have realized is that I need to what Kubuntu thinks my DPI is, how to do that I don't know.

---

### Post by papibe on 2016-08-03
> **napostrophe said:**
> The interface is too small, specifically the tabs, search bar, the buttons to close, maximize, and minimize the window. That whole jam.
Some of these are related to the ability of the desktop to adapt to high dpi display as mention on post 6.

Regarding Chrome. If you are not committed to that browser, Firefox can scale its interface, bars, tabs, and fonts on them, by setting the parameter
```
layout.css.devPixelsPerPx
```
to a higher value. I believe '2' would work well.

There's an extension that does exactly that, if you don't want to set it up by yourself: [Zoom Menu Elements]("https://addons.mozilla.org/en-US/firefox/addon/zoom-menu-elements/").

Let us know if that works for you.
Regards.

---

### Post by QIII on 2016-08-04
System Settings --> Display and Monitor 

Resolution is in the lower half of the window towards the left.

Remember that *DPI* is a characteristic of printers.  Pixel density is a function of *resolution* and the screen's physical size.

---

### Post by napostrophe on 2016-08-04
> **QIII said:**
> System Settings --> Display and Monitor 

Resolution is in the lower half of the window towards the left.

Remember that *DPI* is a characteristic of printers.  Pixel density is a function of *resolution* and the screen's physical size.

That may be so, but just changing the screen resolution will make everything look generally disgusting as it doesn't really scale so much as multiply pixel size, causing a need for anti-aliasing which would be a system setting, but if the computer thinks that the resolution is lower than it actually is no anti-aliasing will happen.

---

### Post by QIII on 2016-08-04
Anti-aliasing or no, there will still be compromises between the output from the video card and what the monitor physically displays.  The pixel density will remain constant.

Kubuntu is the most flexible of the family in terms of GUI configuration.  There are all kinds of possibilities for changing the behavior of window decorations, title bars, etc.

Individual applications, however, may not be so generous.

---

### Post by SeijiSensei on 2016-08-04
> **QIII said:**
> Individual applications, however, may not be so generous.
Especially ones like Chrome that are not written for KDE and the Qt toolkit.

OP, have you tried changing the GTK settings in KDE?  On my 14.04 machine running KDE4 it's under Application Appearance in System Settings. One thing you can do is make the default font for GTK applications larger than the KDE default.

---

