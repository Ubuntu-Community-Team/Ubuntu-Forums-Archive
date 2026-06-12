---
title: "Video Card Upgrade"
date: 2008-02-27
forum: General Help
---

### Post by TimMcE on 2008-02-27
I've decided it's about time that this poor machine got itself a few upgrades, and due mainly to the problems I've had in Ubuntu with it's ATI video card, I'm going to be picking up a Nvidia card as a replacement.  Since this machine doubles as my gaming computer, I'm figuring on picking up a GeForce 8800 since the price is right, and a few minutes of Google-Fu didn't turn up any major problems with the 8800 series & Ubuntu.

But whenever I upgrade anything, I like to know what I'm getting myself into first, and I've never upgraded hardware on a Linux box before, so I just have a few questions.

First, what sort of preinstallation steps should I take?  Should I remove the ATI restricted driver I have currently installed?  Is there anything else I should remove?  And should I have the Nvidia drivers already downloaded and tucked away somewhere special, or can I do that after the fact?

Does Ubuntu perform any kind of automated maintenance when it detects new hardware?  My xorg.conf is rather badly mutilated from all the gentle persuasion and coaxing it took to get all the bells & whistles running with the ATI card.  Am I going to have to go in and rewrite most of it, or will Ubuntu overwrite it when it detects the new card and/or installs the drivers for it?

---

### Post by renzokuken on 2008-02-27
my advice would be to revert to the generic **vesa** driver temporarily, then remove the ATI driver.

swap your new card in, boot up with vesa, then install the Nvidia driver through the Restricted Drivers Manager

to revert to **vesa** run

```
sudo dpkg-reconfigure xserver-xorg
```

selecting vesa

---

