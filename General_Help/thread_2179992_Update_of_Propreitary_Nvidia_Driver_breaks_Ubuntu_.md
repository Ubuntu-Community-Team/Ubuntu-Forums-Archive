---
title: "Update of Propreitary Nvidia Driver breaks Ubuntu Desktop GUI"
date: 2013-10-10
forum: General Help
---

### Post by checkm8 on 2013-10-10
Ever since I switched back to Ubuntu 12.04.3 LTS I lost hope in Ubuntu. LTS has a new meaning for me because ever since 12.04 came out Ive had these issues and it has yet to be resolved. What good is support if you guys never fix the problem? Im not a coder but maybe thats why people buy a Mac. Anyways here are the issues with this release and good luck to you guys!

1) Ever since I've installed Ubuntu I cannot update the nvidia drivers through Jockey or Update Manager. The lightdm manager fails to start and I have to apt-get purge nvidia* and apt-get install nvidia-(insert "supported" version here) from recovery. Thanks Ubuntu! You guys make things so easy! The search feature now thats support!
2) The subwoofer on my laptop (Asus G73SW-XN2) is not supported by the audio manager in Ubuntu and appears "greyed out". I would love for that feature in Ubuntu considering how archaic my laptop is and how alsa doesn't support it properly either. I dont want regular sound from a subwoofer but some bass would be a blessing.

Ill go buy a mac and install windows on it. That way I can post on forums and figure out how to work with the problem rather than get anything done.

---

### Post by Yellow Pasque on 2013-10-10
Just a heads up: this is a user to user support forum, so all of your ranting and threatening to use other OS's is misplaced...

---

### Post by checkm8 on 2013-10-10
> **Temüjin said:**
> Just a heads up: this is a user to user support forum, so all of your ranting and threatening to use other OS's is misplaced...

Sorry Temujin you are right. Ubuntu is great for a lot of users. Im sure thats not misplaced.

---

### Post by Yellow Pasque on 2013-10-10
jockey's broken for some Precise users, from the reports I see. Are you using the system as Optimus (combo Intel/nvidia graphics) or do you have some BIOS switch that forces the nvidia GPU for everything?

For the sound, if you'd like to try the latest driver, see: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by checkm8 on 2013-10-10
> **Temüjin said:**
> jockey's broken for some Precise users, from the reports I see. Are you using the system as Optimus (combo Intel/nvidia graphics) or do you have some BIOS switch that forces the nvidia GPU for everything?

For the sound, if you'd like to try the latest driver, see: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

Temujin my laptop only has the nvidia display adapter and I do not believe it even contains an intel integrated chipset with wifi, bluetooth, graphics, etc. This is not a BIOS setting from my understanding but convince me otherwise.

Also, the sound is not "HDA Intel".

Please do some research and study the problem before jumping to conclusions on what could or may fix it. Your post count looks impressive, but your knowledge in troubleshooting and gauging problems is certainly misguided and misdirected. I'm not surprised open source software headed in the direction of Red Hat (enough said).

Are you going to support every problem you create for another user? When my system crashes are you going to come over and fix it? No thanks.

[B]Heres another rant but at least it's a constructive one:

Why not instead warn users of problems ahead of time BEFORE they install Ubuntu? Rather than clog the forums with problems that exist and no one bothers to fix. That would really bring out a fanbase as I have yet to see a Linux distribution that does this. If you want a user base why not start by building a loyal one rather than an irate one. I'll even throw an idea at you:[/B]

**When you Hit "Try Ubuntu" it warns you of problems ahead of time judging by the hardware detected which matches with a model number.** It's scary I know considering how much hardware goes into computers thats almost exactly alike but at least then maybe that could require some user input on what model they are using. If you are smart enough to TRY UBUNTU what would stop someone from this?

---

### Post by Yellow Pasque on 2013-10-11
> Please do some research and study the problem before jumping to conclusions on what could or may fix it.
I did. Don't jump to conclusions that I didn't.

> Your post count looks impressive, but your knowledge in troubleshooting and gauging problems is certainly misguided and misdirected.
Sigh... You hide your post count and people poke fun and call you "hidden beans" or whatever. You don't hide your post count and people "compliment" it by implying you're an ignoramus.

> Temujin my laptop only has the nvidia display adapter
Update the PCI ID database, and look at lspci to be sure:
```
sudo update-pciids
lspci | grep VGA
```

> Also, the sound is not "HDA Intel"
From my googling, it looked like a Realtek ALC269 codec.  Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

