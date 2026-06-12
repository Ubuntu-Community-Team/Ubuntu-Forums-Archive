---
title: "Upgrade from Ubuntu Server 14.10 to 15.4, now not bootable"
date: 2015-04-25
forum: General Help
---

### Post by stormthirst on 2015-04-25
My PC has 2 drives, a 1tb and an 2tb drive. For historical reasons, the 1TB is an LVM bootable drive which I recently extended with the 2TB drive. Everything was fine, it was fast and stable, though a relatively recent install.

I was prompted to 'do-release-update' last night. Seeing no reason not to, I did. On reboot, it was getting a lot of processes hanging during the start up, something it never did before.

I downloaded the most recent ISOs and tried to do a recovery. I'm not sure where I went wrong, but now it won't boot. Now when I try to recover the system, it lets me mount the LVM root, but for some reason won't write to the /boot partition. It doesn't give me an error message.

The data is, as far as I can tell at the moment, recoverable so I'm in the process of trying to move it off the system and onto several others I have available to me.

I'd rather not have to do that at all, but if a complete rebuild is the route I have to go, then I shall.

Any advice on where I can go to start recovering this system?

---

### Post by Tadaen_Sylvermane on 2015-04-25
Get your stuff off of it and install 14.04 LTS. Using anything other than an LTS for server purposes is dumb, to be blunt. Primarily because so much typically depends on a server, having to do an entire software upgrade every 6 months is just asking for problems. Servers are meant to be stable and left alone once running for the most part. Using such a short release cycle version + server doesn't work.

---

### Post by stormthirst on 2015-04-25
Yeah. Thankfully it's 'only' my home media server, and the contents of the drive are retrievable. I was hoping to get it bootable again, but I guess not.

---

