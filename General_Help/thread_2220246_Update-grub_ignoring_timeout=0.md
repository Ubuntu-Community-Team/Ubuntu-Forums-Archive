---
title: "Update-grub ignoring timeout=0?"
date: 2014-04-27
forum: General Help
---

### Post by tomricht@gmail.com on 2014-04-27
Hi there,

in /etc/default/grub I have

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0

After I run sudo update-grub, /boot/grub/grub.cfg contains this:

if [ "${timeout}" = 0 ]; then
  set timeout=10
fi

Is this a bug or a feature?

tnx

Tom

---

### Post by oldfred on 2014-04-27
Maybe a new feature? :)

Someone else posted this on a recent grub update, not sure what grub has done.

      >  Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported. 



You may need to comment out the hidden timeout setting.

I generally do not suggest using 0 timeout. Some then have issues and cannot ever get to grub menu to run recovery mode.

---

### Post by tomricht@gmail.com on 2014-04-28
> **oldfred said:**
> Maybe a new feature? :)

Someone else posted this on a recent grub update, not sure what grub has done.

You may need to comment out the hidden timeout setting.

Thanks for the suggestion. Tried it. Same result.

> **oldfred said:**
> 
I generally do not suggest using 0 timeout. Some then have issues and cannot ever get to grub menu to run recovery mode.
I know what I am doing and why I am doing it. Trust me ;-)

---

