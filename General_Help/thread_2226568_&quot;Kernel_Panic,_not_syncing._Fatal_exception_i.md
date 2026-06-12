---
title: "&quot;Kernel Panic, not syncing. Fatal exception in interrupt&quot; Issue - Need Help!"
date: 2014-05-28
forum: General Help
---

### Post by francis3 on 2014-05-28
I recently bought a desktop and installed Ubuntu 14.04 LTS completely. Yesterday, after an update, the computer rebooted and got stuck on this screen. 

[ATTACH=CONFIG]253525[/ATTACH]

Now, no matter how much I reboot the computer, it keeps coming back to this screen. Will someone please help? 

Also, please note that I am a complete newbie to ubuntu so I might not be able to understand certain Linux lingo as well. So please expain as best as you can. 

Thanks.

---

### Post by matt_symes on 2014-05-28
Hi

Boot into an older kernel from the grub menu at start up.

I suspect you had a kernel update and it updated the wireless driver and that looks to be going bang after the update.

Kind regards

---

### Post by francis3 on 2014-05-29
> **matt_symes said:**
> Hi

Boot into an older kernel from the grub menu at start up.

I suspect you had a kernel update and it updated the wireless driver and that looks to be going bang after the update.

Kind regards

Thanks Matt, 

I managed to boot into a kernel previously updated and now I got in. But what else do I need to do now? Does it mean that I can no longer install any updates?

What can I do to prevent this from happening again?

---

### Post by jakke1975 on 2014-05-29
You can still update, but I would block this kernel, as it doesn't seem to like your network card...
see this thread on how to stop a kernel update: [http://askubuntu.com/questions/178324/how-to-skip-kernel-update](http://askubuntu.com/questions/178324/how-to-skip-kernel-update)

---

### Post by matt_symes on 2014-05-29
Hi

> **jakke1975 said:**
> You can still update, but I would block this kernel, as it doesn't seem to like your network card...
see this thread on how to stop a kernel update: [http://askubuntu.com/questions/178324/how-to-skip-kernel-update](http://askubuntu.com/questions/178324/how-to-skip-kernel-update)

^^^ That looks like a good start :)

I'll take a better look tomorrow if i get the time.

Kind regards

---

