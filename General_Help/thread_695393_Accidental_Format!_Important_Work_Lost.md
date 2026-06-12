---
title: "Accidental Format! Important Work Lost?"
date: 2008-02-13
forum: General Help
---

### Post by pat_can_vault on 2008-02-13
OK, I was running Ubuntu 7.10 until someone in my family decided to mess around with settings until I got so annoyed I decided to just completely re-install. Being in a bad mood at the time, I didn't stop to think about my mum's important business work. And well, kinda formatted the disk, to the utmost horror of my mum. Is there any possible way that I can get it back? (It's only a few text documents, but it's very important to her) If so, could you please tell me exactly what to do! (I'm still new!)

Thanks In Advance


Pat

---

### Post by housam on 2008-02-13
Try to read in this guide . it may help [[COLOR="black"][COLOR="Red"]http://www.linux.com/base/ldp/howto/Partition/recovering.html[/COLOR][/COLOR]]("http://www.linux.com/base/ldp/howto/Partition/recovering.html")

---

### Post by pat_can_vault on 2008-02-13
Sorry, but I really don't understand a word of it :oops: It's really quite important. Sorry everyone

---

### Post by randy78 on 2008-02-13
> **pat_can_vault said:**
> OK, I was running Ubuntu 7.10 until someone in my family decided to mess around with settings until I got so annoyed I decided to just completely re-install. Being in a bad mood at the time, I didn't stop to think about my mum's important business work. And well, kinda formatted the disk, to the utmost horror of my mum. Is there any possible way that I can get it back? (It's only a few text documents, but it's very important to her) If so, could you please tell me exactly what to do! (I'm still new!)

Thanks In Advance


Pat

The absolute best thing that you can do is to make a "Ghost" image of your entire drive, then transfer it to another drive to perform the recovery.

This will help protect the files you seek to recover from being overwritten.

You can also try a program called PhotRec, which is in the TestDisk package:
sudo apt-get install testdisk

Then, open another terminal and type:
sudo photorec

Just be sure to make a new folder for the recovered files and ONLY search for the text files that were removed (You can search by extension) to ensure that you won't get bogged down by having EVERY file type recovered.

Good luck

EDIT: After you have imaged the drive, check out HELIX, a Linux based Forensic LiveCD
Just download it and burn it to a disk, making sure to set it to bootable

---

### Post by pat_can_vault on 2008-02-13
Please explain?? Sorry. Im new. I have no clue whatsoever:confused:

---

### Post by randy78 on 2008-02-13
> **pat_can_vault said:**
> Please explain?? Sorry. Im new. I have no clue whatsoever:confused:

If you don't know what you are doing, then I DO NOT suggest trying this yourself, as you can irreversibly destroy the data that you are trying to recover.

EDIT: To clarify, if you are on the computer that had the data loss, you need to log off and not get on it again until the recovery has been performed.
You risk overwriting what you are trying to recover, even by browsing the Internet.

Be careful and good luck ;)

---

### Post by pat_can_vault on 2008-02-13
Ok, sorry, I wrote that before I'd read your reply. :) It's currently working. I will post back when it's finished. Thanks

---

### Post by randy78 on 2008-02-13
> **pat_can_vault said:**
> Ok, sorry, I wrote that before I'd read your reply. :) It's currently working. I will post back when it's finished. Thanks

Cool

Just be careful ;)

---

### Post by randy78 on 2008-02-13
If you were able to use the information to solve your problem, mark the post as solved by using the "THREAD TOOLS" button up above.

Thank You

---

### Post by pat_can_vault on 2008-02-13
Uhm, it has completed... It left a folder called something like recup3 or something. it has many-a .doc files in it. But, I cannot seem to open them, copy or paste them, even as root. Any suggestions??

OK, managed to get them to copy-paste. But it just will not open! They're either blank or say "This is not a valid WinWordXXX Document"

---

### Post by randy78 on 2008-02-13
Have you tried burning them onto a disk and opening them with Office, in a Windows computer?

If they still won't open, then they were most likely overwritten, and in that case...
You're outta luck...

You should tell your Mom that she'll need to get another set of copies of whatever it was you deleted, because there's no chance of saving them.

I'm not trying to sound like a jerk, but next time somebody has something important, even if it's on your own computer and you are sharing it, let them know that you'll be reformatting and that they should get all of their own personal files off of there.

You need to realize that this is how HUGE catastrophe's happen, and hope that those weren't critical papers that she needed for work, because I don't think "My son formatted the computer" is going to fly with her boss...

A lesson lived is a lesson learned...

Take Care and Good Luck

---

### Post by az on 2008-02-13
Do not write to the disk.  Make an image of it to an external drive.

[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

You can also just skip making an image and data-carve the kinds fo files you mom needs from the disk.

Use Foremost or Photorec directly on the disk.  Run this from the live cd (or Ubuntu-rescue-remix) and save the files to an external drive.

The files you will recover may not all be valid, since you will data-carve file fragments as well as valid files.  Foremost can recover files that Photorec cannot.

---

### Post by pat_can_vault on 2008-02-14
> **randy78 said:**
>  I'm not trying to sound like a jerk, but next time somebody has something important, even if it's on your own computer and you are sharing it, let them know that you'll be reformatting and that they should get all of their own personal files off of there.


lol. I did tell her I was formatting... she just said OK. See, she's not the sharpest tool in the shed, my mum, and after asking where the files were and breaking the news to her, she told me she didn't know what formatting meant :roll:

Thanks for the suggestions I'll try them out. If they don't work i'll just give up.

---

