---
title: "samba share stuck at loading"
date: 2020-11-30
forum: General Help
---

### Post by sniper8752 on 2020-11-30
I have a samba folder share on my network.  I try to load it from my Lubuntu desktop, but it just stays at "Loading folder..." and never loads the share.  There are no errors.  I spun up my Windows 10 machine, and it loads the share just fine.  Could it be something with cached credentials/timeout?

---

### Post by guiverc on 2020-12-03
You haven't provided much detail for us to help you with.

What release of Lubuntu are you asking about?  Is it legacy with LXDE, or modern with LXQt, release details are a start.

The only experience i have with samba folders is when mounted first via command, I like it as the messages appear on the terminal after command so I can at least get clues. With a terminal, I'd need to look in logs (system logs, `dmesg` or `journalctl` but as I don't know your release, this is generic advice only).

Did you verify the network connection is valid (`ping` or echo requests?, are there differences in the w10 machine and the Lubuntu one, ie. w10 has a different IP address that is allowed access to samba, the Lubuntu is different as isn't on the *allowed* list for access etc)

Samba security has increased to keep it secure for windows clients; so does your box meet those requirements (what level of security are on you? starting point is your *unstated* release).

I'm no expert in SaMBa, as I use NFS primarily, but your release details is where I'd start (inc. kernel stack in use, GA or HWE if an LTS release; I forget if it's the kernel or samba package that causes the default security level to be chosen).  I recall at one stage, commands that mounted the SaMBa shares needed to be changed as I *release-upgraded* my boxes, but I forget when that was done sorry (was some time ago, but I'm now on *hirsute* so you're likely behind me).**

---

### Post by sniper8752 on 2020-12-04
OK, so I was right.  I attempted to access it again, it prompted me for my credentials, and now it is showing the files once again.  
Is there any way to prevent this from happening in the future where it doesn't prompt, and silently fails?

---

