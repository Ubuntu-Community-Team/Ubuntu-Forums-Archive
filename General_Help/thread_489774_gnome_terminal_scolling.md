---
title: "gnome terminal scolling"
date: 2007-07-01
forum: General Help
---

### Post by morphodone on 2007-07-01
In Konsole you have the option to scroll up or down one line at a time with shift + up-arrow.

Is there a way to do this in the gnome terminal?

I only know the command to scroll up or down one page at a time.  shift + pageUp

thanks

---

### Post by Brucevdk on 2007-07-02
I Googled around a bit and found a thread on the GNOME Support forums:

[LIST]
[*][April 26, 2006 -- GNOME Support Forums: gnome-terminal scolling line-by-line]("http://gnomesupport.org/forums/viewtopic.php?p=51225")
[/LIST]
[QUOTE="und0"]
The scroll line-by-line was a Gentoo patch never accepted upstream and that seems isn't included any more. 
[/QUOTE]

And he points to the following bug report:
[LIST]
[*][GNOME Bugzilla: Bug 118967 &#8211; single line scrolling with "Shift-ArrowUp/ArrowDown" and mouse scroll wheel]("http://bugzilla.gnome.org/show_bug.cgi?id=118967")
[/LIST]
Note that this report is from August 3, 2003 though there's a lot of activity in the commentary section (last comment is from April 29, 2007. You might be able to apply [the patch]("http://bugzilla.gnome.org/attachment.cgi?id=71739") found in the attachments and compile gnome-terminal yourself.

If anybody else has some more information or knows of an "easier" workaround, don't hesitate to share it.

---

### Post by chili555 on 2007-07-02
You might also pipe your command through *less* which allows you to scroll back and forth with the arrow keys. An example:```
cat /etc/X11/xorg.conf | less
```

---

### Post by bodhi.zazen on 2007-07-02
Well, I never counted the lines ...

But, you can scroll up and down with the up arrows, and mouse wheel.

You can also enable the scrollbar and drag it up and down.

---

### Post by hugoheden on 2008-05-12
> **morphodone said:**
> In Konsole you have the option to scroll up or down one line at a time with shift + up-arrow.

Is there a way to do this in the gnome terminal?

I only know the command to scroll up or down one page at a time.  shift + pageUp

thanks

I asked the same question on answers.launchpad.net [1] and got an answer by Philipp Bönhof:

[I]Ctrl+Shift+Arrow Up/Down

Hope this works for you
[/I]

Best regards

Hugo Heden

[1] [https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/32554](https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/32554)

---

