---
title: "grub boot screen"
date: 2014-06-23
forum: General Help
---

### Post by Pedroski55 on 2014-06-23
I recently installed Ubu 14.04 on 3 computers. This is a bit of grub.cfg

if [ x$feature_timeout_style = xy ] ; then
  ###  set timeout_style=hidden
    set timeout=30
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi

This '###  set timeout_style=hidden' causes the boot screen to be black. You cannot see any choices of OS, memtest. What other value can this have? 'visible'??? I commented it out, then I could see my boot screen, so I am sure this is the culprit!

I always like timeout to be 30, (I am a bit slow). Where should I set this? In 40_custom??? Can both be set in 40_custom?? Then I won't need to do it again after a kernel upgrade.

Thanks for any replies!

---

### Post by grahammechanical on 2014-06-23
I do not see that In my grub.cfg. But then again I have not changed the time out. We are not supposed to edit grub.cfg. You seem to be quoting bits of the 00_header script.

>   if [ x\$feature_timeout_style = xy ] ; then
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep${verbose} --interruptible ${timeout} ; then
    set timeout=0


We can edit /usr/share/default/grub. We can use /etc/grub.d/40_custom to create our own boot entries. We need to make sure that 40_custom is executable and that we have run

```
sudo update-grub
```

which is an executable script that runs a grub utility called grub-mkconfig which reads the various grub configuration files and creates grub.cfg. But I would not mess with grub.cfg or the scripts themselves that are in grub.d with the exception of 40_custom and 41-custom which we are allowed to edit.

Why not start from the beginning. What is the problem? Does it happen on all 3 computers? Do they have similar hardware?  Do they have BIOS or EFI boot system? Is Ubuntu the only OS?

/usr/share/grub/default/grub

> GRUB_TIMEOUT=10

Change that to = 30 and run sudo update-grub.

Regards.

---

### Post by Pedroski55 on 2014-06-24
Thanks for that. I will set the timeout where you said.

What about 'set timeout_style=hidden' I want to see the boot screen. What other values can this have?? visible? true? seen?

---

