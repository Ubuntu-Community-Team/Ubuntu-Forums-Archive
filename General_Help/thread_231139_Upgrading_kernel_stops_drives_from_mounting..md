---
title: "Upgrading kernel stops drives from mounting."
date: 2006-08-07
forum: General Help
---

### Post by ironfistchamp on 2006-08-07
Hey all

Bit early (in the UK at least) for a post but its pretty important. Anyway I upgraded my kernel to 2.6.17 to see what it is like. The whole making adn installing went off without a hitch. Rebooted and it is on the list. Named 2.6.17.7. Not sure if that is the correct name but I followed the guide and I think it went well. So X Server fails but thats OK I have an nvidia card. I have the driver in my home dir. I cd'ed into my home dir but it wasn't there. I checked in /home and it was empty. Everything below my waist went numb. I thought that my whole home dir had been deleted. I then remembered its on hda2. Phew. Check if its mounted. No it isn't. Odd it should be. Mount it myself. "/dev/hda2 could not be mounted. It may be busy or /home" I can't remember the actual wording but that is the jist of it. So I made a new dir called /temp. I tried to mount it there but no luck. I am really up a certain creek if I can't get home mounted. Can anyone help?

I noticed this also happened a while back when I tried to get the 2.6.16 kernel.

The boot process is weird aswell. I select it on GRUB and the screen goes black for about 2mins then a white line appears in the top left corner for a few seconds and then the failed X Server output.

Thanks for any help

Ironfistchamp

---

### Post by lordjoe on 2006-08-07
The fix is to apply the patch 'bd-claim.patch' from EVMS. I'm not too keen on the details, but it is explained in the [EVMS Docs]("http://evms.sourceforge.net/install/kernel.html#bdclaim").

The patch is found in the evms releases which can be downloaded from the [EVMS Files]("http://evms.sourceforge.net/faq.html") page on sourceforge. Or just use the attached.

There are a couple forum threads that talk about it if you search around.

Perhaps it is possible to convert all your volumes to EVMS and avoid the patch, but I haven't tried it.

---

### Post by ironfistchamp on 2006-08-07
Thanks for the reply I shall give it a go.

---

