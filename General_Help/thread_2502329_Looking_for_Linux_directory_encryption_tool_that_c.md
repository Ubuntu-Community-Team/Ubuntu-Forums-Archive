---
title: "Looking for Linux directory encryption tool that can use a hardware key"
date: 2024-11-10
forum: General Help
---

### Post by Advait on 2024-11-10
I'm using Ubuntu 24.10 on an AMD laptop.

I want a Linux directory or vault encryption app that can use a USB hardware key like a FIDO2 key or Yubikey. Hardware key to unlock the directory or vault.

Anyone know of such an app? I prefer a GUI app.

Currently I’m using Cryptomator but it only uses passwords.

---

### Post by HermanAB on 2024-11-10
LUKS can do it.  Start by trying to read the cryptseup man page and google LUKS cryptsetup guides - there are many.

---

### Post by Advait on 2024-11-10
> **HermanAB said:**
> LUKS can do it.  Start by trying to read the cryptseup man page and google LUKS cryptsetup guides - there are many.

I looked thru that man page and some setup guides. Unfortunately, I'm a tech noob and they made zero sense to me. Way way above my head. I would have no idea where to begin. The only commands I know are apt update and apt upgrade.

Have any suggestions for a tech noob like me?

---

### Post by dragonfly41 on 2024-11-10
I offer a suggestion that you create (as a start) a free Proton Mail account.

Not only does this offer secure communications with other Proton users but you can leverage Proton Drive to upload desktop folders/files into your Proton Drive to be shared with designated users selectively.  All encrypted end to end in zerotrust framework.

Your orginal folders/files can be on your desktop.  I use a removable external caddy with an SSD for this purpose.  So you retain a physical backup of online encrypted vault. Of course accessing encrypted vault requires Internet access. There are multiple other features in Proton such as Pass, VPN.

---

### Post by Advait on 2024-11-11
> **dragonfly41 said:**
> I offer a suggestion that you create (as a start) a free Proton Mail account.

Yep, been using Proton Mail for a few years; it's great.

---

### Post by dragonfly41 on 2024-11-11
Bravo. And yet you write ..
> [COLOR=#000000]Have any suggestions for a tech noob like me?[/COLOR]
But have you looked at, indeed leveraged, Proton Drive? Or Proton VPN?

---

### Post by HermanAB on 2024-11-11
Setting up an encrypted directory is not simple and there is no way to make it simple, so you have to experiment till you understand it and get it to work.

It would probably only take about three commands, but for me to explain it to you, I would have to do it myself first and I feel too old and and sick to read up and test it at this moment :)

---

### Post by Advait on 2024-11-11
I'm now researching Veracrypt and Proton Drive. I'll report back soon.

---

### Post by dragonfly41 on 2024-11-12
Add Tresorit to your research. I am researching hybrid Proton Drive and Tresorit.

P.S. Consider using Obsidian as front end desktop vault to sync with Proton Drive and/or Tresorit. Think of a pipeline.  Keep Obsidian vault (clear text such as Markdown and other assets, images) in removable SSD device in caddy to lock away.

---

### Post by TheFu on 2024-11-12
LUKS on an external USB storage device that automatically unlocks when
connected to a specific system:

* Creating Part1: [Https://youtu.be/vk9Z2_rEUak](Https://youtu.be/vk9Z2_rEUak) (nerds should find this very funny)
* Accessing Part2: [Https://youtu.be/ELEVo6SbYl0](Https://youtu.be/ELEVo6SbYl0) seems to be it.
* Text version: [Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it)

---

### Post by Advait on 2024-11-12
I just remembered that I have an old Backblaze account. And Backblaze supports Yubikey (but unfortunately not FIDO2). I'm also now researching that option.

---

