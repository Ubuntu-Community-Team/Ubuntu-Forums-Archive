---
title: "Ahh crap, what did i do...virtualbox install help/screw up"
date: 2007-03-27
forum: General Help
---

### Post by ssc351 on 2007-03-27
So I went to go download and install virtualbox.  As the install started, i accidently closed the program and shut down the computer.  Now when i go to synaptic i get: 

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I tried reinstalling from the .deb file but I get an error saying it can't open the file because it might be corrupted or you are not allowed to open the file.

Any help?

---

### Post by ssc351 on 2007-03-27
anyone anyone?  I am running fiesty...being a noob I have no idea where to start.

---

### Post by enlightened on 2007-03-27
I had the same problem just now, I fixed it by using command line 
$ sudo dpkg -i VirtualBox_1.3.8_Ubuntu_edgy_i386.deb
I hope that would help, good luck:)

---

### Post by ssc351 on 2007-03-27
Still doesn't work, when i go into terminal and type in that command it brings up something really fast which i can't read and then a blue screen fills the terminal which is the intial install screen for virtualbox but it doesn't continue beyond that.

Any more help?

---

### Post by isecore on 2007-03-27
I found that this thing helped. I found it over at [Ubuntugeek]("http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html"), and it helped me out of this annoying situation.

> Debian packages: If the installation of the VirtualBox_*.deb package was not successful because the compilation of the kernel module fails, it might not be possible to remove the package nor to install other packages as the pre-remove (prerm) script of the package (which is executed prior to package removing or upgrading) aborts with an error &#8220;(Kernel module not found)&#8230;fail!&#8221;. In that case do the following:

Edit /etc/init.d/virtualbox and change line 129 from &#8216;exit 1&#8242; to &#8216;exit 0&#8242;

Reinstall the virtualbox package by &#8216;dpkg -i &#8216;. An installation failure of this package is expected.

Edit /var/lib/dpkg/info/virtualbox.postinst and change line 39 from &#8216;exit 1&#8242; to &#8216;exit 0&#8242;

Execute &#8216;dpkg --configure --pending&#8216;

The package should now be installed successfully. However, the kernel module is still not compiled. Before you will be able to execute VirtualBox you have to create a kernel module for your current kernel, as described in the User Manual(check the link provided at the end of the article) 

However, I didn't proceed with the installation after I fixed that problem, I just apt-get uninstall --purge'd it all away. Virtualbox needs a smoother installprocess, IMHO.

---

### Post by ssc351 on 2007-03-27
Sorry can you give me what exactly to type into terminal...I don't think I am typing in the proper conditions.  Newbie :)

---

### Post by enlightened on 2007-03-27
you might want to try cleaning the bad pacykage first by using this command
$ sudo apt-get clean
then
$ sudo dpkg -i VirtualBox_1.3.8_Ubuntu_edgy_i386.deb

---

### Post by gklein on 2007-03-28
I found that this thing helped. I found it over at Ubuntugeek, and it helped me out of this annoying situation.

Quote:
Debian packages: If the installation of the VirtualBox_*.deb package was not successful because the compilation of the kernel module fails, it might not be possible to remove the package nor to install other packages as the pre-remove (prerm) script of the package (which is executed prior to package removing or upgrading) aborts with an error “(Kernel module not found)…fail!”. In that case do the following:

Edit /etc/init.d/virtualbox and change line 129 from ‘exit 1&#8242; to ‘exit 0&#8242;

Reinstall the virtualbox package by ‘dpkg -i ‘. An installation failure of this package is expected.

Edit /var/lib/dpkg/info/virtualbox.postinst and change line 39 from ‘exit 1&#8242; to ‘exit 0&#8242;

Execute ‘dpkg --configure --pending‘

The package should now be installed successfully. However, the kernel module is still not compiled. Before you will be able to execute VirtualBox you have to create a kernel module for your current kernel, as described in the User Manual(check the link provided at the end of the article)
However, I didn't proceed with the installation after I fixed that problem, I just apt-get uninstall --purge'd it all away. Virtualbox needs a smoother installprocess, IMHO.


I tried this...im pretty sure i have the same problem as him....when i try to edit the files...they are blank!!

---

### Post by ssc351 on 2007-03-28
when I try to put in the 1st edit line I get a warning saying "unknown mim-type for ..."
then it reads "error : no write permissions for.."

I tried using sudo and messing around with the file name but nothing.

Also, I tried enlightened's latest post and still get that blue install screen popping up
 
Doing the get-clean command doesn't seem to do anything, i type it in then my password, then it just brings up the command prompt again.

---

### Post by ssc351 on 2007-03-28
Found the fix here [http://www.ubuntuforums.org/showthread.php?t=388367&highlight=virtualbox](http://www.ubuntuforums.org/showthread.php?t=388367&highlight=virtualbox)

---

