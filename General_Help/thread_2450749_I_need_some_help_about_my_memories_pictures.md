---
title: "I need some help about my memories pictures"
date: 2020-09-20
forum: General Help
---

### Post by chlayman on 2020-09-20
Hello Ubuntu community, hope you are in good.

I will share with you today my problem, about two years ago uninstalled Ubuntu OS 14v without deleting my private files from my computer, and that was working alongside WindowsOS.
Now i notice my hard disk has a lot of space reserved, But i cannot access my files (my private files on UbuntuOS)

My question is will these files appear again if the Ubuntu system is installed alongside windows? Knowing that i forgot the password to my log in (This is the reason why Ubuntu was uninstalled at the time)
If no, is there a way to recover my hidden files?

Thanks for your comments and supporting
All appreciation and respect

---

### Post by guiverc on 2020-09-20
If you encrypted your files, you won't be able to access them without the *lost* password.

If they aren't encrypted, you probably don't even need to install Ubuntu; but if the reason they can't be accessed by windows is only the *file-system*, you'll be able to access them via a *live* system, such as booting Ubuntu install media on thumb-drive, and using the *Try Ubuntu* option.

Some links that maybe helpful

[I]Yes you can also install Ubuntu without erasing user files, however I get the feeling you're not after that, just wanting to recover files, so I'm skipping that detail.
[/I]
**Verify your Ubuntu (ISO) download:**
[https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)  (this is automatic on Ubuntu 20.04 LTS)

**Try before you install:**
[https://ubuntu.com/tutorials/try-ubuntu-before-you-install](https://ubuntu.com/tutorials/try-ubuntu-before-you-install)

**Writing Ubuntu ISO to thumb-drive:** (using Ubuntu/MacOS/windows)
[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview)
[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview)
[URL="https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview"]https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview
[/URL]

---

### Post by Impavidus on 2020-09-20
How did you uninstall Ubuntu? If the partition with your private files is still there, you should be able to access it with an Ubuntu livedisk (or any other Linux livedisk). If the files are encrypted, you need the passphrase. If the partition was deleted but not reused and this is an HDD (not an SSD), file rescue tools may still find something.

---

