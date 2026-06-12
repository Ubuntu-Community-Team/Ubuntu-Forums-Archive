---
title: "grub config on jammy jellyfish tutorial"
date: 2022-05-07
forum: General Help
---

### Post by Oral B Sonic Complete on 2022-05-07
Hi!

I recently upgraded to 22.04 and it reset grub, as it seems. I want to set everything back to the way it was before, i.e. 
Win10
Ubuntu
Recovery options

as the only options I can see upon boot. 
the grub-customizer repo seems to have been taken out of the paket sources for some reason, I assume either for security reasons or its just broken atm. 
So I figured I'd go looking in grub for myself, how hard can it be, right? 
welp. 
Someone on reddit said that grub isn't even responsible anymore, but that 22.04 boots with systemd-boot. Which seems weird to me, but I'm just a user and haven't looked that deep under the hood yet. 
All the tutorials I can see mention /etc/grub/linux_10 as the file to edit for the options grub displays. But my linux_10 looks nothing like the linux_10s from older versions ( 20.04 and lower). Any ideas on where I can look to get a better idea of what's going on and what I need to do to edit things in a way that makes me happy? 

Thanks

OB

---

