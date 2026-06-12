---
title: "Xgl/Compiz Questions"
date: 2006-09-03
forum: General Help
---

### Post by user1397 on 2006-09-03
I just got done setting up xgl/compiz on my dapper desktop, using the fglrx driver in the repos, but i got a few questions about it.

1) Why is it called xgl/compiz?  I mean, what part of the effects is xgl and what part is compiz?

2) How do I move my 4 workspaces in a 3D manner, with my mouse as i've seen in some videos? (i mean something like this: [http://en.wikipedia.org/wiki/Image:Xgl_cube.png](http://en.wikipedia.org/wiki/Image:Xgl_cube.png) )

---

### Post by PsycloneD on 2006-09-03
1) No idea.

2) If you run:
```
sudo gconf-editor
```
you will be able to change the settings of different Compiz plugins such as Cube and Rotate (which requires Cube). After you've typed that in Terminal, click on "apps" then "compiz". You'll see all of the installed plugins. They all have individual settings, so it's really easy to do. I suggest using Quinndebs plugins. They do a great job of improving the existing plugins as well as adding new ones. But to answer your question more completely, the settings you'll want to change are that of 'Cube' and 'Rotate'. So have fun with THAT. I'll post some helpful resources in a little while. EDIT: here they are:

[http://en.opensuse.org/Compiz#Available_plugins]("http://en.opensuse.org/Compiz#Available_plugins")
[http://gentoo-wiki.com/Compiz]("http://gentoo-wiki.com/Compiz")

I know it's not for Ubuntu, but it still gives explanations of each plugin. That's all that matters.

I happen to have some questions. I saw this video a few days ago and it really got me excited. I, however, cannot figure out how some of these things are done. I've thoroughly checked all of the settings available in gconf-editor, and I can't find what I'm missing. I have Quinndebs installed. Enough jibber-jabber, here's the video.

[Compiz/XGL video]("http://www.youtube.com/watch?v=lawkc3jH3ws")

What I want to know is 1) [found on video at 0:10] how this person can zoom out so far when rotating the cube. The Skydome seems more visible and the cube seems further into the screen and 2) [found on video at 0:20] how  you get that wavy bending resize option. I've checked the resize options and nothing really does what's in this video.

Also, I used to have the active window be focused while the windows and desktop in back of it dimmed to a black shadow. Here's an image of what I mean:

[Faded background]("http://img243.imageshack.us/img243/4456/scaletozoombl1.png")

So if anybody can help me out, that would be great!

---

### Post by user1397 on 2006-09-03
> **PsycloneD said:**
> 1) No idea.

2) If you run:
```
sudo gconf-editor
``` you will be able to change the settings of different Compiz plugins such as Cube and Rotate (which requires Cube). After you've typed that in Terminal, click on "apps" then "compiz". You'll see all of the installed plugins. They all have individual settings, so it's really easy to do. I suggest using Quinndebs plugins. They do a great job of improving the existing plugins as well as adding new ones. But to answer your question more completely, the settings you'll want to change are that of 'Cube' and 'Rotate'. So have fun with THAT. I'll post some helpful resources in a little while. EDIT: here they are:

[http://en.opensuse.org/Compiz#Available_plugins](http://en.opensuse.org/Compiz#Available_plugins)
[http://gentoo-wiki.com/Compiz](http://gentoo-wiki.com/Compiz)

I know it's not for Ubuntu, but it still gives explanations of each plugin. That's all that matters.thanks!

---

