---
title: "Cannot Enable gedit Plugins"
date: 2013-07-14
forum: General Help
---

### Post by hwttdz on 2013-07-14
I am getting the following when attempting to enable the "code comment" plugin.  Does anyone know what might be going on?

```
Traceback (most recent call last):
  File "/usr/local/lib/gedit/plugins/codecomment.py", line 57, in <module>
    class CodeCommentPlugin(GObject.Object, Gedit.WindowActivatable):
  File "/usr/lib/python3/dist-packages/gi/types.py", line 230, in __init__
    cls._setup_vfuncs()
  File "/usr/lib/python3/dist-packages/gi/types.py", line 118, in _setup_vfuncs
    for vfunc_name, py_vfunc in cls.__dict__.items():
RuntimeError: Couldn't find GType of implementor of interface GeditWindowActivatable. Forgot to set __gtype_name__?
```

---

### Post by mc4man on 2013-07-14
> **hwttdz said:**
> I am getting the following when attempting to enable the "code comment" plugin.  Does anyone know what might be going on?


Never hurts to mention what release of Ubuntu you're using, what version of gedit &  also in this case,  where did you get the plugins from?
 As I see -

File "/usr/[COLOR="#FF0000"]local/[/COLOR]lib/gedit/plugins"

---

### Post by hwttdz on 2013-07-14
It was gedit 3.8.1 I believe.  I had attempted to install an unrelated package, which had required upgrading one of gedit's dependencies, and things got out of hand quickly.

I was able to restore my /usr/local to a previous state and everything played well again.  I believe this error is actually due to the commit reverted by this one: [https://mail.gnome.org/archives/commits-list/2013-January/msg00722.html](https://mail.gnome.org/archives/commits-list/2013-January/msg00722.html)
but gtk didn't build directly from git for me and since I was able to get everything working by restoring, I'm just not worrying about it anymore.

---

### Post by monkeybrain2012 on 2013-07-14
Did you install gedit 3.8.1 with gnome ppa? Don't know if it is the same issue, but I have a partition running Debian unstable and I have installed gnome-shell 3.8 from experimental, gedit 3.8 is available in the experimental repo but upgrading it would remove gedit-plugins (so I didn't upgrade)

---

