---
title: "Strange problems with Ubuntu 13.10"
date: 2014-03-05
forum: General Help
---

### Post by agons on 2014-03-05
Hello all,
I've used Ubuntu in the past but It's not often I have two OSs on the same computer. So here the event. I had windows 7 Installed on 2 ssd's set in raid 0 By the Bios of my computer, I hear some people call it a software raid I perfer to call it a Bios raid. anyways I then installed Ubuntu on another HDD I bought last week. Then I broke something in windows(long story) so i had to reinstall. I didnt want to ruin my ubuntu so I unpluged the drive just to be safe. Once windows was installed I plugged my Ubuntu drive back in. Now as I assume the Grub loader now desnt point right and I cant get to windows from the grub menu, but I guess i didnt realize this before but ubuntu doesnt even see my ssd's. It has no idea where they are so even though I'd love to redirect my grub so I could boot to windows which having to change my boot settings I can't because as far as my Ubuntu see's it, the ssd raid does not exist. Anyone have any ideas?

-Max

---

### Post by Kirboosy on 2014-03-06
Have you run the following command from terminal once booted into Ubuntu?

```
sudo update-grub
```

That command will tell GRUB to detect and add whatever OS it can. Hopefully its as simple as that for you since its a RAID 0. RAID might make it more difficult.

If that doesn't work you could try [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") and see if that fixes it

Hope that helps!
~Caboose

---

