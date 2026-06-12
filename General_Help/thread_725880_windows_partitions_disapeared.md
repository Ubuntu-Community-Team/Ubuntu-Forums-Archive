---
title: "windows partitions disapeared"
date: 2008-03-16
forum: General Help
---

### Post by ubiubi on 2008-03-16
Hi

I have a triple boo system 5Ubuntu, PCLOS and Windows XP. My two windows partitions have disapp eared and their existance is only registered under the Gparted programme. When I do a search in 'Places for the partitions they are not there. This is a pain because We've loads of family pictures in windows which we wish to transfer into ubuntu to make new desktop backgrounds. 

If this helps I don't know but I transfered pictures from windows (Under PCLOS - which found the partitions) to the pictures folder in a home directory in Ubuntu. Rebooting ubuntu, when we opened this directory, non of the images could be opened. A message saying we didn't have permission


Any suggestions from you kind folks would be greatly appreciated!


Ubiubi

---

### Post by sixpence on 2008-03-16
Alrighty. IF you want open those transferred images that give you the permission error, follow the steps as best as you can. If a step is unclear, please post a response and I will try to clarify.

I have made the assumption that you use gnome, if this is not the case, also notify me and I will revise the instructions according to your window manager.

1) Open a Terminal - Do this by clicking "Applications" at the top left of your screen. Then click "Accessories" and then click "Terminal" This should open a terminal window.

2) Open the image-viewer application from the terminal with 'sudo' - Do this by typing in the word 'sudo' and then after it the name of the program you used to open the images. For example, if you used the Gimp to view the images, you would type:

```
sudo gimp
```

3) Enter your user password - The terminal will ask you for a password, enter the password of the user you are currently on.

4) Just open the images as you usually would, and there should be no permission error. Now save the images to another name, somewhere on your hard disk and you should be able to open them as a regular user, without all this hassle.

Hope this helps!  ^.^

---

### Post by taurus on 2008-03-16
Maybe the reason those ntfs partitions disappeared because you didn't shut down windows cleanly the last time you used it.  If you used either hibernation or sleep mode to shut down windows, then Ubuntu can't mount it unless you use the force option.

Therefore, boot into windows again and this time, shut it down cleanly.

---

### Post by ubiubi on 2008-03-17
Hello to both of you for your time and help. In fact the problem was caused by a badly closed down windows session. I followed your ip and everything is functioning properly in linux. Cheers!:):)

---

