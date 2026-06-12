---
title: "No Autoboot after Updating Lubuntu"
date: 2015-05-26
forum: General Help
---

### Post by Bonfire_Dog on 2015-05-26
Hello, thanks for any help you can offer; this is just the latest hair-pulling incident in my flirtation with Linux...

I have a little box running Lubuntu for remote file access etc. It had Lubuntu 14.x (sorry I cannot provide exact version) running tickety-boo. I received a dialog box to update Ubuntu to the latest version (I believe 15.04; in hindsight I should have realised this might break something, as I am running Lubuntu not Ubuntu)... after updating and rebooting Lubuntu no longer autoboots, as it did before; now, a Grub2 menu appears.

When I load the default, 'Ubuntu', I just get a black screen and nothing loads.

I CAN boot into 15.04 Lubuntu if I select 'Advanced Options' in Grub manually and select '[COLOR=#111111][FONT=Consolas]Ubuntu, with Linux 3.16.0-36-generic'

[/FONT][/COLOR]This does seem to load the updated Lubuntu with all my installs, settings etc. intact. However I seem to have no internet access in this option.

Can anybody help me get my autoloading Lubuntu back and internet access? Perhaps more importantly, explain to me WHY what I did made such a boo-boo? I'd like to learn. 



My only option at the moment is to boot the Lubuntu liveCD from USB and reinstall the OS; however, if I did this how can preserve my files and settings? 

Thank you in advance.

---

### Post by timotheus3 on 2016-01-14
maybe review your boot logs, may be a good place to start, im no expert, so i cant offer much help

im fairly sure that when the software update says "Ubuntu" it knows your running Lubuntu and should update accordingly..

also this obviously dosent help your current situation but always make sure you backup anything important before upgrading, and it pays to read the Documentation online in regards to upgrading to make sure everything goes smoothly

---

