---
title: "Corrupt openoffice.org files in Hardy"
date: 2008-06-03
forum: General Help
---

### Post by leemid on 2008-06-03
Hi,
I'm having a problem with OpenOffice.org 2.4 which creates corrupt documents approximately 50% of the time. It's only happens on the few boxes I've upgraded to Hardy.

When I open a file I've saved with 2.4, I get the *"The file <filename> is corrupt and therefore cannot be opened. Should OpenOffice.org attempt to repair the file?"* dialogue box. The file is *usually* recoverable if I choose Yes, but even when I save the recovered copy, it's corrupt again when I open it!

On further inspection, I'm fairly certain that [this question from Launchpad]("https://answers.launchpad.net/ubuntu/+question/32500") describes my problem perfectly, as it only happens when accessing my files from a Samba share. I have a Windows box on the same network that creates files no problem at all; it's only the Ubuntu machines that create the corrupt files.

This is driving me slowly insane - if anyone has any answers, I'd be really, really grateful!

Thanks in advance,
Lee

---

### Post by zedcar on 2008-07-23
leemid - have you gone insane yet? I've just this week set myself up with HH at work and the first two spreadsheets that Ive worked on from the network (samba) share have corrupted. Did you find any resolution? I've searched and found nothing.

- David

Edit: sanity is restored. I found a fix. Open the file ina  hex editor and you find that there is a duplicate entry for 'manifest.xml' right at the very end of the file which apparently should not be there. Delete it - I just delete all bytes from the 'm' in manifest to the end. Not sure how correct this is but OO can then repair & open the file.

---

### Post by leemid on 2008-07-25
Hi David,
I managed to avoid insanity by simply not using the file in the end! I've tried corrupting my files deliberately and using a hex editor I don't seem to have the second manifest.xml entry that you do.

Interestingly, this problem only occurs with my networked spreadsheets now. Writer documents used to be corrupted beyond repair, but now they're fine. I'm hoping OO.o 3.0 will fix this when it comes out in time for Intrepid - but glad the hex editing works for you!

Lee

---

### Post by maxim0512 on 2008-08-15
Has anyone found a solution or a good workaround to this issue? At work, our file server is Windows based, and if this bug persists, I will be unable to use the OpenDocument format.

---

### Post by fgysin on 2009-07-17
I just stumbled upon this Thread and think I can give an Update:

OO 3.0 did NOT solve this issue - I'm using OO 3.0 on Ubuntu Hardy and the corruption of files on Samba Servers is still a big problem.

Spreadsheets that I try to work with corrupt at a rate of about 80% when I save them directly on the server. Then I can only recover them with the Hex editor trick explained above.
Text documents corrupt at maybe 20% and are at least recoverable through the normal OO process. There is another anoying thing tough: Whenever I want to save a file on a Samba in a different location, that is using the 'Save As...' option, OO just crashes immediatley and all changes are lost. This does not happen when I use the normal 'Save' option - but it is really annyoing because we use to keep complete histories of our more importand documents, so after every change you would save them as another version.

It is really a problem for me and I only found one solution:
I copy the file from the Samba, modify it locally, and put it back on the Server. Really darn annoying - should have been fixed a long time ago. This is not exactly helping OO to spread through the business world where Samba shares are quite common... :/

---

