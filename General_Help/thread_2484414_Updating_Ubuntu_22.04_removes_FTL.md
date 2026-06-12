---
title: "Updating Ubuntu 22.04 removes FTL"
date: 2023-02-25
forum: General Help
---

### Post by fotingo on 2023-02-25
I use Ubuntu 22.04 and running Pihole.
Recently, I noticed that I wasn't able to update Pihole due to getting this error.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291835&stc=1[/IMG]

So, after trying a few things, nothing worked. So, I ended up reinstalling a fresh Ubuntu and everything started working again.
But, I updated Ubuntu today and after the update, I started getting that same error again. 

It seems the latest version of Ubuntu removes FTL?
Please help.

---

### Post by MAFoElffen on 2023-02-25
It would help if you included the full information in this post here on the Forum... According to your error output posted in your other thread posted at: [https://www.linux.org/threads/updating-ubuntu-removes-ftl.44029/#post-184662](https://www.linux.org/threads/updating-ubuntu-removes-ftl.44029/#post-184662) :

It can't find the file there, but the file you are trying to get is actually at: [https://github.com/pi-hole/FTL/releases/download/v5.21/pihole-FTL-linux-x86_64](https://github.com/pi-hole/FTL/releases/download/v5.21/pihole-FTL-linux-x86_64)

It doesn't seem to be a problem with Ubuntu, but that the URL changed at GitHub, and the link going through their "latest" is broken. You should file an issue there on that GitHub project, so they can update/fix their link there.

---

### Post by DuckHook on 2023-02-25
It is not good netiquette to leave multiple threads asking for help all over the internet unless you follow up by posting updates and the eventual solution on all of them.

---

### Post by fotingo on 2023-02-25
The reason I came here and created an account to post my issue is because I came from Pihole and they are telling me there is nothing wrong on their side.
I am being told there is nothing wrong with their link to update pihole as they are not having any issues.

---

### Post by MAFoElffen on 2023-02-25
How did you install FTL? Because the error is coming from "somewhere" and getting a "file not found" error? Because Pi-hole and FTL are not Ubuntu packages. They are installed externally from pi-hole URL's to get their packages... (That is what I see. RE:[https://www.virtualizationhowto.com/2021/12/install-pi-hole-in-ubuntu-21-04/](https://www.virtualizationhowto.com/2021/12/install-pi-hole-in-ubuntu-21-04/))

See where that goes?

---

### Post by fotingo on 2023-02-25
I didn't. that's all installed on its own when I install ubuntu and pihole, then it bugs out after the recent Ubuntu 22.04 update. i don't have this issue with Linux Mint, only with Ubuntu 22.04.

---

