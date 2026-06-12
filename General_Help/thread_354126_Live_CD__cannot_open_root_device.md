---
title: "Live CD:  cannot open root device?"
date: 2007-02-05
forum: General Help
---

### Post by mikeglaz on 2007-02-05
I boot from this CD.  I select **Start or Install Unbuntu**.  Then the Ubuntu logo appears with the progress bar below it.  Then nothing.  The screen goes blank, the CD stops spinning.

I tried hitting F6 and typing **break-bottom.** And here is the line it hangs on:

**VFS: Cannot open root device "<NULL>" or unknown-block(8,1) Please append a correct "root=" boot option kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(8,1)**

I have the K8V SE Deluxe motherboard and ATI Radeon 9800 video card if that helps.

Any ideas??

---

### Post by ed-j on 2007-02-05
I am a Novice, so I can only give some moral support!

Is your CD player working properly?
Does the light stay on after the drive spins down?
Is the cabling ok?
Is there any way to test that the CD you have is ok?

Best I can do. Post if you think it might help!

---

### Post by Brunellus on 2007-02-05
> **mikeglaz said:**
> I boot from this CD.  I select **Start or Install Unbuntu**.  Then the Ubuntu logo appears with the progress bar below it.  Then nothing.  The screen goes blank, the CD stops spinning.

I tried hitting F6 and typing **break-bottom.** And here is the line it hangs on:

**VFS: Cannot open root device "<NULL>" or unknown-block(8,1) Please append a correct "root=" boot option kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(8,1)**

I have the K8V SE Deluxe motherboard and ATI Radeon 9800 video card if that helps.

Any ideas??
possibly corrupted CD.  Verify the iso and burn another one, this time using the SLOWEST POSSIBLE SETTING.

---

### Post by mikeglaz on 2007-02-05
The CD is fine.  I tested it with the utility that is available while booting from the CD.

---

### Post by r4ik on 2007-02-05
The low speed burning is going to be an issue in the future my lowest setting
is 16x with Nero that is.

---

### Post by Brunellus on 2007-02-05
> **mikeglaz said:**
> The CD is fine.  I tested it with the utility that is available while booting from the CD.
that's very odd, then.  are you using the default edgy desktop CD?

---

### Post by mikeglaz on 2007-02-05
Yes, I have the default Edgy Eft 6.10 CD.  Someone just suggested that the Dapper Drake 6.06 doesn't have this problem...

---

### Post by Brunellus on 2007-02-05
> **mikeglaz said:**
> Yes, I have the default Edgy Eft 6.10 CD.  Someone just suggested that the Dapper Drake 6.06 doesn't have this problem...
I agree, try running Dapper.  Be sure to get the point release.

If you *do* decide to install, you could conceivably dist-upgrade to edgy.  The current edgy kernel will be different from the one shipped on the CD images, and you might be able to bypass your install problems that way.

---

### Post by mikeglaz on 2007-02-05
What is the 'point release'?

---

### Post by Brunellus on 2007-02-05
Dapper released initially as 6.06.  Subsequently a new "point" release for Dapper was released, 6.06.1.  It is this latter one that I recommend.

---

### Post by mikeglaz on 2007-02-05
ok, I tried Dapper and same problem.  When I **break=bottom** here's the error message it gets stuck on:
[B]
VFS: Cannot open root device "<NULL>" or unknown block (8,3)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,3)[/B]

---

### Post by Brunellus on 2007-02-05
I'm moving this thread to a more competent forum, and also changing the title.  This is a very strange problem indeed.

---

### Post by mikeglaz on 2007-02-05
Ok, I tried booting on my brother's computer with my CD-ROM.  It boots fine.  So the CD-ROM drive is not the problem.  Then installed an IDE drive on my computer (vs. SATA) and it didn't work.  Then I tried a new video card in my system (instead of my ATI) and nada.

Then I tried Ubuntu Dapper - no luck.  Then I tried Edgy in Safe Graphics Mode - same problem.  Finally, I tried Dapper in Safe Graphics Mode and it worked.  So I have everything up and running.  The only problem now is that my resolution is set to 1280x1024 @ 60Hz.  I can't change it to anything else or the system crashes and I'm teleported back to the signon screen.

mike

---

