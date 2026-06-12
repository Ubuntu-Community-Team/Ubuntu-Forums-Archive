---
title: "10 Ubuntu dual boot. Ubuntu gone."
date: 2017-01-10
forum: General Help
---

### Post by hoppings on 2017-01-10
What has Windows 10 done!!
I had managed to put Windows 7 on a brand new HP laptop that originally came with Windows 10. I had heard that Windows 10 made things very difficult for Linux users. They were not kidding!

Even though I got Windows 7 from HP legally, it suddenly turned the screen black and a notice popped up saying it was not genuine.
HP told me I needed to reinstall Windows 10, which I reluctantly did.

Now, my Ubuntu is gone, and I cannot even gain access to the BIOS to re-install it. My previous option of booting from other media has been removed.

I have been on with it all day and tearing my hair out.

Thanks for nothing Microsoft, now I have a brand new useless computer.

Does anyone have any ideas how I can get back to Ubuntu?

---

### Post by coffeecat on 2017-01-10
Post moved to own thread and relevant title applied.

Please do not hijack other threads. The thread you posted to had little in common with what you are describing. It is always better to start your own threads.

---

### Post by oldfred on 2017-01-10
You have to gain access to UEFI/BIOS first.

Many vendors now assume you only need it from working Windows. But what about Windows when it breaks.
UEFI has a fast boot which is different than Windows fast start up. Both should be off.

       UEFI fast boot fwsetup
[URL="http://askubuntu.com/questions/652966/unable-to-access-bios-menu-after-installing-windows-8"]http://askubuntu.com/questions/652966/unable-to-access-bios-menu-after-installing-windows-8
[/URL]
  
You may be able to access UEFI if you do a full power down. If laptop also remove battery. If battery not removeable you should have a tiny pinhole reset button.
And then hold power switch for 10 sec or so to fully drain all power. Then you need to quickly press correct key(s) to get into UEFI/BIOS on start up.


 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

[URL="http://askubuntu.com/questions/652966/unable-to-access-bios-menu-after-installing-windows-8"]
[/URL]

---

