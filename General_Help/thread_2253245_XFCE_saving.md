---
title: "XFCE saving?"
date: 2014-11-18
forum: General Help
---

### Post by simon d w on 2014-11-18
I was thinking about reinstalling me Image and starting fresh. I was wondering is there a way of saving your XFCE settings so I don't have to fart around fiddling with fonts, remembering where all my icons go? I have it set up exactly how I like it. It is annoying remembering what you had before; also what programs I have installed, fonts sizes and colours. That would be a great I idea If when you sign up to Ubuntu one it automatically,periodically, remembers your set up, so if something went wrong and you needed to reinstall, when you signed back in to Ubuntu one or some other program, it could ask you if you wanted your previous settings reinstalled including background and the like? Maybe there is and you'll tell me you just press this button and there you go. 
Cheers

---

### Post by slickymaster on 2014-11-18
```
~/.config/xfce4
```
Of course you might want to backup other stuff not directly related to Xfce's settings under **~/.config** or somewhere else in **~** but it's in that where you'll find anything worth backing up (like panel and keyboard settings).

---

### Post by grahammechanical on 2014-11-18
"Press that button. And there you go." Happy now?

Life is never that simple. Do you have a separate /home partition? The existence of a separate /home partition would make it possible to re-install without losing the user configuration files. But it is not a one click process.

We can also reinstall without instructing the installer to format the Ubuntu partition. That might work. But again it is not a one click process. We choose the Something Else option and we go from there.

When we get to the page where the partitioner shows us the hard disk partitions we select the partition where Ubuntu is installed. We click Change and in the dialog we change Use As to Ext4; the mount point to / but we do not tick the box to Format the partition. Then we click OK and then when back at the partitioner page we make sure that the boot loader is going to be installed where we want it to be installed (default is sda) and then we click Install Now.

Things are slightly different if we have a separate /home partition. In this case we can format the Ubuntu partition but we have to tell the installer where /home is. So, we select the partition that is presently /home and click Change and at the dialog we set Use As to Ext4 and the mount point to /home but we do not tick the box to Format the partition. Then we click OK and we end up back at the partitioner page where, after double checking - it is never good to do these things without double checking - click install.

Be careful to put in the same user name and password.

Regards.

---

