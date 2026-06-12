---
title: "Protect config files in /etc"
date: 2008-05-17
forum: General Help
---

### Post by roe_polak on 2008-05-17
Oi there

I've got a desktop computer running Ubuntu and my laptop is running Gentoo. Lately I've used my laptop a lot (and generally just fiddling with setting up the system) and I've grown accustomed to setting system wide configs in /etc, thus not needing to have identical .zshrc, .vimrc and so on in ~/ and /root.

When I put Hardy on my desktop i started configuring the system the same way. But suppose I updated, let's say, Vim, wouldn't that destroy my configs? So far no updates have ruined anything, but is there any way to protect these files in Ubuntu? If not, what clever tricks are available to having a single configuration for my everyday user and root?

There might be a very simple answer to this, but hey, I'm still learning the ways of Ubuntu.

---

### Post by ibuclaw on 2008-05-17
For gnome type configurations, I just put at the top or bottom:
```
include "/path/to/config"
```
And have all my settings put in there.

For script files, it is very much the same:
ie: BASH
```
. /path/to/script
```

Generally, the config files are left alone (ie, crontab, gdm, apt), and if they are tinkered with (a good example is me always tinkering with the /boot/grub/menu.lst script). Then when you install a package (at least, via aptitude) it will ask you what want to do with the file.
Of the top of my head, I think its:
 - Leave Altered File Unchanged,
 - Replace old lines with new.
 - Erase over with package maintainer file.

And if it doesn't, the deb scripts are smart enough not to erase your personal settings anyway!

They use a technique where they read the config file line by line and add new configurations/replace old ones using line matching.
ie, you'll read something like this:
```

This line is unaltered
--Remove this line++Put this here instead
This line remains
++New Line++
++Another new line++
--And completely remove this line--

```

So your files are pretty much safe regardless!

Regards
Iain

---

### Post by roe_polak on 2008-05-17
Thanks, that was very useful information. I wasn't aware that aptitude had this functionality, then again, I haven't set up my Ubuntu system this way before. Luckily I prefer using aptitude so I might have found out about this sooner or later :) I'll keep an eye out at the next updates but I might as well try to reproduce it buy reinstalling select packages.

---

### Post by ibuclaw on 2008-05-17
Edit the /boot/grub/menu.lst file...

Rename the kernel name "Ubuntu Hardy" to, I don't know... erm "Test test".

Then upgrade your kernel to the newest one. It's in the "proposed" repository, I think.
Either that or make your own kernel deb package following the instructions [here]("http://ubuntuforums.org/showthread.php?t=311158"), since I know that you gentoo users just love to compile your own kernel ;), and you should see what I mean when you "dpkg --install" it.

Regards
Iain

---

### Post by roe_polak on 2008-05-17
I just wanted to make sure that when updating packages my own config files would remain untouched. I've just tested it (though not a real update, just reinstall) and it's seem to work. With the kernel compiling I'd rather not compile my own Ubuntu kernel. I'm using the Ubuntu Studio realtime kernel and my desktop computer does not mind the large kernels. Besides I've got way too many gadgets connected to the computer and with the Ubuntu kernels most stuff just work. On my laptop it's different. I like to keep my kernel and system at a minimum. If was compiling just for the fun of it I would be truly mad :D

---

