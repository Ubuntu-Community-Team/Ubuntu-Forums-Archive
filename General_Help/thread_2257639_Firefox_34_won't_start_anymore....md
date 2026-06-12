---
title: "Firefox 34 won't start anymore..."
date: 2014-12-21
forum: General Help
---

### Post by bigred2012 on 2014-12-21
Hello,

I've been using Kubuntu for sometime now and recently installed a fresh copy of KUBUNTU 14.10.  Fully updated and so forth, everything is working splendidly.

Except. suddenly for Firefox.  It now loads when its icon is clicked but doesn't actually show up.  I attempted to start Firefox through the terminal and it worked but gave me the following error message:

(process:3555): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
1419181226369   GMPInstallManager.simpleCheckAndInstall INFO    Last check was: 163 seconds ago, minimum seconds: 86400
1419181226369   GMPInstallManager.simpleCheckAndInstall INFO    Will not check for updates.



Would anyone know to go about resolving this issue?

---

### Post by tgalati4 on 2014-12-22
Try again:

```
sudo killall firefox
firefox --debug
```

You might have to delete your firefox profile and start with a clean one.

If you are running plug-ins, you can use the -safe-mode switch to turn them off and see if the behavior changes.

---

### Post by nerdtron on 2014-12-22
Try resetting your firefox profile.
1. Close all firefox.
2. Open home folder and show hidden files.
3. Rename .mozilla folder to .mozilla_old folder.
4. Launch firefox again.

---

