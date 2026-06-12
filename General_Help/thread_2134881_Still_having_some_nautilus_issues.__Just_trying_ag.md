---
title: "Still having some nautilus issues.  Just trying again."
date: 2013-04-12
forum: General Help
---

### Post by xeddog on 2013-04-12
I have been running Ubuntu 12.04 since it came out, but I had to re-install it after a HD crash recently.  I installed it back onto a new 1TB hard drive, and I have a second 1TB hard drive that contains my /home filesystem from the previous install.  And, I have installed gnome3 (using software center), and since I don't care for Unity or Gnome3, i have also installed gnome-session-fallback, and that is my preferred desktop.

Now,  when I did the new installation of 12.04, and installed the Gnome3 and gnome-session-fallback desktops, everything was working just fine.  Unity works, Gnome3 works, and gnome "classic" works.  Then I edited my fstab to use my old /home directory and rebooted.  After that, the gnome classic has several problems, mostly minor, but the one that is really bugging me is that when I go to the top panel and click on Places>Home,  Places>Network, Places>Computer, etc. I get an error panel like the attached example for Places>Computer.  Of course, where the example shows "Computer://", Places>Home will show "file:///" and Places>Network will show "Network://"

This has to be a problem with some file in my pre-existing home directory somewhere, but I am at a loss as to where to look.  I have tried copying a bunch of the hidden files from the new /home to my old /home, but the only thing I have managed to do is lose my upper panel customization (no biggee) and all of my Firefox bookmarks (%$#@$%).  Oh, and a few desktop icons.  So now I have made the fire under the kettle a bit bigger.

Any and all help and suggestions would be appreciated.

X

---

### Post by fantab on 2013-04-12
Can you open nautilus?

Try:

```
sudo apt-get install nautilus
```

I suspect that 'nautilus' may not have installed or installed properly. You can check this in either 'Software Manager" or with 'Synaptic'.

---

### Post by xeddog on 2013-04-12
Thanks fantab, but I don't think this is the problem.  I have removed and re-installed it a few times over the course of the time I have been trying to resolve this.  The problem is that when you uninstall nautilus, a lot of other gnome stuff goes with it.  Like almost anything to do with gnome, so it takes a little work to get it all back.  Besides, why would it work perfectly when I remove my old /home from fstab and use the newly installed /home?   I think it is definitely something that is screwed up in my old /home, I just don't know what it is.

I have managed to make a minor improvement though.  I just used synaptic and installed a package called nautilus-share.  That gave me back the file:/// associations so now things like Places>Home work, but the others like Places>Computer and Places>Network still do not.

Thanks,

X

---

