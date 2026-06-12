---
title: "Tweak refusing to accept changes"
date: 2013-02-06
forum: General Help
---

### Post by TheBigH on 2013-02-06
I'm using Ubuntu Tweak v 5.14 on my Ubuntu 10.04.4 machine, and I cannot get it to add file associations in File Type Manager. I am trying to use "add custom command" in the "add application" window, but as soon as I type anything into the text window, the "Add" and "Cancel" buttons become  non-functional. Not only is my change not saved, but I can't even close the "add application" window except by using the red X close window button.

If I run "sudo ubuntu-tweak" through the terminal, the bad behaviour is the same when hitting the Add button, but it also dumps the following error message (?) onto the terminal output:

```

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/modules/filetype.py", line 395, in on_add_button_clicked
    app = gio.AppInfo(we)
TypeError: gio.AppInfo() argument 1 must be string, not None
```What's going wrong, and how do I fix it?

Or is there a way to add file associations by editing something through a terminal, so that I can avoid having to use Tweak at all?

---

