---
title: "Disable Hibernation in 7.10"
date: 2007-10-18
forum: General Help
---

### Post by elventear on 2007-10-18
Hello everyone,

I just upgraded to 7.10 and everything has been working very well.

I would like to disable hibernation in my computer. Previously in 7.04 I did by configuring gnome-power settings in the gconf-editor.

In 7.10 gconf-editor says that those keys are set as read only and I can't change them. I've tried to unset them as root but still there is no way for me to edit them. 

Anybody have any idea on how I can disable Hibertnation now?

Thanks!

---

### Post by por100pre1 on 2007-10-18
Try this:

```
sudo chown -R user:user /home/user/.gconf
```

```
chmod -R 700 /home/user/.gconf
```

replace user in every instance with your user name.

Then try to use gconf editor again.

---

