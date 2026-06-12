---
title: "LibreOffice Base Crashes"
date: 2018-03-14
forum: General Help
---

### Post by rbscairns on 2018-03-14
I am not sure if this is the best place to get this problem solved. Maybe I should ask in the LibreOffice forum. If so, just tell me.

I wanted to create a database using LibreOffice 5.1.6.2 that I have installed in Lubuntu. I created the database that I wanted but then when I clicked on Forms, the program froze. I then created the database again using LibreOffice 5.1.6.2 that I have installed in Windows XP. There the database works well.

I reboot to my Lubuntu and open the database that I created under Windows. Again, if I click on Tables, Queries, Forms, or Reports the program freezes.

All my other components of LibreOffice work as expected.

Any help will be gratefully received and faithfully applied.

---

### Post by wyliecoyoteuk on 2018-03-14
Have you tried updating to 5.4.5 or 6.02?

---

### Post by wyliecoyoteuk on 2018-03-14
this might help:
[https://ubuntuforums.org/showthread.php?t=2364249](https://ubuntuforums.org/showthread.php?t=2364249)

---

### Post by amanchesterman on 2018-03-15
I can add from my own experience that the solution posted by psherlocksdb on the thread referenced above by wyliecoyoteuk worked perfectly for me. I had experienced exactly the problem reported by the OP above, and by many others in the referenced thread.

I also learned, however, that the problem affected only 32-bit Ubuntu systems. At the time I was using an older laptop which needed a 32-bit installation. Some time later I was able to move to a 64-bit machine, and there the problem does not seem to occur. So rbscairns, you may want to check if this is part of the issue.

---

### Post by rbscairns on 2018-04-01
Thank you wyliecoyoteuk and amanchesterman. Problem solved using the information found [here]("https://ask.libreoffice.org/en/question/120447/libreoffice-base-crashes-on-32bit-linux/"). Evidently, LO Base does not work "out-of-the-box" on 32 bit Linux machines after a new kernel release in about mid June 2017. This bug (that has been reported) has not yet been rectified by either Ubuntu or LibreOffice or OpenJDK.

In a nutshell, I add the kernel parameter "stack_guard_gap=1" (without the quotation marks) in my grub file. This was easily done in the General settings of Grub Customizer that comes with Lubuntu. I do not know what the parameter means or does, however it works for me.

Now all appears to be working as it should in LibreOffice (I hope).

---

