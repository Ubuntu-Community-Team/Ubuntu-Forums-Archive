---
title: "Ubuntu or Kubuntu"
date: 2007-07-21
forum: General Help
---

### Post by Sandwich on 2007-07-21
I'm not sure on which one to choose. I tried both out, and I have gathered that Ubuntu is a much easier system to use and that Kubuntu doesn't like my computer (It shows that by refusing to boot sometimes). I'll mostly be using the computer for internet browsing/ 3D design/ photo manipulation and music.....and videos. Any advice would be helpful.
Thanks.

---

### Post by strabes on 2007-07-21
It's 100% preference. You can run QT apps in gnome and GTK/gnome apps in KDE so there's not really a limitation there.

Here is my completely unbiased comparison of the two: KDE is more powerful, has more options/preferences, and doesn't have a windows-like registry editor. (gconf-editor) Gnome is simpler and reminds me of OS X without all the eye candy because it seems to assume the user is a dummy and doesn't really know what he/she is doing.

Here's a wikipedia article comparing several X desktop environments: [http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

Some people say that kubuntu isn't a very good KDE distribution and that if you want to use KDE you should use PClinuxOS or openSUSE.

Anyway, if you want to try kde out (and you're using gnome), just do ```
sudo aptitude install kubuntu-desktop
```

This will install all the packages that come with kubuntu so you can just log out of gnome and log into kde via the session menu, to try it out. Make sure you use "aptitude" and not "apt-get" for this task because aptitude will let you remove kubuntu-desktop much easier than apt-get because it's better with dependency issues and other stuff that I don't really know.

In my opinion, amarok is by far the best music management software available in linux. The GIMP is the best image manipulation program. VLC is the best movie player. I don't do any 3d design but I hear blender is good...? Those are my recommendations.

---

### Post by Sandwich on 2007-07-21
Blender FTW!!!! lol
..I was recomended Sabayon linux. Do you know if that's any good?
Thanks.

---

### Post by strabes on 2007-07-21
It's KDE based. It comes on a DVD so it takes forever to download unless you get the mini version which in my opinion kind of sucked when I tried it last month.

---

### Post by Sandwich on 2007-07-21
That's what I'm downloading right now...I'll see how I like it and then I might download the DVD.
...Do you know if PClinuxOS is 64-bit? Because there's only one download option on their site.

---

### Post by strabes on 2007-07-21
I really have no idea. I've never used PCLinuxOS before. That would be a good question for #ubuntu.

---

