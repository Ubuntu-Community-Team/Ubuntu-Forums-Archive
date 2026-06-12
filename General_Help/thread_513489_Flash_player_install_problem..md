---
title: "Flash player install problem."
date: 2007-07-30
forum: General Help
---

### Post by upthelum on 2007-07-30
I'm trying to install Flash Player as i cant view some web content and i get this message, what should i do i've tried various paths but it doesn't accept them.

root@linuxhomepc:/home/install_flash_player_9_linux# ./flashplayer-installer

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as the "root" user.
Adobe Flash Player 9 will be installed system-wide.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...



Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla):

I use xubuntu with kde on asus board with onboard vga, gig ram, athlon 64.
Thanks

---

### Post by findnitin007 on 2007-07-30
[http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)

should help you!

Nitin

---

### Post by upthelum on 2007-07-30
I haven't tried any of those alternatives yet but i tried it again but not as root and got a messaage saying "installation complete, please remove xpti.dat from the components directory of the mozilla browser". 
I dont have this file so any other suggestions before i try the alternatives?

---

### Post by Gremlinzzz on 2007-07-30
Flash Player support on 64-bit operating systems
Flash Player is not supported for playback in a 64-bit browser.
However, you can run Flash Player in a 32-bit browser running on a 64-bit operating system.
Adobe is working on Flash Player support for 64-bit platforms as part of our ongoing commitment to the cross-platform compatibility of Flash Player. We have not yet announced timing or release dates.
To use Flash Player to view Flash content on a 64-bit operating system, you must run a 32-bit browser. this from adobe site.
[http://ubuntuforums.org/search.php?searchid=24588474](http://ubuntuforums.org/search.php?searchid=24588474)

---

### Post by upthelum on 2007-08-06
> **Gremlinzzz said:**
> Flash Player support on 64-bit operating systems
Flash Player is not supported for playback in a 64-bit browser.
However, you can run Flash Player in a 32-bit browser running on a 64-bit operating system.
Adobe is working on Flash Player support for 64-bit platforms as part of our ongoing commitment to the cross-platform compatibility of Flash Player. We have not yet announced timing or release dates.
To use Flash Player to view Flash content on a 64-bit operating system, you must run a 32-bit browser. this from adobe site.
[http://ubuntuforums.org/search.php?searchid=24588474](http://ubuntuforums.org/search.php?searchid=24588474)

Hey thanks. That link didn't seem to work. I tried opening the video and selecting to manually install the plugin and it then gave a message saying i need "application/x-mplayer2".
I did a search in synaptic but came up with mplayer which i installed with plugins. So i ran the installer again and it completed, said everything was hunkdory, so i then did a system restart for the sake of it, but when i try to view said videos again it still doesn't work. 
HELP!!!

---

### Post by upthelum on 2007-08-06
> **findnitin007 said:**
> [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)

should help you!

Nitin

Thanks i tried some of those alternatives with no success.

---

### Post by Bablefish on 2007-08-06
You could also try Add Remove the flash player is listed

---

### Post by upthelum on 2007-08-07
> **Gremlinzzz said:**
> Flash Player support on 64-bit operating systems
Flash Player is not supported for playback in a 64-bit browser.
However, you can run Flash Player in a 32-bit browser running on a 64-bit operating system.
Adobe is working on Flash Player support for 64-bit platforms as part of our ongoing commitment to the cross-platform compatibility of Flash Player. We have not yet announced timing or release dates.
To use Flash Player to view Flash content on a 64-bit operating system, you must run a 32-bit browser. this from adobe site.
[http://ubuntuforums.org/search.php?searchid=24588474](http://ubuntuforums.org/search.php?searchid=24588474)

I installed the 32 bit firefox successfully but it still wont work. I've just installed a load of other web browsers so will try that.

---

