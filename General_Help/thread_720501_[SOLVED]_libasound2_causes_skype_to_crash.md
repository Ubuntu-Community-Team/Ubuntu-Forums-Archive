---
title: "[SOLVED] libasound2 causes skype to crash"
date: 2008-03-10
forum: General Help
---

### Post by Achetar on 2008-03-10
I have libasound2 v. 1.0.14 installed on my computer (running Xubuntu Hardy, but GNOME is also installed, though I rarely use it). On the Skype website it says libasound2 v. 1.0.12 

When I run Skype, it allows me to login, but crashes before it gets to the contact list. When run in the terminal, it spits out the following errors:
```

ALSA lib conf.c:1588:(snd_config_load1) _toplevel_:5:34:No such file or directory
ALSA lib conf.c:2849:(snd_config_hook_load) /home/fixer/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2713:(snd_config_hooks_call) function snd_config_hook_load returned error: No such file or directory
ALSA lib conf.c:3076:(snd_config_update_r) hooks failed, removing configuration
Aborted (core dumped)

```Do I need libasoun2 v. 1.0.12 or is there another thing that I am having problems with?

EDIT: I solved it. my .asoundrc file was causing the problem. When I deleted it, the problem went away and now skype works perfectly!

---

