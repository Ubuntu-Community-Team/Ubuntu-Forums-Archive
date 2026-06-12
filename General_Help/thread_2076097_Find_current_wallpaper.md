---
title: "Find current wallpaper"
date: 2012-10-25
forum: General Help
---

### Post by antalg on 2012-10-25
Is there any way of getting the current wallpaper from the terminal? And by current wallpaper I don't mean the source image, which you can get through
```
gsettings get org.gnome.desktop.background picture-uri
``` but instead the *actual* shown image that matches your screen resolution.

*(If I'm being vague, just tell me and I'll elaborate some more.)*

Thanks in advance!
*antalg*

---

### Post by Paddy Landau on 2012-10-25
AFAIK, you cannot do that directly.

But, once you have your file, you can get the tiling or stretch method from picture-options (from gsettings), the opacity from picture-opacity (also from gsettings), and the resolution of your screen using xrandr.

You can tile, resize and change opacity with ImageMagick.

Would that answer your question?

---

### Post by antalg on 2012-10-25
That is pretty much what I wanted to avoid doing, as writing code for each of the scaling methods didn't really strike my fancy. But I guess that there might not be a better way of doing it.

I thought that the scaled background image has to be stored somewhere, but maybe my intuition is just dead wrong.

Edit: I've always wondered, what does picture-opacity actually do? I haven't seen any difference when playing that value.

---

### Post by Paddy Landau on 2012-10-25
> **antalg said:**
> That is pretty much what I wanted to avoid doing, as writing code for each of the scaling methods didn't really strike my fancy. But I guess that there might not be a better way of doing it.
The code would already have been written. Perhaps it is a module that you can call? If you contact the Gnome team (I am presuming that it is Gnome), you may be able to find out how to call the code.

> **antalg said:**
> I thought that the scaled background image has to be stored somewhere, but maybe my intuition is just dead wrong.
Good point! I have searched [FONT=Lucida Console]/tmp[/FONT], [FONT=Lucida Console]/run[/FONT] and [FONT=Lucida Console]/var/cache[/FONT] but found nothing.

> **antalg said:**
> I've always wondered, what does picture-opacity actually do? I haven't seen any difference when playing that value.
Opacity means the opposite of transparency. If you make the picture partially-transparent (or partially-opaque), you can see what lies underneath it. I have found it makes a difference when using the Cube.

---

### Post by antalg on 2012-10-26
Sigh...I ended up coding ImageMagick rescaling methods for all 6 scaling methods.

I guess there is some people wondering why in the world I would want to do this.

Here's the thing. I want the panel to be disguised as the wallpaper (I want the 24 upper pixels of the background to be the background for the panel, see the attached screenshot). After editing the needed css file I was up and running, but I wasn't happy about having to crop every panel image manually. So I made a script that worked with perfectly sized wallpapers. Then I got bored of having to crop the wallpapers all the time. And thus I am here today, hands dirty with ugly code and sleep deprived. Anyway, I got everything working nicely in the end. However it took 150+ lines of ugly code, rather than ~10 lines of clean code.

I think I'll leave this as unsolved for now, as I'm still interested in whether this elusive "desktop background image" exists somewhere.

Big thanks for the help, even though my main question stands unanswered.
*antalg*

---

### Post by Paddy Landau on 2012-10-26
> **antalg said:**
> I want the panel to be disguised as the wallpaper  (I want the 24 upper pixels of the background to be the background for  the panel, see the attached screenshot).
Uh… OK… Why didn't you just make the panel transparent?

---

### Post by antalg on 2012-10-27
> **Paddy Landau said:**
> Uh… OK… Why didn't you just make the panel transparent?

Because when I first came up with this trick, there was a bug with unity that caused shadows of texts to remain in the panel. But it seems this has been fixed (which I didn't even bother to test). I don't know if I should feel sad about this or not... So, in the end I did all that work in vain. Oh well...thanks for that painful realization. It was well needed.

*antalg, a.k.a. the one facepalming because of his own stupidity*

---

### Post by Paddy Landau on 2012-10-27
> **antalg said:**
> antalg, a.k.a. the one facepalming because of his own stupidity
LOL, it is a lesson that I have learned: ask for what you want before presenting what you think is the best solution. Doing that has often led me to a simpler solution than the one I had thought of.

Anyway, I'm glad it's fixed. Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by call4hemant on 2013-02-12
gconftool -g /desktop/gnome/background/picture_filename

---

