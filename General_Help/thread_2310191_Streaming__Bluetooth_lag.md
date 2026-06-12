---
title: "Streaming / Bluetooth lag"
date: 2016-01-16
forum: General Help
---

### Post by nickTaylor1181 on 2016-01-16
Hi all.


Bit of an odd one (for me at least). 

New Install on a new laptop. I'm using Ubuntu 15.04 because 15.10 generated a ton of start-up errors, and after about 3 boots it couldn't get to the desktop.

So I reinstalled an older version... seems ok, a couple of bizarre quirks, but the only thing that's really bothersome is:


When I try to play a youtube (or any other streaming video) using bluetooth headphones, it goes fine for about 4 seconds, then splutters a bit, then comes back with 1 sec or so of lag.

Doesn't happen if I use the same headphones with a wire, or on a different PC. Doesn't make a difference what browser I use. Doesn't happen if I play a video that's on the local system... and it seems to not be quite so bad if I stream the youtube vid via VLC... although that's no way to live etc.

What it "feels like" is some sort of cache/buffer issue... ie: Bluetooth and streaming are fighting over the same bit of cache/buffer memory, and it runs out. 

Obviously I have no idea what I'm talking about. That's what it feels like though.


I'm not sure what I need to provide in the way of diagnostics... If anyone can help, I would be most eternally grateful.




Nick

---

### Post by Bucky Ball on 2016-01-17
I'll just throw this in. 15.04 has about two weeks support left at which stage you are going to need to upgrade to a supported release anyway. Forget 15.04 (or do a net upgrade to 15.10 while you can - Software & Updates> Updates tab> Notify me of new Ubuntu version: For any new version).

If 15.10 has issues, you could try asking for help here with them or try the LTS release, 14.04 LTS, which is supported until 2019 and is upgradeable directly to the next LTS, 16.04 LTS, support til 2021, in the second half on 2016.

---

### Post by nickTaylor1181 on 2016-01-18
Yea I know... when I first tried to set this machine up, I started with 15.04 (and bluetooth didn't work at all), then someone suggested I upgrade to 15.10 - which I did.

After that, every time I tried to boot I'd get a ton of error messages (to do with video apparently), which eventually wound up with me not being able to get to the desktop at all. 

I had to reinstall from scratch, which for me is killer time-consuming. It takes me about a week to get a new machine set up. I really don't want to have to go through all that again.

---

### Post by nickTaylor1181 on 2016-01-18
Hmm... okay just removed device from ubuntu bluetooth and installed blueman, which seems to have solved it.

---

### Post by Bucky Ball on 2016-01-18
Oh, well. We'll see what happens when you upgrade to 15.10 in a month or less, if you do. If you have any problems with 15.10 in future probably a good idea to look for help here rather than using an unsupported release (which we can't help much with). You might have saved yourself a lot of time and messing about by doing so in this instance (you probably had the wrong driver in the 15.10 kernel or the wrong proprietary driver installed. Did you agree to third-party updates during install? Don't next time.) Graphics problems at install time are generally pretty easily fixed.

Perhaps install 15.10 on another partition and start trying to fix it now in preparation because come February, help will dry up for 15.04. 

Thanks for marking as solved and good luck whatever you choose to do.

---

