---
title: "How to shred data on an external hard disk?"
date: 2014-06-09
forum: General Help
---

### Post by davy jones on 2014-06-09
I have an old laptop and its screen doesn't work. So I wanted to sell it off after shredding the data on the hard disk. I connected the hard disk to another laptop and tried the following command.

```
shred -vfz -n 5 [volume]
```

But it gave a message saying that the disk was not writable. I didn't have permission to do it. Is it because I should be using sudo? Or is it something else?

Is using the "right click->shred" option in Windows 8 the same as this? Right now I've formatted the drive two times. It was in EXT4 format so I formatted it to NTFS first and then again to EXT4. Will anyone be able to recover my data?

Need help with this quickly. Thanks.

---

### Post by sudodus on 2014-06-09
> **davy jones said:**
> I have an old laptop and its screen doesn't work. So I wanted to sell it off after shredding the data on the hard disk. I connected the hard disk to another laptop and tried the following command.

```
shred -vfz -n 5 [volume]
```

But it gave a message saying that the disk was not writable. I didn't have permission to do it. Is it because I should be using sudo? Or is it something else?

Is using the "right click->shred" option in Windows 8 the same as this? Right now I've formatted the drive two times. It was in EXT4 format so I formatted it to NTFS first and then again to EXT4. Will anyone be able to recover my data?

Need help with this quickly. Thanks.

If your drive is reasonable new, you should be able to use ***hdparm*** or ***DBAN*** to wipe it in a more efficient (and secure) way compared to shred. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2124829"]
best way to wipe a drive[/URL]

-o-

But it is certainly possible to use shred. For almost all purposes concerning a private person, you need not overwrite the data several times. Once should be enough. It is different if you want to wipe the drive with military level security.

Read the info page about shred.

info shred

-o-

Repeated formatting does not remove the data for the disk surface.

Finally, yes, *I would use shred with sudo*, but consider using hdparm.

---

### Post by davy jones on 2014-06-11
Thanks for the quick reply. Those methods seemed a little to complicated for me, but I've run shred with sudo and it seems to be working. I've reduced the number of times to overwrite from 5 to 3. It's a 233 GB hard disk. How long should it take? And does it mean that all 4 passes will take place three times? If yes, then I really need to cancel it after the first 4 passes are complete because it's taking too long!

---

### Post by sudodus on 2014-06-11
I think what you mean by all four passes is the three specified random overwrite passes and one final zeroising pass. This should be run ***once***, not three times.

Wiping with hdparm may look a little complicated, but once you understand it, it will run faster, much faster than shred (maybe ten times faster and I think better wiping, because it is done at a very low level, close to the hardware (how the logical data blocks are mapped to the physical blocks)).

---

