---
title: "Deleting old Windows Thumbnails in Ubuntu 12.04"
date: 2014-01-05
forum: General Help
---

### Post by brianmacgrath399 on 2014-01-05
I removed windows vista and installed ubuntu 12.04 my laptop recently. 

I used photorec to see what images are on my hard drive, and I got a few thousand thumbnails. I flicked through them in the folders, changed access and then deleted them in terminal using  
"sudo rm -r /home/username/Pictures/recup_dir.10"

 I used bleachbit to remove thumbnails then saved on Ubuntu from those images.  
that only removes Ubuntu specific thumbnails, created from viewing those files.


Does anyone know how to remove old windows thumbnails or all old windows files on my PC through Ubuntu or is it impossible or very difficult?


tldr windows thumbnails show up, in photorec, how do I delete them?




P.S. only beginner using terminal.

---

### Post by ivan-balseiro91 on 2014-01-05
Why wouldn´t you do a clean install of Ubuntu getting rid of Windows OS and then set it up on a virtual machine if you once ever need it again? I think it the best and most clean solution for you.

PS: when you install ubuntu select the option of erasing everything on the hard drive and install ONLY Ubuntu.

---

### Post by brianmacgrath399 on 2014-01-05
What do you mean by a clean install of Ubuntu? 

Do you mean using something like [h=1][Darik's Boot And Nuke]("http://www.dban.org/")?[/h]
And then installing Ubuntu?

---

### Post by nerdtron on 2014-01-05
Yes that is a good option. I think the only way to remove those deleted files if to overwrite them with random data. Assuming you have a drive in which you already reformatted once but still photorec was able to detect deleted files, you need to *wipe* the drive.
Example: sudo dd if=/dev/random of=/dev/sda1 
Be careful with this command. It will wipe everything on that partition (or drive). After that (it takes a long time depending on drive), you need to reformat the hard drive again to ext4 or ntfs since it won't have any filesystem intact.

---

