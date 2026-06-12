---
title: "Workaround for Dialog Windows Too Big in 12.04.4LTS?"
date: 2014-03-04
forum: General Help
---

### Post by 2CV67 on 2014-03-04
Hi!
I know this is an old problem, covered in many threads & with numerous bug reports, including this one:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/760645](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/760645)

But I have just installed 12.04.4LTS on my wife's netbook & we are very irritated by the fact that many dialog windows (example - Save-as) open too big for the screen, so you can't get at the buttons at the bottom.

I know there are several every-single-time workarounds:
- Alt+Left-click > drag window up
- Alt+F7 > drag window up > Enter (to release hold)
- Maximise window

But really.... Every Single Time!!

So I would really like to find a once-for-all workaround.
And as 12.04LTS is LTS, I suppose many others would like it too?

I did find something here:
[http://askubuntu.com/questions/96375/why-are-my-file-selection-dialogs-so-big-how-do-i-make-them-smaller](http://askubuntu.com/questions/96375/why-are-my-file-selection-dialogs-so-big-how-do-i-make-them-smaller)

```
.config/gtk-2.0/gtkfilechooser.ini:GeometryWidth=1440

Removing that line (and the corresponding GeometryHeight) solved the problem for me.
```

But I don't seem to have that file or anything similar (do I?).

So - how can I, once-for-all, make dialog windows open with all buttons visible?

Thanks for any ideas!

---

### Post by varunendra on 2014-03-04
It exists on my default Ubuntu 12.04(.2) installation here, although the said value is different for me. I hope you are aware that files/directories whose names start with a dot (.) are hidden by default.

Does it return an error for you ? -
```
cat .config/gtk-2.0/gtkfilechooser.ini
```

---

### Post by 2CV67 on 2014-03-04
Yes, it does:
```
chris@netbk:~$ cat .config/gtk-2.0/gtkfilechooser.ini
cat: .config/gtk-2.0/gtkfilechooser.ini: No such file or directory
chris@netbk:~$ 
```

I am quite aware of how to see hidden files, but you are PERFECTLY right to bring up the point! 
Thanks!

I also ran a Nautilus search for *filechooser.ini with no result.

---

### Post by varunendra on 2014-03-04
Do you have a .config/gtk-2.0/ directory? If yes, you may try creating that file. It seems a profile preset for "Open File" dialogue box, containing just a few preset values.

Here's mine for reference -
```

[Filechooser Settings]
LastFolderUri=file:///home/varun/Desktop
LocationMode=path-bar
ShowHidden=true
ShowSizeColumn=true
GeometryX=0
GeometryY=0
[B]GeometryWidth=840
GeometryHeight=630[/B]
SortColumn=name
SortOrder=ascending

```

---

### Post by 2CV67 on 2014-03-05
> **varunendra said:**
> Do you have a .config/gtk-2.0/ directory?

No:
```
chris@netbk:~$ ls .config
autostart  gedit                 ibus             user-dirs.dirs
compiz-1   gnome-control-center  libreoffice      user-dirs.locale
dconf      gnome-disk-utility    nautilus
enchant    gnome-session         software-center
eog        goa-1.0               update-notifier
chris@netbk:~$
```

Not sure where to look next...

---

