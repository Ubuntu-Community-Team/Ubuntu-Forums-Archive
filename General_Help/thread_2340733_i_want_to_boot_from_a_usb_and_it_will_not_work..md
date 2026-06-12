---
title: "i want to boot from a usb and it will not work."
date: 2016-10-21
forum: General Help
---

### Post by professorjuicy on 2016-10-21
so i have an hp laptop and i really want to put ubuntu on it because win 10 is so slow. 
however when i go to boot off the usb all i get is grub2  
first an error saying "unknown filesystem" 
any ideas as why i cannot get ubuntu to boot to install??

---

### Post by yancek on 2016-10-21
> however when i go to boot off the usb all i get is grub2  
first an error saying "unknown filesystem" 

The usb you are referring to is the installation medium, correct?
Did you download the Ubuntu iso from the Ubuntu site?
Did you do an md5 checksum on the downloaded iso to verify that it was not corrupted during the download?
Did you test the usb on another machine to see if it boots, that eliminates a possible problem?
How, meaning what software, did you get the iso on the usb drive?

---

### Post by professorjuicy on 2016-10-21
yes i used the iso archive straight from the ubuntu site. 
i ran a checksum prior with 0 errors 
i do not have another machine to test 
and i used rufus as recommended from the ubuntu site

---

### Post by Bucky Ball on 2016-10-21
Welcome. Do you have hibernation off in Windows? You need to boot into Win and switch it off then boot to the BIOS and switch off faststart and secure boot. After all that, you should see two entries in the boot device order for the USB and one should have [EFI] or [UEFI] next to it. You *must* use that one as Win 10 will be installed in EFI if pre-installed and Ubuntu should be installed in the same mode so they play nice. 

Consequently, if you've installed Win manually in Legacy mode ...

PS: Does everything work fine when you boot to a live session (Try Ubuntu)?

---

### Post by professorjuicy on 2016-10-21
I will try that first i am currently reinstalling ubuntu tp usb (making sure nothing is wrong with the install) 
I want to completely wipe win 10 off this pc and only have ubuntu, is there something else i need to do for that? 
and no when i boot after changing bios to boot from usb it boots straight into grub2 and not to the ubuntu live 
and i updated to win 10 through the auto installer on the launch of win 10 this laptop came with win8.

---

### Post by Bucky Ball on 2016-10-21
Sounds like you are installing Ubuntu to the USB, not creating USB install media. When you say it boots straight to Grub2, do you mean the boot options with a list of kernels and when you choose one you get 'unknown file system'? The description in your first post is a bit ambiguous.

---

### Post by professorjuicy on 2016-10-21
i do not get a list of kernels, just an error unknown filesystem then a blank grub2 page

---

### Post by Bucky Ball on 2016-10-21
Could you please explain why you've marked this thread solved? If you found a solution, please share with the rest of the community. Thanks. :)

---

