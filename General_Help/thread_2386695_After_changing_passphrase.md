---
title: "After changing passphrase:"
date: 2018-03-08
forum: General Help
---

### Post by dwilches on 2018-03-08
I installed Ubuntu 17.10 in dual boot with Windows 10 earlier this week, and I setup full disk encryption in one of the partitions using this guide: [https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption)
Until now, I had been able to boot into Ubuntu after inputting my passphrase, but today I decided to add a passphrase to another slot and delete the old one.
After I rebooted, GRUB asked me for my passphrase and I inputted it, it was successful and showed "Opened slot 0" (the slot where my luks passphrase is), but then ubuntu continued starting and it showed this error:

    cryptsetup: cryptsetup failed, bad password or options

And then went to sleep for 60 seconds.

What could be wrong?

I know my passphrase is correct because GRUB manages to open slot 0. I have even tried with another spare passphrase I have in slot 1, and GRUB showed the message "Opened slot 1" and then the same error message as before.

BTW, there is list of known bugs in the guide I followed, but none of them seem to be my problem as I nor Windwos updated any software: [https://help.ubuntu.com/community/ManualFullSystemEncryption/KnownBugs](https://help.ubuntu.com/community/ManualFullSystemEncryption/KnownBugs)

---

### Post by HermanAB on 2018-03-09
Well, with things like this which can have potentially catastrophic consequences: You can end up locked out of your system; it is usually best to read a guide or two and then read the relevant man pages also, since that is the real canonical information.

So, first read the cryptsetup man page and then try to figure out what is going on:
$ man cryptsetup

---

