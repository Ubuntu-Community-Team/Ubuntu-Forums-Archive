---
title: "Sometimes, Kubuntu just doesn't boot"
date: 2020-01-25
forum: General Help
---

### Post by pascalcnrad on 2020-01-25
Hello, I have a Lenovo Thinkpad P43S running Kubuntu 19.10 on it.
Actually, Kubuntu runs very well on my computer but, there is still a mysterious issue that I don't understand because it only occurs occasionally.
When I start the Computer I get the GRUB menu directly where I have some boot options. Most of the time when I select Kubuntu to boot it just works. So, I see the Kubuntu boot screen first and then, I see a Lenovo boot screen and then, I see the Kbuntu boot screen again and then, I see some text and then, I see a blinking curser and finally, SDDM appears. 
All this happens within a very short time. But, approximately every fifth boot trial there's just the Kubuntu boot screen and it will never disappear until I shut down the Laptop for by pressing the power button for a few seconds.

Considering the differences I suppose that GRUB only loads the boot screen but however, it never loads the kernel and GRUB doesn't return an error message.
Can anyone explain these happenings? Does anyone know why GRUB does not return an error message? Why does this only occasionally occur?

---

### Post by rbmorse on 2020-01-25
It really sounds like a firmware issue to me. Check with Levono for updates. 

I have an Nvidia RTX 2080 in my desktop PC that does more or less the same thing. Nvidia says it needs a vbios (firmware) update but the AIB (ASUS) hasn't provided, yet.

---

