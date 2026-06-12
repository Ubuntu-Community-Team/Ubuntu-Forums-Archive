---
title: "Password Issue"
date: 2015-05-21
forum: General Help
---

### Post by Safeeq on 2015-05-21
I am unable to logon or change the password on ubuntu 1204 LTS installed on Windows 7. I tried following the below link to reset the password but when boot ubuntu on recovery mode and  select drop to root shell prompt > It's asking me to enter the root password and its not accepting the root password so I am not able to login to ubuntu or change the password. 


[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Any help would be appreciated.

---

### Post by Vladlenin5000 on 2015-05-21
Perhaps you should find a method to remember your passwords... Here's a memory refresher: [http://ubuntuforums.org/showthread.php?t=2224475](http://ubuntuforums.org/showthread.php?t=2224475)

---

### Post by Safeeq on 2015-05-21
That issue was still exists - I was able to login as guest but now all of sudden, I am having issues logging in as guest too.

---

### Post by Vladlenin5000 on 2015-05-21
If you have been working as guest then probably there's nothing you need to backup. So, why not just reinstall?

---

### Post by Safeeq on 2015-05-22
How to reinstall, should I uninstall the ubuntu and reinstall it? If so, how to uninstall it. I will google and try find out the best way but if you can share some details- that would be helpful. Thanks for your help.

---

### Post by Vladlenin5000 on 2015-05-22
Operating systems don't need to be "uninstalled". Operating systems reside in partitions in such way that when those partitions are removed and/or formatted the old OS is gone. 
You can boot the installation media and just install as usual. It isn't that much different from a bare metal installation. Note how I mention the plural "systems"... I applies to any operating system, including Windows.

---

### Post by Safeeq on 2015-05-25
I have misplaced the recovery disk(s) for windows so downloaded ubuntu 1210 on the USB disk and tried booting it but it does boots up normally and gives me the option to select ubuntu 1204 or windows, not recognizing the downloaded 1210 on usb. Is there a way to delete the partition belonging to ubuntu.(Sorry,I am newbie to ubuntu)

---

### Post by Vladlenin5000 on 2015-05-25
OK, a few comments before we proceed:

- Assuming the current installation - the one giving you trouble now - is standard, re-installation should be really easy because you can use the same partitions.
- Do NOT use any "End of Life", hence unsupported, version like 12.10. The currently supported versions are the new release 15.04, the current LTS (Long Term Support) 14.04 (valid until April 2019) or the previous LTS 12.04 (valid until April 2019). Interim releases like 12.10 had 9 months support only, their repositories are no longer accessible, new apps can't be installed and no security updates.

Regardless of the previous points, the USB Flash drive should be able to boot a live session and/or installation provided that
a) It has been done properly
b) the correct boot sequence has been selected.

Considering you've been running 12.04 I suggest you download the current LTS as well - 14.04 - and prepare the USB Flash drive (or DVD) with it. Probably you'll have to do it in another computer.

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)

The above are official instructions but take it as suggestions only. For all three OSs there are other tools as good as the ones suggested.
In order to boot from the newly created drive you need to select it as the first boot device and that depends on your hardware. Usually there's a on time boot menu triggered by a key that's shown in the first POST screen (the screen that comes before the OS starts loading). You can also check it in your manual or online. Other option is going to the BIOS settings.

**IMPORTANT** - This concerns Ubuntu installation only. In a dual-boot scenario with Windows, if you can't boot Windows either then you MUST have some Windows recovery media and use it to repair the Windows boot first. This usually results in loosing the dual-boot because, well, Windows does that. Don't worry because then you can boot your Ubuntu installer, proceed with the installation and at the end Ubuntu should be again in charge of the dual-boot process.
I now it sounds difficult but it isn't. I've been doing it for +20 years.

---

