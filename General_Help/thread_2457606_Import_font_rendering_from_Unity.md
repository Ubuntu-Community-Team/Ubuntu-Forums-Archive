---
title: "Import font rendering from Unity?"
date: 2021-02-05
forum: General Help
---

### Post by username2758 on 2021-02-05
Hiya!

Going back from Ubuntu 20.04 to 16.04 LTS (Unity), I have noticed a significant improvement in font rendering clarity and sharpness, almost resembling that of Windows 10.

So my question is if it's possible to sort of "import" the font rendering settings from one Linux distribution to another? I want to get the exact same font rendering engine that is in Ubuntu 16.04 LTS.

Thanks!

---

### Post by grahammechanical on 2021-02-05
I doubt if font rendering settings have anything to do with it. Linux is under constant development. There have been changes to display managers. We are moving from the X-Server Window manager to a window manager based on the Wayland protocol. Then there are the tool kits used to create applications. I do not know what version of GTK was used in Ubuntu 16.04 but today Ubuntu is using GTK3 and in the future will move on to GTK4. I think that stuff like this will affect rendering.

Regards

---

### Post by username2758 on 2021-02-05
So you are suggesting font rendering sharpness has a lot more to do with the display manager rather than the font settings themselves?

That's what I've kind of been suspecting as well, even though I thought it had more to do with driver compatibility and temporal dithering etc than anything else.

---

### Post by Holger_Gehrke on 2021-02-05
Slight error in Terminology: the display manager has nothing to do with it. That's just the program that sets up the **display server** for a graphical login and after that's done starts the user's session. On a system using X11 the display server could be at fault, since it has the capability to render text. But most modern programs use one of the major tool kits - GTK or Qt - and those mostly do the rendering of all graphical elements themselves and just give the server a pre-rendered bitmap to display, which is one of the reasons for the development of Wayland which does away with all the things X11 can do but nobody uses anymore. For text rendering the tool kits in turn rely on a whole stack of other libraries - Pango, Harfbuzz, FriBidi, Fontconfig and Freetype - and any and all of those libraries are under constant development. So as you can see finding the culprit for what you perceive as a loss in quality of text-rendering is not an easy task.

Holger

---

### Post by username2758 on 2021-02-06
> **Holger_Gehrke said:**
> Slight error in Terminology: the display manager has nothing to do with it. That's just the program that sets up the **display server** for a graphical login and after that's done starts the user's session. On a system using X11 the display server could be at fault, since it has the capability to render text. But most modern programs use one of the major tool kits - GTK or Qt - and those mostly do the rendering of all graphical elements themselves and just give the server a pre-rendered bitmap to display, which is one of the reasons for the development of Wayland which does away with all the things X11 can do but nobody uses anymore. For text rendering the tool kits in turn rely on a whole stack of other libraries - Pango, Harfbuzz, FriBidi, Fontconfig and Freetype - and any and all of those libraries are under constant development. So as you can see finding the culprit for what you perceive as a loss in quality of text-rendering is not an easy task.

Holger

Thanks for providing further explanation on how font rendering works!

Unfortunately, Windows always seemed to have superior text rendering compared to Linux, and in my opinion Ubuntu with Unity is the only distro that comes close to the Microsoft product.

I really hope the great Linux community could work together to find an alternative to this. I think it's common sense to say that most Linux users are the more "tech-savvy" people, therefore offering higher levels of font-rendering quality reducing eye-strain as a result. Not saying Windows is unimportant, but perhaps Linux should care more.

---

### Post by dinkidonk on 2021-02-06
Font rendering and fonts have changed a lot in various Linux distro's - IMO mostly improving. I used to have issues with font rendering in Linux, letters looked like turds on a row. I copied all the fonts from Windows 7 to my Linux distro and disabled everything about anti alias, hinting and what not, and that was a huge improvement - close to a Windows experience. So fonts them selves can make a huge difference in readability and you might try to copy the fonts you use in Ubuntudiddelidoo 16 to 20 and see if that improves the experience.

Another thing to mind is the monitor, settings and fonts that look good on one monitor may look very poor on another monitor. On my old monitor (Samsung 206BW) I could not use the default Ubuntastic settings, had to disable all anti alias and so on. On my new(er) monitor (Dell U2719D) the default settings look great, using the settings from my old monitor is a complete no-go!

---

