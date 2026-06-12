---
title: "I can't access encrypted ubuntu with the correct password"
date: 2022-04-22
forum: General Help
---

### Post by aaaaahhhkllll on 2022-04-22
I installed ubuntu a long time ago, I don't remember the version, I chose to encrypt and spent some time entering the password and everything worked fine.
A hint: One day I changed the keyboard and I realized that I could not enter, I returned to my old keyboard and entered without problem.
One day liquid fell on that keyboard and the keys were damaged and I could no longer access the system.
I bought a keyboard exactly the same months later (because I had the computer without touching it) and it does not allow me to access it either.


It happens this way:


1 - Please unlock disk sda6_crypt
2 - I enter the password
3 - Cryptsetup: ERROR: sda6_crypt: cryptsetup failed, bad password or options?


I have already tried to access the disks tool through live session and decrypt the partition and it does not work either.


I have thought that since I know the correct keys what is happening is that the encoding or something is different.
Is there a way to generate for these keys all the conventions of keyboard layouts and encodings?


or any other solution?


Thank you very much.

---

### Post by TheFu on 2022-04-22
Just a guess.

With the old keyboard connected and perhaps the new one connected, you could add another unlock method. LUKS supports 8 slots for this.  An existing passphrase must be known to add another.  Use the old keyboard to enter the existing passphrase and the new keyboard to enter the new passphrase into a different slot.

If you really want to trace this down, you can use a program to capture the keycodes from the old and new keyboard and compare them.
Also, the locale and language settings probably need to be the same.

**cryptsetup** is the command to work with LUKS.  The manual page for that tool is relatively clear.  The option I think you'll want is *luksAddKey*. Be certain to specify the --key-slot .  I always dump the header info to be certain that I've got the correct unused slot.

Some of the fancy new keyboards do odd things with their keycodes.

---

### Post by aaaaahhhkllll on 2022-04-22
Thank you very much for the reply!
I already tried to use that command to add a new password but I have the same problem, to add a new password it asks for the previous one and the previous one does not accept it.

any other idea?

---

### Post by TheFu on 2022-04-22
Use the old keyboard to enter the old passphrase.
Use the new keyboard to enter the new passphrase.
Multiple keyboards can be connected concurrently.

If you changed the locale or language, all bets are off.

---

### Post by aaaaahhhkllll on 2022-04-22
the old keyboard does not work because liquid fell on it, I have one exactly the same bought second hand but it does not accept the password with it.

---

### Post by TheFu on 2022-04-22
One more idea.  

Can you bring up a screen keyboard (accessibility options) and enter the passphrase?  This is from the *Try Ubuntu* boot.  From that environment, it might be possible to add another passphrase.

Besides that, I'm out of ideas.

I know that accessing encrypted storage from a different machine is possible. I've done it - pulled a drive from a laptop, put it inside a USB enclosure, and connected it to a desktop. Then used caja (that's a file manager) to click enough to get the passphrase requested, entered and the partition mounted.

Of course, having good backups would make most of this a non-issue, minor inconvenience only.

---

### Post by aaaaahhhkllll on 2022-04-26
Hello, thanks for answering


The problem is that I know what the keys are pressed to define the password but I don't know what is stored (because I don't know what keyboard layout and encoding was used) so the visual keyboard is of no use to me I write the keys but no enters.


the only thing that occurs to me is if there were a program that for certain pressed keys would generate the output of all the possibilities, Sound like that to you?

---

### Post by TheFu on 2022-04-26
**xev** is the program, I think.  It works with X/Windows. Doubt it will work with Wayland.  That's for a GUI keyboard input.  Console key input settings can be different, but usually aren't.

---

### Post by aaaaahhhkllll on 2022-04-27
xev???? where can I download? I don't find
thank you

---

### Post by TheFu on 2022-04-27
xev is part of the normal X/Windows programs.  I can't say I've ever seen a desktop system that didn't have them installed the last 25 yrs.  Yep. Just checked my 20.04 and 18.04 desktops. Both had **xev**.  It is in the Canonical repos, probably as part of X/Windows Client Tools.

```
$ dpkg-query --search   /usr/bin/xev
**x11-utils**: /usr/bin/xev
```

So that's the package name for you. Lots of little tools for knowing X/Windows in there.

---

