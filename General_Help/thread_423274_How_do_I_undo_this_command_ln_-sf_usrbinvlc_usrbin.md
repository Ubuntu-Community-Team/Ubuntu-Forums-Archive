---
title: "How do I undo this command? ln -sf /usr/bin/vlc /usr/bin/totem"
date: 2007-04-25
forum: General Help
---

### Post by SnowPunk98 on 2007-04-25
I wanted to make VLC play all audio/video except for MP3 and someone said to do ln -sf /usr/bin/vlc /usr/bin/totem however this makes it so I cannot use Totem.

So can someone tell me how to reverse this and then make it so VLC opens all video and audio, except MP3 which I want Rythembox to open?

---

### Post by leg on 2007-04-25
My first thought would be to go to the dir and remove the link.
```

cd /usr/bin
sudo rm /usr/bin totem

```
but I am worried about what the "f" optiojn has done. The force option in man states```
 -f, --force
              remove existing destination files

```which suggests that totem has been removed. You may need to re-install it.

---

### Post by SeanHodges on 2007-04-25
You'll need to reinstall totem, open a terminal and type:

sudo aptitude reinstall totem

That should get things back to how they were...

I don't know how to change a bunch of file types at once (though I'm sure theres a way), you can right-click on a video file and select "Properties" -> "Open With"... which should allow you to set your preferred application, see this thread for a more descriptive answer:

[http://ubuntuforums.org/showthread.php?t=285195&highlight=gnome+file+associations](http://ubuntuforums.org/showthread.php?t=285195&highlight=gnome+file+associations)

---

### Post by Metacarpal on 2007-04-25
to reverse:
```
sudo rm -f /usr/bin/totem && sudo aptitude reinstall totem
```

When you used -sf (instead of just -s) with ln, it replaced whatever it found in /usr/bin/totem with a symbolic link to /usr/bin/vlc.  (The "f" stands for "force")  "ln -sf" should only be used when you want to make a link to a file that doesn't exist yet, or when you want to overwrite an existing link.  Stick to "ln -s"

Then, go to one file of each type that you wish to associate with a program (ie, one .mpg, one .avi, etc).  Right-click that file, select Properties.  Then click on the Open With tab.  Click the radio button for the program you want to use for that file type, then Close.

Maybe there's an easier way to do that second part, but I don't know it.

---

### Post by SnowPunk98 on 2007-04-25
> **Metacarpal said:**
> to reverse:
```
sudo rm -f /usr/bin/totem && sudo aptitude reinstall totem
```


I did that and now when I try and launch totem it says "failed to execute child process "totem" (no such file or directory.)"

---

### Post by SnowPunk98 on 2007-04-29
bump

---

### Post by SeanHodges on 2007-04-29
This will ensure that totem is removed completely, and will install it again:

sudo aptitude remove totem
sudo aptitude install totem

after that completes, try running "totem" in command line...

I tried this on my machine after deleting /usr/bin/totem and it worked fine for me

---

### Post by SnowPunk98 on 2007-04-29
nope same thing, whats the command for totem, is it just totem?

---

### Post by SnowPunk98 on 2007-04-30
bump

---

### Post by SnowPunk98 on 2007-05-01
bump

---

