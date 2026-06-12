---
title: "Opening Terminal also opens Skype"
date: 2015-05-21
forum: General Help
---

### Post by mtift on 2015-05-21
In spite of my [ethical concerns]("https://wiki.ubuntu.com/SkypeEthics") (I prefer [Mumble]("http://wiki.mumble.info/wiki/Main_Page") for voice chat), I have [Skype 4.3.0.37]("http://blogs.skype.com/2014/06/18/skype-4-3-for-linux/") installed on a machine running Ubuntu 12.04.5. It works just fine. However, whenever I press Ctrl-Alt-t or click on my Terminal icon, both Terminal and Skype open. This is quite annoying, as I open terminals frequently. Ideally, I would like keep using the default behavior, opening Terminal with Ctrl-alt-t. I don't see any options to change this behavior in the Skype UI, ~/.config/Skype/Skype.conf, or elsewhere.

My main goal is to prevent Skype from opening rather than change how I open Terminal. I realize this may be difficult given that Skype is proprietary. At this point, it seems like my best option is to uninstall Skype and only reinstall it on the rare occasions where I need it (e.g. when I appear on a podcast, recorded over Skype, to promote free software).

Any ideas how I can avoid this nuisance?

(FWIW, I have the exact same problem on Debian GNU/Linux testing/stretch, XFCE, with Skype 4.3.0.37.)

---

### Post by oldos2er on 2015-05-21
Have you checked your .bashrc file to see if Skype is loading from there? Just a thought.

---

### Post by mtift on 2015-05-21
That was it! I was having problems installing Skype and rather blindly followed the directions on [http://linuxg.net/how-to-properly-install-skype-4-3-on-debian-and-derivatives-and-fix-the-crashes](http://linuxg.net/how-to-properly-install-skype-4-3-on-debian-and-derivatives-and-fix-the-crashes), including:

[FONT=courier new]  echo "LD_LIBRARY_PATH=/usr/lib/i386-linux-gnu/ /usr/bin/skype" >> ~/.bashrc[/FONT]

It looks like that was [not a particularly good idea]("ftp://linuxmafia.com/faq/Admin/ld-lib-path.html"), and removing that line fixed my problem. (I share a .bashrc across machines, so it fixed the problem in both places.) I added a comment on that blog post.

Thanks, oldos2er!

---

### Post by oldos2er on 2015-05-21
Welcome!

---

