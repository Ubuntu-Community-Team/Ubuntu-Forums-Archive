---
title: "Set UTC/Localtime at boot"
date: 2008-07-07
forum: General Help
---

### Post by Xyem on 2008-07-07
I have Ubuntu 8.04 installed on a 2.5" HDD and I boot it up in different circumstances where the hardware time ( what BIOS uses? ) may be either UTC or the local time.

Is there a parameter or something I can pass which would allow me to tell it ( the kernel? ) which one it is so it gets the time correct right from the start? At the moment, I have to manually call 'hwclock --hctosys' with the appropriate parameters for the situation.

Perhaps ideally, an entry in GRUB or for it to ask me during boot ( with a timeout ) would be great but anything that doesn't require me to become root would be appreciated ( such as asking before log-in ).

Thanks

---

