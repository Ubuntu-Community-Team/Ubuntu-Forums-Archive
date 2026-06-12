---
title: "logging hd spindowns"
date: 2008-02-02
forum: General Help
---

### Post by phasmatis on 2008-02-02
I'm currently running an apache server on a cheap 40GB laptop harddrive I had lying around. Needless to say, I'm a bit concerned about keeping it running constantly.

in /./dev/ I have no HDA.. for some reason the drive seems to be mounting as SDA, which is weird because it's definitely an IDE drive.

Anyway, for starters I'd like to keep a log of any time the harddrive spins down, to see if it is actually happening.

And secondly, any info or tips on how to make hdparm work safely would be appreciated.

thanks in advance.

---

### Post by PinkFloyd102489 on 2008-02-03
SCSI devices are listed as sdx, which your HD is probably a SCSI. Mine displays the same way, dont feel bad. When I had my drives plugged into a PCI jumper card, they appeared as hdx.

---

### Post by accatagon on 2008-02-03
For some reason Ubuntu mounts IDE drives as sdx. Don't ask me why, but I don't think you need to worry about it either, because it happens on my comp as well, and Debian definitely mounted them as hdx (on the same system with the same hard drive). 

I'm sorry, but I don't know much about the hard-drive events. I suspect that you might be able to use dmesg. 

I'm not entirely sure what you mean by "make hdparm work safely." Is it inherently dangerous? Some of the operations are. . . but, well, you are messing with your hardware.

I'm probably not the best person to ask about this question, but I figure I can at least assure you that the sda thing is normal. . . for Ubuntu at least.

---

