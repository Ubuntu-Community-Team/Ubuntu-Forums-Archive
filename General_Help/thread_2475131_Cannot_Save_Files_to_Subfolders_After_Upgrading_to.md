---
title: "Cannot Save Files to Subfolders After Upgrading to Ubuntu 22.04"
date: 2022-05-17
forum: General Help
---

### Post by androy518 on 2022-05-17
OS: Ubuntu 22.04 LTS x86_64 
Host: HP Pavilion Laptop 15t-cs200 
Kernel: 5.15.0-30-generic 
Shell: bash 5.1.16 
Terminal: gnome-terminal 
CPU: Intel i7-8565U (8) @ 4.600GHz 
GPU: Intel WhiskeyLake-U GT2 [UHD Graphics 620] 


I have been having this issue since upgrading to 22.04 from 20.04. I am able to save files to these locations: Home, Documents, Downloads, Music, Pictures, and Videos but when I try to save to a sub-folder in those locations, it does not save. I am also able to save to a location that I am able to save to and move the file into a sub-folder. This happens when I try to save any file type from my browser. It also happens when I try to drag and drop files from my virtual machine into Nautilus.

I have tried uninstalling and reinstalling Nautilus but that did not work. I have also tried different browsers but that also did not work. I have tried changing the permissions on the folders but that did not work. Additionally, I have tried changing the access to the folders but that also did not work. I have also read a thread on this forum that had a similar issue but it did not have a solution to the problem ([https://ubuntuforums.org/showthread.php?t=2474920&highlight=Subfolder](https://ubuntuforums.org/showthread.php?t=2474920&highlight=Subfolder)). If I am using a download manager like aria2 and I specify the location that I want the file to be saved to, the file saves properly. Does anyone know how to solve this issue.

---

### Post by yancek on 2022-05-18
When you try to save a file to one of these sub-directories, do you get any warning/error message?

Check the owner:group and permissions.  Permissions should be 755 on directories and 644 on files.  Is this problem limited to saving a file from your browser?  Can you copy a file using the GUI or terminal?

>  It also happens when I try to drag and drop files from my virtual machine into Nautilus.

Have you configured your computer to do this?  The link below explains it for VirtualBox.  If you are using other virtual software, you should be able to fin it at their site.

[https://www.makeuseof.com/tag/transfer-files-virtual-machine-guest-host-pc/](https://www.makeuseof.com/tag/transfer-files-virtual-machine-guest-host-pc/)

---

### Post by philhughes on 2022-05-18
I can't find it now, but came across this somewhere else. A workaround was once you have selected the folder, click on the file name and then the file will save. Works for me.

---

### Post by androy518 on 2022-05-18
No warning appears when I try to save files to these directories. What happens is nothing. There is no pop on the browser that shows the file downloading and no saved file.
I can copy files with the GUI and Terminal. I can also save to a directory that does allow me to download a file then move the downloaded file to a sub directory that I normally would not be able to download.
How do you view the permission numbers?

I looked for a tutorial on YouTube about dragging and dropping files in VirtualBox. It said that I needed the guest additions CD. When I downloaded it and inserted it, the Windows VM did not have a notification showing that it was inserted so I am not sure if it is inserted.

---

### Post by androy518 on 2022-05-18
This works and allows me to save files but I would prefer to not have to click the file name before saving. Thank you for the workaround.

---

### Post by yancek on 2022-05-18
I've noticed recent version of firefox don't show the pop-up asking if you want to download but simply downloads to the user Downloads directory.  What version of firefox are you using?  You can open a terminal and type:  firefox -vesion to find it or go to the Help tab in firefox and click on it and the bottom option is About Firefox which will also tell the version.

You can change the default download directory by clicking the icon in the upper right, 3 small horizontal bars and selecting Settings and scrolling down to Files and Applications.  Selecting Downloads using this option will show all recent downloads.  You can do the same by clicking on the Tools tab and selecting Downloads to see recent downloads.

The VirtualBox site has a page explaining how to install guest addtions.

[https://www.virtualbox.org/manual/ch04.html](https://www.virtualbox.org/manual/ch04.html)

To find the permissions for the Documents directory you run this from your /home/username directory:  ls -ld Documents
To find the permissions for the directories and files in Documents run from your /home/username directory:  ls -l Documents:

---

### Post by androy518 on 2022-05-18
Firefox is not currently my main browser. I am currently using Brave. This is my Firefox Version: Mozilla Firefox 100.0.1 
For me, the popup for the downloads does appear in Firefox but downloads still do not work in sub-directories unless I use the workaround where you click on the file name before saving. Changing the default download directory did not solve the issue.

My file permissions are 664 for files and 775 for directories. I believe that this is because I went to the Home folder properties in Nautilus and tried changing the group permissions to Create and Delete files because I did not know what was causing the issue.

---

### Post by androy518 on 2022-05-31
I am not sure why but I am not having this issue anymore. Saving from the browser works normally for me now.

---

