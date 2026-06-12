---
title: "Would like to disable the Welcome banner"
date: 2024-03-02
forum: General Help
---

### Post by hrsetrdr on 2024-03-02
I recently installed Ubuntu MATE 22.04.4 LTS, and noticed that the checkbox to disable the Welcome banner(booting to desktop) is no longer there.    It's not a big deal, but I really have no use for any of the features that the Welcome banner displays.   I have looked through all the Preferences options but am not seeing anything.    Googling-for-answers isn't turning up any useful information, perhaps I need another cup of coffee...

Any suggestions?

---

### Post by TheFu on 2024-03-02
Check **grub** boot options.
Perhaps quiet or nosplash is supported?

I don't boot very often and generally I'm not sitting at the computer watching.  If I reboot, which is about every other week, it is just after patching lots of systems and bringing them all up takes a few minutes - perfect to get some tea.

---

### Post by hrsetrdr on 2024-03-02
> **hrsetrdr said:**
> Would like to disable the Welcome banner 

...just for clarification here is a screenshot of what I'm referring to:

[IMG]https://i.postimg.cc/bwS5MqPQ/Screenshot-at-2024-03-02-08-39-21.png[/IMG]

---

### Post by deadflowr on 2024-03-02
It should be a snap package so try disabling it.
```
snap disable ubuntu-mate-welcome
```

---

### Post by hrsetrdr on 2024-03-02
> **deadflowr said:**
> It should be a snap package so try disabling it.
```
snap disable ubuntu-mate-welcome
```

Thanks, that did the job.

---

