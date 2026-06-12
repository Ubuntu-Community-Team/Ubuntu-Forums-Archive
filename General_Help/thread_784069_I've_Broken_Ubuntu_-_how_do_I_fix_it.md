---
title: "I've Broken Ubuntu - how do I fix it?"
date: 2008-05-06
forum: General Help
---

### Post by rubbermyroof on 2008-05-06
Hi all, I've posted this a few days back and had no answer so I've distilled this a bit and hope someone can help me cos I'm totally stuck!

***
I had (have) Gutsy Gibbon installed on its own partition, so that I could boot into that (or Win2K pro, after the BIOS screen). 

Not knowing it would cause such problems, I closed down Ubuntu many times when I wanted to go into Windows, before it had started up properly. 

Now, Ubuntu refuses to run. It come up with various problems as it loads which it labels "fixed" one by one, then it loses interest and gives me the Black Screen of Death before it has even started up.

So, I downloaded the Heron .iso (from Oxford Uni mirror)and burnt it to CD in the hope of fixing things or installing over the last Ubuntu. (The home burnt CD of the download boots up OK but when I select the 'check the CD' type of option, it says that 1 file has issues. I've downloaded it from Italy (mirror) and again have precisely the same problem (- is there an issue with the copies stored there? 

(I've now ordered a 'proper' disk online).

Anyway, trying (using that slightly corrupted version) to install the Heron, it gets as far as showing a progress bar but then loses interest and gives me a Black Screen of Death.

I need my Win 2K for business daily so can't do a Format over the whole HD and start again, but would so much like to move over to the Heron as soon as possible so any help as to how to get it installed would be appreciated. How can I format just the Ubuntu partition to start again, given that Windows doesn't seem to see it? And then what would I have to do to the Boot-up menu so that the selection menu sees the newly installed Ubuntu version rather than expecting the old one? (I'm a bit worried about breaking Windows too then I'd be really stuck without doing an entire system re-install) Any help really appreciated!

Cheers, Jules the rubberroofer

---

### Post by TeoBigusGeekus on 2008-05-06
First of all, you should have downloaded Hardy Heron through torrents. The torrent client checks the integrity of the image automatically.

When you receive your cd, or, if you are impatient enough and download it now, choose manual install. Select your previous Ubuntu partition and delete it.
Then create a partition for your file system (preferably ext3 format, mount point /), a partition for your home folder (again preferably ext3 format, mount point /home) and a partition for swap, about 1.5~2 times your ram. The Ubuntu installer will do the rest.

---

