---
title: "Installing to Raid:"
date: 2008-05-03
forum: General Help
---

### Post by zebadee on 2008-05-03
Hi :)
I 1st tried installing to my main PC the latest version of ubuntu.
However got nowhere (except a corrupt boot up).
Is this because the drives are Raided ( Raid 0 )?
The install appeared to be going just fine.
On reboot however there was problem.
As I result I couldn't boot at all.
I've sorted this out.
But wonder if I am right in my conclusion..... That...
ubuntu sees the drives as individual always.
Regardless of the Raid set up.
I have now installed to a 2nd PC.
Non-Raided. :lolflag:

---

### Post by ddrichardson on 2008-05-04
There are a couple of pointers [here]("http://www.linuxquestions.org/questions/ubuntu-63/install-ubuntu-on-sata-raid-0-dmraid-dual-boot-windows-xp-409595/") and [here]("http://linuxmafia.com/faq/Hardware/sata.html"). I've heard good things about this [howto]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto") on the Indian wiki, if it works well let me know and I'll look into adopting it into the system docs or community wiki.

---

### Post by fjgaude on 2008-05-04
To the best of my knowledge, you can't boot from a raid0... when you think about it: how could you? The data and all programs are split been the drives with the OS, so how could mdadm or md assemble to get a whole stream.

We are talking about software raid, eh?

---

### Post by zebadee on 2008-07-19
Hi :)
Gave up on Raid, but also found I had to make sure the SATA drive I installed to.
Was first in line, to avoid boot problems etc.

---

### Post by Mister.Vash on 2008-07-19
You should be able to do the raid, see the following links

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I've had enough hard drives go out that I think it is well worth it for any data you consider important.  A combination of raid and data backups sure makes life easier when you loose a drive

---

