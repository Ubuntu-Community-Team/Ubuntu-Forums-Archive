---
title: "Minimal Bash-like line editing is supported after Ubuntu 18.04 installation"
date: 2018-07-10
forum: General Help
---

### Post by lendon210 on 2018-07-10
I've just bought a brand new SSD and installed Ubuntu 18.04 LTS on  it. After the installation is completed successfully it asks to restart  upon which it presents the Minimal Bash-like line editing is supported  screen.
  What could be the cause of this issue? The SSD only has Ubuntu  installed on it. Secured Boot is disabled and the boot mode is set to  UEFI in the BIOS. Previously on my mechanical hardware it installed it just fine.

-- Edit; Just installed Windows 10 on the SSD and it is working just fine so it must not be a hardware issue.

---

### Post by Impavidus on 2018-07-10
That screen indicated grub couldn't find its configuration file.

I suggest [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") to get some more diagnostics. You can run it from your live disk that you used for installation. But as you now installed Windows to that SSD, I expect all traces of Ubuntu have gone, so you first have to try and install Ubuntu again.

Edit: Only create the Boot-info summary and share the link with us.

I see there's a whole bunch of people with these grub problems on the Ubuntu forums this morning (European time). There was a grub update this morning too. Related?

---

### Post by lendon210 on 2018-07-11
I think you are right on the money. I've just reinstalled but this install opted to not enter the Wifi password or connect an ethernet cord and Ubuntu 18.04 installed correctly. Just as a test I decided to reinstall Ubuntu again this time with the internet connection and it gave the same "Minimal Bash-like line editing is supported" error".

It seems like there was a recent update on grub that seemed to broken the installation for some people.

Thanks again for your help!

---

