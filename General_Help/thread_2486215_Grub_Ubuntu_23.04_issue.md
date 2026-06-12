---
title: "Grub Ubuntu 23.04 issue"
date: 2023-04-23
forum: General Help
---

### Post by rhpositivo on 2023-04-23
hello, i have used Ubuntu 22.04 and Ubuntu 22.10 (updated from 22.04) in this last year, and i have Manjaro (other dev or ssd) and Win (other dev or ssd) installed too, when i used  ```
sudo update-grub
``` the grub build the grub.cfg and i needed to correct manually for start Manjaro from ubuntu grub.
 Now i installed an EndeavourOS (other ssd) and a fresh Ubuntu 23.04 (replace the Ubuntu 22.10 because update failed :() and it build a different grub.cfg (sudo update-grub) but now in the terminal i have some messages error for every OS (usr/sbin/grub-probe: errore: file system sconosciuto) file system uknown, and if i try to correct grub.cfg for example for manjaro like in Ubuntu 22.10 the system dont start anyway 

[IMG]https://i.ibb.co/Fmkfv8T/Screenshot-20230423-065734.png[/IMG]

---

### Post by yancek on 2023-04-23
Are you booting and getting these messages from Ubuntu 23.04 Grub?
Are Manjaro and Endeavour installed in UEFI mode and do you have a separate EFI partition on their drives that you boot the different OS from?  Or do you only have one EFI partition on one drive with all the entries for the different OSs?  If you don't resolve this issue, you should run boot repair with the 2nd option described on the page and select to 
create bootinfo summary and do not make any repairs.  Post the link you get when boot repair finishes here so you can get help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by rhpositivo on 2023-04-23
1 [COLOR=#000000]Are you booting and getting these messages from Ubuntu 23.04 Grub? no, if I boot from ubuntu (because i use 2 grubs [1-Manjaro and 2-Ubuntu]) grub i can boot Ubuntu and Windows only , i have this error messages (uknown system) if i update the grub from terminal
2 [/COLOR][COLOR=#000000]Are Manjaro and Endeavour installed in UEFI mode and do you have a separate EFI partition on their drives that you boot the different OS from? Only Manjaro and Ubuntu have an EFI Partition (FAT32) and bootloader grub installed i can't boot from endeavouOS from EFI (the default is Manjaro Partition Grub) but if i select or use F8 when system start i can choose to boot from Ubuntu EFI
3 if i use boot repair the Uknown Systems errors remains, and it set Ubuntu default ... and i cant start Manjaro and Endeavours anymore, so i need to repair manjaro grub to start all systems

Edit: [/COLOR]these are 2 screenshots if they help :

 1 **Ubuntu 22.10 and Manjaro start (**it was in sdf but then i moved it to sda but it still worked after a grub update[B])
[/B]
[IMG]https://i.ibb.co/g4t6MPf/Screenshot-20230423-132120.png[/IMG]

2 **Ubuntu 23.04 and Manjaro don't start not even if I change the final string (*255*) manually  (*****initrd /boot/initramfs-6.1-x86_64.img*****)**
 [IMG]https://i.ibb.co/ZMK7zHk/Screenshot-20230423-132116.png[/IMG]


i guess the system uknown errors make a bad grub.cfg file


UPDATE: tryed to repair with boot repair and it reported erros, so I decided to format and reinstall Ubuntu 23.04, without Manjaro and EndevourOS connected, and the grub seems to work only with **Windows and Ubuntu** but when I physically installed **Manjaro** the problem came back, but first I had to mount the ssd to make it recognized

---

### Post by ActionParsnip on 2023-04-24
Oh jesus, use text! This is a text based forum and you are showing text....so why use screenshots?? It makes absolutely no sense at all. Copy the text and use the standard code tags

---

### Post by yancek on 2023-04-24
Rather than posting images of your boot menu, it would be more helpful and provide more information that is useful if you run boot repair and post the link here as I suggested in my previous post.

---

### Post by rhpositivo on 2023-04-26
avoid writing sentences that aren't helpful, if you know how to solve the problem thank you very much but if you don't know how to do it just because it's an image and you don't understand it, it's not my fault (this is my first post in the forumm this is not a nice presentation of how to get help, maybe in the future I will avoid posting anything)

---

### Post by QIII on 2023-04-28
@rhpositivo:

Please do as you have been asked with regard to pasting text rather than images.  Images can be difficult to make out, particularly on mobile devices with small screens.  They may also discourage help that might have otherwise been provided by those who have slow connections or data limits who will simply pass by.

Further, text allows others to copy what your provide as text and experiment with it to help provide answers.  Further still, posting the *entirety* of text content provides context for the parts you are pointing out.

This is more or less standard netiquette on peer-to-peer technical support forums.   If you are getting results in the form of text, provide those results in the form of text.

If you find this too onerous, we have no problem at all if you choose to use another venue to receive assistance.

---

### Post by ActionParsnip on 2023-04-28
> **rhpositivo said:**
> avoid writing sentences that aren't helpful, if you know how to solve the problem thank you very much but if you don't know how to do it just because it's an image and you don't understand it, it's not my fault (this is my first post in the forumm this is not a nice presentation of how to get help, maybe in the future I will avoid posting anything)

Its not "don't understand". Its the fact that you are using a form. You can encapsulate your text in code blocks and it's much easier to read and comment on as the text can be copied and pasted. Code blocks look like this

```

see how much better this is
please use code blocks and paste text
use images for application windows but using a screenshot for text is non-sensical

```

---

