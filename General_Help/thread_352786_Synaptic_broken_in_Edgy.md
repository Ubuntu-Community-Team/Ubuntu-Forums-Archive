---
title: "Synaptic broken in Edgy"
date: 2007-02-03
forum: General Help
---

### Post by Rich78 on 2007-02-03
Hi,

I tried to install VirtualBox via the deb file on the VirtualBox website, on my Edgy machine, it installed ok but did complain of something missing during the process.  

It still launched but gave me the following error: VirtualBox kernel  driver not installed.

I followed a post from this forum which suggested: sudo apt-get install linux-686

So I performed that and found it made no difference, I thought I'd remove the product but it said that it needed to be reinstalled but couldn't find the archieve.

Now my Synaptic package manager won't list any packaged but lists the following error:

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Can anyone help?

Thanks

---

### Post by taurus on 2007-02-03
Try

```
sudo aptitude --purge remove virtualbox
sudo aptitude update
```

---

### Post by Rich78 on 2007-02-03
Thanks,

Unfortunately I get:

The following packages have been automatically kept back:
  libwxbase2.6-0 libwxgtk2.6-0 python-wxgtk2.6 python-wxversion 
The following packages will be REMOVED:
  virtualbox 
0 packages upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 19.1MB will be freed.
Writing extended state information... Done
dpkg: error processing virtualbox (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors were encountered while processing:
 virtualbox
Aborted (core dumped)

It seems to be in a state where I can't remove it or reinstall it.

If I re-run the deb file from the gui desktopI get the following error prompt:

Could not open
'VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb'
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.

I right clicked on the deb file and changed all permissions to read/write for my current user but it makes no difference.

Any more ideas?

Thanks again

---

### Post by taurus on 2007-02-03
```
sudo dpkg -r VirtualBox
```

---

### Post by Rich78 on 2007-02-03
Same error:

dpkg: error processing virtualbox (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 virtualbox

---

### Post by notatoad on 2007-02-04
i'm getting this same error.  i tried the above, it didn't work for me either.  i also tried re-downloading the .deb and reinstalling, as well as downloading the dapper .dep.  neither worked.

the worst part is that i can't install anything else, as the error is locking me out of both graphical and commandline package managers

---

### Post by Rich78 on 2007-02-04
Not  good, did you do a sudo apt-get install linux-686 or just install VirtualBox via the deb package?  because I'm trying to work out whether it was the linux-686 kernel that broke it.

---

### Post by Rich78 on 2007-02-04
Just found a fix but haven't tried it yet.

Debian packages: If the installation of the VirtualBox_*.deb package was not successful because the compilation of the kernel module fails, it might not be possible to remove the package nor to install other packages as the pre-remove (prerm) script of the package (which is executed prior to package removing or upgrading) aborts with an error "(Kernel module not found)...fail!". In that case do the following:

    * Edit /etc/init.d/virtualbox and change line 129 from 'exit 1' to 'exit 0'
    * Reinstall the virtualbox package by 'dpkg -i <the VirtualBox package for your distribution>'. An installation failure of this package is expected.
    * Edit /var/lib/dpkg/info/virtualbox.postinst and change line 39 from 'exit 1' to 'exit 0'
    * Execute 'dpkg --configure --pending'
    * The package should now be installed successfully. However, the kernel module is still not compiled. Before you will be able to execute VirtualBox you have to create a kernel module for your current kernel, as described in the User Manual (see our Downloads section).

---

### Post by Rich78 on 2007-02-04
It does fix the problem, I'm now following the instructions to get the kernel module built

---

