---
title: "mistake with grub customizer makes my laptop only boot to UEFI settings"
date: 2020-12-01
forum: General Help
---

### Post by jmbrown2 on 2020-12-01
Hello, 

I've been trying to figure out how to get my computer to boot from a usb drive and haven't been having much luck.  I was also having a hard time getting into the UEFI settings when it's booting. So, using grub customizer, I changed it to boot to UEFI first.  I didn't really think this through and now it's stuck in this cycle of booting to  the UEFI menu over and over without ever booting from the usb drive or from ubuntu.  

Exactly what I did:

Under list configuration, I moved "UEFI firmware settings" to the top of the list.  
Under general settings I changed Predefined from ubuntu to "advanced options for ubuntu>ubuntu, with Linux 5.4.0-generic"

I changed the predefined setting out of curiosity, and it did allow me to enter the UEFI menu.  I changed the boot order in that menu, too.  

So now I'm feeling pretty dumb and I can't get my computer to boot up.  

Is there any way that I can get past this in order to change back the settings that are causing the problem?  

I really appreciate any help!   Thanks.

---

### Post by ajgreeny on 2020-12-01
If your computer is now booting to the UEFI settings surely you can again change the boot priority.

You obviously need to put the Ubuntu option in those settings as the first boot priority, but having never used grub-customiser I have no idea what it is capable of nor what you see when using it.
What I do know is that it can make changes to grub configuration files that are not easily repairable with normal configuration file edits mainly because it makes fairly fundamental changes to grub.

Whatever you do manage to do to get back to Ubuntu, please remove grub-customiser as soon as you can and don't use it again.  This may sound odd, as it is a package in the repos, but there have been several posts similar to yours asking for help to overcome problems created when using grub-customiser. Another of our forum staff, oldfred, is the expert in these matters and hopefully he will soon see this thread and be able to help you a lot more than I can.

---

### Post by oldfred on 2020-12-01
Do you have UEFI fast boot on.
That is different than Windows fast start up.
Fast boot assumes no system change to hardware or software configuration, so it immediately boots and since so quick, you normally do not have time to press any key to choose UEFI boot menu.
Often then full "cold" boot or power shutdown, disconnect all power including battery if laptop, hold power switch for 10 sec or so to drain all power.
Then when booting press correct key to get into UEFI boot menu or UEFI settings.

What brand/model system?
Many require you to turn on or allow USB boot. Review UEFI settings.
USB boot would not be in grub or grub customizer normally, but you still would have to be able to boot either internal drive's grub or USB flash drive to choose a new grub menu item.

---

