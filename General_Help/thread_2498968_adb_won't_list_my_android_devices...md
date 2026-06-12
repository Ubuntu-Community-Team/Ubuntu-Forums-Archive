---
title: "adb won't list my android devices.."
date: 2024-07-05
forum: General Help
---

### Post by ronjjjg8885 on 2024-07-05
hello
i followed this
[https://wiki.lineageos.org/adb_fastboot_guide](https://wiki.lineageos.org/adb_fastboot_guide)
[downloaded and extracted to ~/adb-fastboot and then added the text to ~/.profile]..

but i can't list my device after typing "adb devices".. [i did allowed USB debugging]..
it does not asks me anything on my device..

in the past i did it with windows. but i don't use windows any more..

what can the reason be?
thank you.

edit..
i added the text in the end of the .profile file..
i did log out and in again

edit..
now it looks like this..
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293944&stc=1[/IMG]

---

### Post by currentshaft on 2024-07-05
Try a different USB cable and check the output of "sudo dmesg" for errors.

---

### Post by ronjjjg8885 on 2024-07-06
thank you
i've tried a different cable and port but it says it can't connect to server.....

here is the "sudo dmesg" output..

[https://pastebin.com/ND3ikWEu](https://pastebin.com/ND3ikWEu)


edit..
there was a reflection but this is how i pictured the msg..
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293945&stc=1[/IMG]

---

### Post by currentshaft on 2024-07-06
I must say, you offer what must be the most unique and possibly creative perspective on providing screenshots. The cropped and sideways Samsung monitor is possibly your pièce de résistance.

That being said, I see no errors in your dmesg output. The phone appears to connect and be recognized by the kernel. You might want to confirm USB debugging is actually on and if so, perhaps another USB port or computer entirely.

Perhaps others have more ideas to try. adb has always just worked for me on Ubuntu.

---

### Post by ronjjjg8885 on 2024-07-06
i will try

next time i will picture better :)

---

### Post by ronjjjg8885 on 2024-07-06
i've tried again and this is what i got..
[https://pastebin.com/9janxCQg](https://pastebin.com/9janxCQg)

does adb can be considered a privacy problem if i install it on my main computer to try? i don't like big tech companies software on my main computer.. but if you will tell me it is not a problem i will try..

---

### Post by deadflowr on 2024-07-06
> **ronjjjg8885 said:**
> i will try

next time i will picture better :)

It's terminal output, just copy and paste it and wrap it in code tags.

---

### Post by ronjjjg8885 on 2024-07-07
i don't have my password manager on that computer so i can't login to the forums there.
but i will copy it to a usb drive and post it from there.....
do you need the terminal out put to be posted in code tags at this point?

---

