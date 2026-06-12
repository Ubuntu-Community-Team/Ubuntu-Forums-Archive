---
title: "Problem with alien."
date: 2008-06-24
forum: General Help
---

### Post by ahriman22 on 2008-06-24
So I've been trying for about an hour to install a firefox plugin. Adobe flash 9, to be exact. They only had the tar.gz and .rpm files for download and after reading a short how to, i installed Alien and downloaded the .rpm file. But every time i try to install it, it gives me an "Cannot execute binary file" error. I'm getting pretty frustrated. 

I'm using Ubuntu 8.04.

---

### Post by bobbob1016 on 2008-06-24
You shouldn't need to manually install flash.  In most cases anyways.  Go to youtube.com and play any video, assuming you're using firefox, there should be a yellow bar at the top click here to install flash or missing plugins or something.  Also try clicking Applications -> Add/Remove and search for Ubuntu Restricted and select and install it.  That should work.

---

### Post by ahriman22 on 2008-06-24
I'm trying to update the flash i have since it seems no sound comes out of youtube videos, but music plays in Banshee with a problem.

---

### Post by sdennie on 2008-06-24
I would see Section B of this thread: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578).  It describes your problem and the workaround.

---

### Post by chelovik on 2008-06-24
Don't use the .RPM version, rather the tar.gz version ... I successfully installed Flash9 into Firefox about five minutes ago, and have just replied to someone asking the same problem .... but here is my reply to save you searching ....

I am on Ubuntu 7.(Gutsy) but this is a Firefox issue, not OS.

My steps were:
1. unload the AdobeFlash installer from their site (you probably have ... I found the "install_flash_player_9_linux.tar.gz" works, so get that version

2. extract this to a folder, say "Documents" ... if you aren't sure how to extract, simply open the downloaded file, and you will see an Extract button. Navigate to an appropriate directory and press Extract

3. Open a terminal, and "cd" to the folder ... in my case it was:
cd /home/pe/Documents/install_flash_player_9_linux

4. Issue the following command:
./flashplayer-installer

5. You will now need to close any Firefox sessions you are using, and follow the instructions on the terminal ... ie, reply "y", "y", "y" ...

Done .... it worked first time for me.

Should you get a problem with the install, try:
sudo ./flashplayer-installer

This will bump your security to root, and run. Not the best command to run for every action, but in this case, Adobe software is trusted.
- cheers

---

### Post by ahriman22 on 2008-06-24
> **vor said:**
> I would see Section B of this thread: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578).  It describes your problem and the workaround.

I received yet another error while doing part B:
 Package libflashsupport is not installed.
  Package libasound2-plugins is not installed.
dpkg: error processing flashplugin-nonfree (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 flashplugin-nonfree

I got that after i pressed enter after entering:
sudo dpkg -i flashplugin-nonfree_10.0.1.218ubuntu1_i386.deb

---

### Post by ahriman22 on 2008-06-24
> **chelovik said:**
> Don't use the .RPM version, rather the tar.gz version ... I successfully installed Flash9 into Firefox about five minutes ago, and have just replied to someone asking the same problem .... but here is my reply to save you searching ....

I am on Ubuntu 7.(Gutsy) but this is a Firefox issue, not OS.

My steps were:
1. unload the AdobeFlash installer from their site (you probably have ... I found the "install_flash_player_9_linux.tar.gz" works, so get that version

2. extract this to a folder, say "Documents" ... if you aren't sure how to extract, simply open the downloaded file, and you will see an Extract button. Navigate to an appropriate directory and press Extract

3. Open a terminal, and "cd" to the folder ... in my case it was:
cd /home/pe/Documents/install_flash_player_9_linux

4. Issue the following command:
./flashplayer-installer

5. You will now need to close any Firefox sessions you are using, and follow the instructions on the terminal ... ie, reply "y", "y", "y" ...

Done .... it worked first time for me.

Should you get a problem with the install, try:
sudo ./flashplayer-installer

This will bump your security to root, and run. Not the best command to run for every action, but in this case, Adobe software is trusted.
- cheers

Thanks, but it's telling me "cd /home/japanfan/Documents/install_flash_player_9_linux no such file or directory"

If it helps I'm not using the Live Cd, i only used it for the installation.

---

### Post by ahriman22 on 2008-06-24
Well, i did it, finally. I opened documents and opened the extreacted file and then ran the installer in the terminal...
Thanks anyways.

---

