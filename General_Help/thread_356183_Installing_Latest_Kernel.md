---
title: "Installing Latest Kernel"
date: 2007-02-08
forum: General Help
---

### Post by PetePete on 2007-02-08
I want to install the latest (stable) kernel (2.6.20) 

is there any simple way of doing this? I dont want to delete my old kernel, just install the new one so i have the option in grub of choosing which one to load.

is there any repository i can add, so all i'd have to do would be install using apt-get or similar?

any EASY to follow guides maybe?

---

### Post by DagMan on 2007-02-08
You can search ubuntu packages, select Feisty which is using the 2.6.20 kernel, and see what's available.
[http://packages.ubuntulinux.org/](http://packages.ubuntulinux.org/)
If you're looking to compile that kernel with specific options, this guide has worked for me on dapper edgy and feisty: 
[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)

I must say that using the ubuntu kernel from feisty seems like the best option because it is patched well for extra hardware support and is patched specifically for ubuntu as I understand it.  I have used this kernel in a Dapper install though, and ran fine but did not play 100% well with my hardware.  Running Feisty with the Kernel, it did play just fine with the same hardware.  I haven't tried using it in an Edgy install, however an Edgy kernel will not run a Feisty install.  I didn't find any performance improvement with Fiesty so you have to first ask yourself why you want to run a later Kernel.  I saw no differance in responsiveness between the Edgy kernel and  the Feisty one.  Good luck whatever you decide though.

There is also a thread in the tutorials section called the master kernel thread r something like that if you want to search here for it [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100) that is supposed to give instructions on compiling custom kernels.  I haven't looked at it in a while but it was maintained as current (somewhat) when I last saw it.

I almost forgot, don't grab a Feisty kernel by editing your sources.list file just grab it and install it (and resticted modules and so forth if you need them) at the command line using **dpkg -i nameoffile.deb** ... I dont know what dependencies would be pulled in if you changed your sources.list and it could screw things up.  My upgrade to Feisty actually started out as a small mistake and then I kept fixing before I realised that upgrading was the easiest solution.  It's sort of embarrasing.

---

### Post by PetePete on 2007-02-09
thanks for the detailed guide
i'll try and install the fiesty one later, good tip about not changing my sources.list lol no doubt i would have done that !

one questio nthough
do i need to donwload and install anything other than just the linux-386 (2.6.20.6.1) package ?
what about headers? or source?

thanks

---

### Post by DagMan on 2007-02-09
If you're compiling your own kernel, you'lle want to download the source from here [http://packages.ubuntulinux.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-source-2.6.20_2.6.20-6.11_all.deb&md5sum=dc117b7cb45cdf32d668357f76073703&arch=all&type=main](http://packages.ubuntulinux.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-source-2.6.20_2.6.20-6.11_all.deb&md5sum=dc117b7cb45cdf32d668357f76073703&arch=all&type=main)
Move it to your home folder and then do this ```
sudo dpkg -i linux-source-2.6.20_2.6.20-6.11_all.deb
```

To get a config file for a compile, right click and select to open with the archive manager in the file downloaded from your closest mirror here. [http://packages.ubuntulinux.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-image-2.6.20-6-generic_2.6.20-6.11_i386.deb&md5sum=d322a790642260af31433afadc1345de&arch=i386&type=main](http://packages.ubuntulinux.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-image-2.6.20-6-generic_2.6.20-6.11_i386.deb&md5sum=d322a790642260af31433afadc1345de&arch=i386&type=main)
and click until you find the file config-2.6.20-5-generic in the boot folder.
Extract this file to your home folder by dragging and dropping it there slowly.  You'lle see a thing moving back and forth at the lower right side of the archive manager and when it stops you can drop. move it to your /usr/src folder like this```
sudo mv config-2.6.20-5-generic /usr/src
```and on the step on that kernel compile page I linked to in the previous post, where it says to do this:
```
sudo cp /boot/config-`uname -r` ./.config
```
do this instead:
```
sudo cp /usr/src/config-2.6.20-6-generic ./.config
```

Again if you are compiling, I recomend that when you get to the step where you've just typed in ```
sudo make menuconfig
``` that you go to 'processor type and features', find the enty that says 'processor type and family', hit enter and then if you find that your processor is there and higher up on the list, select it using the space bar.  This isn't a necissary step but can give you better performance and it's the number one reason for a lot of people to be recompiling an ubuntu kernel.



You can try to just download the deb files for the kernel headers and kernel image and install them using   sudo dpkg -i   but I have had this not work on breezy with a dapper kernel.
Good luck

---

