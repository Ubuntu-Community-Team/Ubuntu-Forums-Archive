---
title: "Grub Customizer."
date: 2023-10-15
forum: General Help
---

### Post by Hewjr100 on 2023-10-15
Please excuse me if I am posting in the wrong forum topic, and of course move it to the right topic.

Up until I did a fresh install of Ubuntu 22.04 I was using and still use Grub Customizer via PPA.  The only thing that changed is that I can no longer use my own images for the grub menu background.

I noticed that the PPA shows it was updated 20 hours ago.  I ran updates, but no Grub Customizer update, it must be for Ubuntu 23.10.

Does anybody else using Grub Customizer have this issue? and if so has anyone figured out how to use an image.

Henry

---

### Post by yancek on 2023-10-15
I've never used Grub Customizer but to have a background image of your choice in the Grub menu, all you need to do is put the image in /boot/grub and run sudo update-grub.  Not all types of image files work, you can find that info with an online search.

---

### Post by Hewjr100 on 2023-10-15
Sounds good to me, thank you very much.

Henry

---

### Post by MAFoElffen on 2023-10-15
Adding on to that explanation...

Historically Grub made a search of images in that directory (/boot/grub), in this order:
 
[LIST]
[*]The first image found, in this order: jpg, JPG, jpeg, JPEG, png, PNG, tga, TGA
[*]They had to be images of type:  PNG, JPG/JPEG and TGA images for the background.
[/LIST]
 
The image must meet the following specifications:
[LIST]
[*]JPG/JPEG images must be 8-bit (256 color). Else you will get errors saying "Too many Huffman tables". Since most of the time you will not want to limit yourself to 256 colors (which is totally yesteryear) you will probably find PNG much preferable.
[*]Images should be non-indexed, RGB.
[/LIST]
 
The GIMP image editor is one application which can edit images to conform to the GRUB 2 standards. Use the Image > Mode menu options to set the properties to RGB and ensure the mode is not set to Indexed. 

Sometimes it was better just to say which image you wanted to display by adding a line that pointed right to a specific image:
```

GRUB_BACKGROUND=/path/file_name.extension

```

---

### Post by Hewjr100 on 2023-10-15
Working on it.  will keep you posted.

---

### Post by oldfred on 2023-10-15
Not a fan of grub customizer as it replaces the grub scripts with its own 'proxy" versions.
About the only way to undo that is remove grub customizer and totally reinstall grub2, correct version either UEFI or BIOS.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by MAFoElffen on 2023-10-15
I'm glad you said that oldfred. I didn't want to be the first one to open that door. I thought to myself, again, and again, about asking how he felt about unistalling that... Instead, I sat back and bit my tongue.

My reasons, is that I keep seeing people come here, and on other Forums with broken machines, that cannot boot because of problems that Grub-Customizer has caused.

---

### Post by Hewjr100 on 2023-10-16
Nice to see your post oldfred, and by the way so long as anyone's suggestions help, don't be afraid to say so.  I will never be as good as most people here, and all your help is appreciated.

Henry

---

