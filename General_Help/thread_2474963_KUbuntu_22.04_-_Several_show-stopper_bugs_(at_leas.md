---
title: "KUbuntu 22.04 - Several show-stopper bugs (at least for me)"
date: 2022-05-12
forum: General Help
---

### Post by LVDave on 2022-05-12
I use a Dell Latitude 5480 laptop, which runs Kubuntu 20.04 perfectly. I decided I'd upgrade to 22.04 with a clean install on a new SSD. The install went flawlessly, and after it completed, I went about testing. I soon found two showstopper bugs (at least for me), things that worked perfectly in 20.04 that do NOT work in 22.04. These being sound and OpenVPN. The system uses a bog-standard Intel Corporation CM238 HD Audio Controller (rev 31) that works perfectly in 20.04 (and previous LTS). For some reason, Pulseaudio apparently does not see the interface however an lspci does show the interface and all the sound stuff in lsmod seems to be there, but pulse only presents a "dummy interface", ie: No sound. As for Openvpn, I set the configuration precisely the same as i've done many times on 20.04, but Openvpn puts out an "Openvpn service stopped", and I don't see any
smoking guns when I check the log. Worried that I had some failures on the laptop, I removed the new 22.04 disk and put the working 20.04 disk back, and everything just works again like before. Guess I was stupid to try to use a just released OS. Posting this to see if I'm the only one seeing this.

---

### Post by SeijiSensei on 2022-05-12
I had some wobbles with 22.04 when I was trying it out. I've since switched to [KDE Neon]("https://neon.kde.org/"). It's built on 20.04 but with the most recent Plasma desktop. I've had to add a few applications like libreoffice and kate, but apt works fine.

---

### Post by LVDave on 2022-05-12
Thanks for the tip.. Since the Kubuntu 22.04 is snafu, I'll give KDE Neon a try. Since I use only KDE (HATE Gnome) I'd been thinking about trying KDE Neon. Will give it a try..

---

