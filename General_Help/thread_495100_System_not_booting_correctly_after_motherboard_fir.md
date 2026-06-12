---
title: "System not booting correctly after motherboard firmware update"
date: 2007-07-07
forum: General Help
---

### Post by johnsd8 on 2007-07-07
I recently purchased an Athlon X2 chip, and in order to get cpu frequency scaling to work, I needed to update my bios on an MSI Nforce4 board.

After doing so, my system is not behaving nicely, and I'm having trouble tracking down what's going on. None of the logs show too much. I have both  2.6.17-11-generic installed, for dual proc support, and an x386 variety as well. Both sporatically will make it to X login, but sometimes die before that, hard locking the console. If networking has been loaded, I can still ssh in, but I'm still amiss to what is misbehaving.

I know this isn't a lot to go on, but I'm having trouble isolating what the problem is.

When X does start, gnome crashes, powernowd still says that frequency scaling is unsupported, and no window decorator loads. I can get a terminal by launching one remotely to the local server, lots of things are crashing leaving core dumps in my home directory.

I have a complete nightly incremental system backup stored for the past months, but I wouldn't know what would need to be restored, if anything.

(Sorry about the title, bad cut and paste)

---

### Post by tnseditor on 2007-07-08
I don't know if you have tried this, but try Feisty.  If it works then you could install it and then import everything you have backed up.

---

