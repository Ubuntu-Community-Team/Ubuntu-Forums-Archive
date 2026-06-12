---
title: "Explore Munipulation?"
date: 2007-09-16
forum: General Help
---

### Post by zhavoney on 2007-09-16
I arrange and manipulate and move and manage all of my files in [COLOR="Red"]M.S. Windows[/COLOR] with drag and drop in [COLOR="Red"]Explore[/COLOR]. All from this one visible location. I create all my folders an move all of my files etc. How can I set this capability up in Linux?

---

### Post by JinxAu on 2007-09-16
Gday Zhavoney,

Yes, it is possible to manage your files from Linux... Ubuntu uses the Gnome Desktop Environment, although there are others available such as KDE (also in Kubuntu) and XFCE.

If you're wanting to check out Ubuntu without having to install it on your computer, you can run the Live CD version. To do this, you download the Desktop version of Ubuntu, burn to CD and boot into a live desktop environment. It does not touch your HDD(s), so it will allow you check out the Desktop without having to disrupt your current OS install.

One thing I will say, is that writing to NTFS fileystems has been a problem in the past. However, it's my understanding that this issue has been resolved with the latest NTFS Linux drivers (can someone confirm this?).

Cya round
Jinx

---

### Post by zhavoney on 2007-09-16
> **JinxAu said:**
> Gday Zhavoney,

Yes, it is possible to manage your files from Linux... Ubuntu uses the Gnome Desktop Environment, although there are others available such as KDE (also in Kubuntu) and XFCE.

If you're wanting to check out Ubuntu without having to install it on your computer, you can run the Live CD version. To do this, you download the Desktop version of Ubuntu, burn to CD and boot into a live desktop environment. It does not touch your HDD(s), so it will allow you check out the Desktop without having to disrupt your current OS install.

One thing I will say, is that writing to NTFS fileystems has been a problem in the past. However, it's my understanding that this issue has been resolved with the latest NTFS Linux drivers (can someone confirm this?).

Cya round
Jinx

Thanks for the reply JinxAu.

I already have Ubuntu Studio and Ubuntu 7.04 installed on this computer. I can not find the explore type of tree program that allows you to move and change and manipulate and manage the hard drive from one central location. Is it here somewhere and I just can't find it? 

Zhavoney

---

### Post by bikeboy on 2007-09-16
In the file manager there should be a side panel on the left, if not press F9. Then you can see a little down arrow, click on this and select "Tree". If desired, you can click where it says "View as Icons" and change it to "View as List" as well.

Hope that's what you're after, or at least part of it.

---

### Post by zhavoney on 2007-09-16
> **bikeboy said:**
> In the file manager there should be a side panel on the left, if not press F9. Then you can see a little down arrow, click on this and select "Tree". If desired, you can click where it says "View as Icons" and change it to "View as List" as well.

Hope that's what you're after, or at least part of it.

Thanks bikeboy
I am going to reboot  to Ubuntu right now and check it out. 


Zhavoney

---

### Post by zhavoney on 2007-09-17
> **zhavoney said:**
> Thanks bikeboy
I am going to reboot  to Ubuntu right now and check it out. 


Zhavoney

I can't find a file manager. 

Can you direct me to where it is? 

This version of 7.04 was installed from the first  Live DVD.

---

### Post by avik on 2007-09-17
Just go to Places->Home Folder.

---

### Post by zhavoney on 2007-09-17
> **avik said:**
> Just go to Places->Home Folder.

I still see no File Manager. Does it have to be installed?

---

### Post by jocko on 2007-09-17
When you click "home folder" or any of the other folders under "places" in the menu, the file manager (nautilus) will open that folder for you. From there you can browse through the entire file system exactly like windows explorer.

---

### Post by zhavoney on 2007-09-18
So how do I configure this so that I can drag and drop and delete and create folders. All of those options are blanked out and nothing will move or work.

---

### Post by zhavoney on 2007-09-19
> **zhavoney said:**
> So how do I configure this so that I can drag and drop and delete and create folders. All of those options are blanked out and nothing will move or work.

Is there no way to do this?

---

### Post by JinxAu on 2007-09-19
Sounds a bit strange. Usually you can open up the file browser as Avik mentioned (click on "Places" on the top menu, then select "Home Folder"). From here, it works pretty much like Windows... you can right click on folder and copy it, then navigate to another location and paste it. Or you could drag and drop it to another file browser window (or straight to your Desktop)... much the same as Windows. You can delete files and folders by highlighting it and hitting the "delete" key, or right-clicking and send to trash.

Not sure why it would have all of these options blanked out, unless you're outside of your /home directory - then you probably don't have the correct permissions to move the directory you're wanting to. This is much the same as Windows will not allow anyone who is not an Administrator to modify/delete any content outside of their C:\Documents and Settings (home) directory... unless specifically allowed.

Hope that helps.

Cya round
Jinx

---

