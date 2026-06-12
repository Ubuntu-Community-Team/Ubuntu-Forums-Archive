---
title: "WubiGuide needs more documentation"
date: 2008-04-24
forum: General Help
---

### Post by sneakbob on 2008-04-24
I read the WubiGuide on wiki.ubuntu.com here:

[https://wiki.ubuntu.com/WubiGuide?highlight=%28wubi%29](https://wiki.ubuntu.com/WubiGuide?highlight=%28wubi%29)

The guide is unclear in a few places, is this the right forum to ask?

For example, the section "How do I install Ubuntu?" starts with the sentence "Run wubi, insert a password for the new account, and click "install", and an image of the Ubuntu Setup Rev 457 is shown with steps 1 to 3 highlighted.

Hence my questions:

1. Today I downloaded the 1 megabyte wubi installer and saw it is Rev 501. Does this matter?

2. Must the installation drive be C: and/or must it be partitioned in a specific way?

3. The username is shown as "ago", which I assume is an example, but must the username be the same as the Windows username, or different, or does it matter?

Those were my initial questions before I decided to fill in the fields as follows. I am using Vista Home Premium on HP Pavilion Media Center TV m8055.it, but without the SP1 update (it is downloaded but I want to have a Linux LiveCD ready before I risk installing it).

Installation drive = L:
because that was the last drive I created, but it is a logical partition and not a primary - will wubi fail to boot from there?

Desktop environment: Xubuntu
but a download error occurred so I retried with
Ubuntu desktop

Language: English
(it was Italian so I changed it)

Username: sneakbob
which is NOT a Vista user name - I was unsure whether the username should be new

Password: I devised a new password


Finally, because wubi is downloading the ISO very slowly (it will take over 25 hours) I have downloaded the ISO separately (took only a few minutes) and I plan to cancel wibu and restart it with ubuntu-8.04-desktop-amd64.iso in the same folder.
 
Sorry for this long post, but I wanted to get all the details clear.

Edit: wubi setup has finished installing the 8.04 ISO into L: in folder ubuntu. It has also created two C: files: wubildr and wubildr.mbr .

Edit2: I have now restarted the PC from Vista and I chose ubuntu from the boot loader. Ubuntu installed (I caught a glimpse of out of memory error before the screen blanked). The PC then restarted and Ubuntu started with a rather Windows-like login screen. I tested that all partitions were accessible (except the L: logical partition), and tried most of the adminstration tools. I saw a few fleeting error messages but none stayed on screen long enough for me to read them. I then restarted the PC from Ubuntu's "Start button" and booted back into Vista. I was pleased nothing had been altered in L: outside the ubuntu folder, but Ubuntu had changed the system time to 3 hours ahead (there was no network available for Ubuntu which might explain this). In all I'm pleased wibu managed to install the ISO, given it was Vista and that I had several partitions. :)

--
HP Pavilion Media Center TV m8055.it 
AMD Athlon 64X2Dual Core 5000+ 2.6GHz; RAM 2GB;
Windows Vista Home Premium, up to date but not SP1
230 Gigabyte hard disk partitioned into:
 C: 118 GB NTFS (system, boot, primary)
 K:  64 GB NTFS (primary)
 L:  43 GB NTFS (logical)
 D:   5 GB NTFS (primary)

---

