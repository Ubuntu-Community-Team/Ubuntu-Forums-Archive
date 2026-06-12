---
title: "Ubuntu screenshot question"
date: 2012-12-31
forum: General Help
---

### Post by KingNeil on 2012-12-31
If I use CTRL+ALT+F6 to switch to a new screen, and use "startx -- :1" to launch a new desktop....

... is it true, that it's not possible to take a screenshot on the other screen (as in, the default, CTRL+ALT+F7)... without switching back to it...?

Because, I've tried using an automated script to take a screenshot of the other screen, while I've switched to the new one, and it doesn't work... 

Is there any way around this... like... is there any way to be switched over to the new screen, but actually take a screen on the other one, without having to switch to it?

Note.. when I say "screen", I'm not talking about dual monitors.. only one physical monitor is being used here, on my laptop...

---

### Post by sudodus on 2012-12-31
I know that there have been other threads about this, and I have not seen any solution. Of course there might still be solutions.

What do you want to do? Why can't you run the screensaving command from the current screen?

Have you tried gimp, that can capture a screen? And run it with a proper --display option. It might work.

Have you tried to run in a virtual machine and use the host to take the screenshot. I know this works.

---

### Post by KingNeil on 2012-12-31
> **sudodus said:**
> 
What do you want to do? Why can't you run the screensaving command from the current screen?


Well, you can surely imagine why someone might want to do this. For example, if you had full-screen programs running on multiple screens, you might want to take periodic screenshots of each, without having to keep manually switching between them.. 

But really.. I just want to know if this is possible or not... I've heard that X only allows one output per physical monitor.. so... it's not possible....

On that note.. I would also like to ask... if you had a VirtualBox program open, and you minimised it on the host computer, could the VirtualBox guest take screenshots, while minimised...? Or... would that also fall under the single core, root "One X output per screen" rule, that I mentioned in the previous paragraph of this post?

> **sudodus said:**
> 
Have you tried gimp, that can capture a screen? And run it with a proper --display option. It might work.


No.. haven't tried that. How would I do that?

---

### Post by sudodus on 2012-12-31
> **KingNeil said:**
> Well, you can surely imagine why someone might want to do this. For example, if you had full-screen programs running on multiple screens, you might want to take periodic screenshots of each, without having to keep manually switching between them.. 

But really.. I just want to know if this is possible or not... I've heard that X only allows one output per physical monitor.. so... it's not possible....

On that note.. I would also like to ask... if you had a VirtualBox program open, and you minimised it on the host computer, could the VirtualBox guest take screenshots, while minimised...? Or... would that also fall under the single core, root "One X output per screen" rule, that I mentioned in the previous paragraph of this post?



No.. haven't tried that. How would I do that?

I don't know about that trick with VirtualBox, but it wouldn't be too difficult to try :-)
--
You mean with Gimp?

Run gimp from a text window (or via ssh from another computer) while you send the graphics to the graphics desktop environment with using the --display option.

```
echo $DISPLAY
``` in a window will print its display number. Typically it is :0 

You might succeed with batch mode.

---

### Post by KingNeil on 2013-01-04
By the way, I figured out that you can indeed minimise VirtualBox, and it still takes a screenshot, and in fact, you can minimise VirtualBox, and switch screens on the host machine, and it still takes a screenshot...

I guess it just doesn't like taking a screenshot of the main screen, but it can actually take one from within VirtualBox, regardless of which screen the host computer is switched to... V. weird... Anyway, I've decided to just use VirtualBox in order to sort this issue of taking multiple screenshots from different screens, so yeah... 

I never tried the GIMP thing, because I'm still not precisely sure what your instructions are actually telling me to do. Regardless, I decided to just use VirtualBox.

---

### Post by sudodus on 2013-01-04
> **KingNeil said:**
> ...

I never tried the GIMP thing, because I'm still not precisely sure what your instructions are actually telling me to do. Regardless, I decided to just use VirtualBox.

I think it is a good choice :-)

---

