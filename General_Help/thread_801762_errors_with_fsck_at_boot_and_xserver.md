---
title: "errors with fsck at boot and xserver"
date: 2008-05-20
forum: General Help
---

### Post by swordlashe0 on 2008-05-20
Ok, Ive been using ubuntu on my laptop for about 6 months now. Today I booted up my gateway mx3231 laptop to have the ubuntu logo and load bar take FOREVER. After that it shoved me into a maintenance shell and told me fsck had failed to run at startup, asking me to run it manually. I typed in fsck to run it, and it went into a loop locking up tight and spitting out the same code over and over. I rebooted it, and when it shoved me into this console again I hit control+D to reboot and it began to reboot WHEN... 

I received an error message saying xserver had failed to start. I tried to run dpkg-reconfigure xserver-xorg but it showed me the confg window and locked up. Im lost now and rather SOL. Is there anyway to breath life back into xserver?

thanks.

---

### Post by hanktacoma on 2008-05-21
> **swordlashe0 said:**
> Ok, Ive been using ubuntu on my laptop for about 6 months now. Today I booted up my gateway mx3231 laptop to have the ubuntu logo and load bar take FOREVER. After that it shoved me into a maintenance shell and told me fsck had failed to run at startup, asking me to run it manually. I typed in fsck to run it, and it went into a loop locking up tight and spitting out the same code over and over. I rebooted it, and when it shoved me into this console again I hit control+D to reboot and it began to reboot WHEN... 

I received an error message saying xserver had failed to start. I tried to run dpkg-reconfigure xserver-xorg but it showed me the confg window and locked up. Im lost now and rather SOL. Is there anyway to breath life back into xserver?

thanks.

I'm having a similar problem but it didn't get as far as yours so I don't know if my story is going to help even if it's on time.  But on my system I noticed (fine print) message to escape from the /dev/sda1 system check.  So I pressed escape and Ubuntu booted.  Every time I boot I have to poise my finger on the escape button because the message flashes by very fast. Good luck...  hanktacoma

---

### Post by hanktacoma on 2008-05-21
[QUOTE=hanktacoma;5007338]I'm having a similar problem but it didn't get as far as yours so I don't know if my story is going to help even if it's on time.  But on my system I noticed a (fine print) message to escape from the /dev/sda1 system check.  So I pressed escape and Ubuntu booted.  Every time I boot I have to poise my finger on the escape button because the message flashes by very fast.

(I came back to edit a mistake and then my message was too short to post hence these last words.)

---

