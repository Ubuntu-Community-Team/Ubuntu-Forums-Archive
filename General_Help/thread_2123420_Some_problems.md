---
title: "Some problems"
date: 2013-03-07
forum: General Help
---

### Post by St0n3 on 2013-03-07
I installed Ubuntu 12.04 LTS x64 with wubi and it works fine but i have no sound and i cant install wine..

About the sound:
Ubuntu and alsamixer detects that i have sound  but i not hear nothing for some reason :/

Picture
[ATTACH=CONFIG]240026[/ATTACH]

About wine:
When i try to install Wine it gives me a error
[ATTACH=CONFIG]240027[/ATTACH]

I hope you guys help me

---

### Post by St0n3 on 2013-03-08
anyone?

---

### Post by ManamiVixen on 2013-03-08
Is your audio from a Sound Card/Intergrated Audio, or from the video card?

Because ALSA set your video card's HDMI as the main sound output.

---

### Post by St0n3 on 2013-03-08
> **ManamiVixen said:**
> Is your audio from a Sound Card/Intergrated Audio, or from the video card?

Because ALSA set your video card's HDMI as the main sound output.
Integrated audio, i have no video card.

---

### Post by ManamiVixen on 2013-03-08
Copy and paste into terminal. " cat /proc/asound/cards " hit enter and paste here what it says.

---

### Post by St0n3 on 2013-03-08
> **ManamiVixen said:**
> Copy and paste into terminal. " cat /proc/asound/cards " hit enter and paste here what it says.

[ATTACH=CONFIG]240028[/ATTACH]

It says intel in the beggining
But.. i dont have intel

I got AMD-Based processor

---

### Post by ManamiVixen on 2013-03-08
The Nvidia card uses a sound driver that is used for generic DSP's Like what Intel has in their chipsets. Hence the Intel name.

According to ALSA, your onboard audio is not recognized. What motherboard does you computer have, or if prebuilt, what brand and model.

---

### Post by ManamiVixen on 2013-03-08
Sorry, I got stupid. You have no card, but chipset is Nvidia using the standard Intel driver. Let me think a sec,.

---

### Post by St0n3 on 2013-03-08
i got integrted graphics 256 mb

---

### Post by ManamiVixen on 2013-03-08
Look here
[http://ubuntuforums.org/showthread.php?t=1462288](http://ubuntuforums.org/showthread.php?t=1462288)

Looks like your sound isn't supported by Linux VIA VT1705 Sound chip.

---

### Post by ManamiVixen on 2013-03-08
Yeah, I apologize for my brainfart, I missed the VIA part in the ALSA terminal as well as the intergrated video part.

---

### Post by dulbirakan on 2013-03-08
I may be wrong but there may be a very simple solution for this.

Open the sound settings. It is in system settings, I think you can open it by clicking on the speaker icon too.

You will see 2 output devices listed select the one that is not currently selected. That should solve it...

[ATTACH=CONFIG]240029[/ATTACH]

---

### Post by St0n3 on 2013-03-08
> **dulbirakan said:**
> I may be wrong but there may be a very simple solution for this.

Open the sound settings. It is in system settings, I think you can open it by clicking on the speaker icon too.

You will see 2 output devices listed select the one that is not currently selected. That should solve it...

[IMG]http://ubuntuone.com/1v6xsY4zr2e5aHLi3mRqce[/IMG]
it doesnt working

---

### Post by St0n3 on 2013-03-10
how i can get wine working anyway?

---

