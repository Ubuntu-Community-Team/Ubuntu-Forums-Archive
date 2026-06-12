---
title: "Tip for getting Totem to work"
date: 2005-10-26
forum: General Help
---

### Post by laran on 2005-10-26
It's apparently pretty common to try to startup Totem with a fresh install and have it error out saying something like "Totem could not start up: resource unavailable or busy".

The posts on this topic all seem to say to install a different player or to uninstall and re-install Totem, which involves uninstalling ubuntu-desktop (which is optional but suggested). Well, I got it to work without doing any of that. So I just wanted to pass along how I did it.

On the menubar, click System -> Preferences -> Multimedia Systems Selector.
Click the Video tab. Under Default Sink select "XWindows (No Xv)". Under Default Source select "Test Input". Click "Close". You're done.

Hope this works for others. This is one bug that has been  annoying me for months.

p.s. - I run Ubuntu in VMWare. So hopefully this solution is portable to native installations. Good Luck!

---

### Post by John.Michael.Kane on 2005-10-26
Try Totem-xine, and installing all codecs

---

### Post by rplantz on 2005-10-26
[QUOTE=SD-Plissken]... and installing all codecs[/QUOTE]

I'm not clear on what you mean by "all codecs."

Thanks,
Bob

---

### Post by autonomy on 2005-10-26
I just this in help. I had to click the life preserver, the user guide, applications, and music and movies, and it told me how to install multimedia codecs.

---

