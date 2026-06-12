---
title: "Little problem when shutting down/ restarting Ubuntu"
date: 2021-10-25
forum: General Help
---

### Post by pinho1604 on 2021-10-25
Dear Ubuntu Friends:

 Everytime i try to shut down or restart, my desktops tries to close then it comes back, waits for about 30 seconds and so it finally shuts down or restart. The curious thing is it only happens when i click on the shutdown option on the "gear' in the taskbar.
 When trying the famous 'shutdown now' or 'sudo reboot' on terminal, the system responds immediately. I don't know what is stalling the shut down/restart on the graphical interface as on the terminal the system responds normally.
 I'm still on Ubuntu 16.04 since now i don't have time to back everything up and do a clean install, also i'm waiting for the 'Jammy Jellyfish' next year, so i'm on ESM and no other problems so far.

Is there anything i can do to check on the issue?
Best regards for all!

---

### Post by TheFu on 2021-10-26
I think the reboot command doesn't actually cleanly shutdown all the processes before doing the reboot.  It is so fast, that concerns me. Programs don't get sufficient warning to close their files and terminate properly before the reboot.

The manpage has this warning:

```
NOTES
       These commands are implemented in a way that preserves basic
       compatibility with the original SysV commands.  systemctl(1) verbs
       halt, poweroff, reboot provide the same functionality with some
       additional features.
```
So perhaps we should be using the **systemctl** version of shutdown and reboot instead?  The manpage for systemctl has much longer sections explaining each ... which is a little scary. I haven't read the entire manpage, so it may not be too bad. Hard to tell.

---

