---
title: "Ubuntu Software Updater Won't Apply Security Updates, Says No Space"
date: 2014-10-09
forum: General Help
---

### Post by carmen2012 on 2014-10-09
This morning, Software Updater opened up and said I had some security updates to apply.  Like always, I applied the updates but this time, I got the message "Not enough free disk space - The upgrade needs a total of 83.5 M free space on disk '/boot'.  Please free at least an additional 19.1 M of disk space on '/boot'.  Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.  I did run the sudo apt-get clean command but get the same error.

I should say:

1.  I am running Ubuntu 14.04 with whole drive encryption.  I took the default settings during the install.
2.  I have not really installed any additional applications on my PC except for Chrome, Filezilla and GUFW so I wouldn't think I have used up much space.  I also don't save files on my desktop, everything is in the cloud
3.  In File Manager, I right clicked on Computer under devices and selected properties.  It shows 9.9GB used, 453.1GB free.
4.  In the /Boot folder, there is 64.4MB of files.

I really don't know enough about Ubuntu on how to proceed and would really appreciate any help on how I can complete this update.

Thank you

---

### Post by Impavidus on 2014-10-09
We get this question a few times every week. As you use full disk encryption, you must have a /boot partition. This boot partition has filled up with old kernels. Uninstall the old ones. Usually you should be able to autoremove them.

---

### Post by carmen2012 on 2014-10-09
> **Impavidus said:**
> We get this question a few times every week. As you use full disk encryption, you must have a /boot partition. This boot partition has filled up with old kernels. Uninstall the old ones. Usually you should be able to autoremove them.

Sorry, I'm really new to this, how do you "uninstall" or "autoremove" them?  When I go into Files=>Computer, I do see a boot folder, can I just right click=>delete and then empty the trash can?

or

Is the above boot folder I mentioned different from the boot partition and if so, how do I access the boot partition?

Sorry for the newbie questions.

Thank you

---

### Post by nerdtron on 2014-10-09
See here to uninstall the old kernels. Be sure that the one you are using now has no issues before you erase the olde ones. The Synaptic method I think is the newbie friendly way.
[http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)

---

### Post by carmen2012 on 2014-10-09
> **nerdtron said:**
> See here to uninstall the old kernels. Be sure that the one you are using now has no issues before you erase the olde ones. The Synaptic method I think is the newbie friendly way.
[http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)

Thank you, I got it to work.  The Synaptic method looked easy, but I wasn't 100% sure which files to delete, some of the names sounded awfully similar.

I ended up going with the automated method below and then rebooted and it worked.  

Not that I understand this command, but I assume it is fully safe, I was a little concerned about running something I didn't understand.

 [FONT=Ubuntu Mono]sudo apt-get remove --purge $(dpkg -l 'linux-image-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d')


[/FONT]

---

