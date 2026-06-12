---
title: "Remove Kernel Update from Update Manager - 12.04"
date: 2013-06-02
forum: General Help
---

### Post by ProgenitorVirus on 2013-06-02
Hi there,

I recently had to compile a custom kernel to fix an audio issue.  The trouble I have now is where I compiled it myself and did not use a .deb, I'm lost on how to hide the update for the same version as the one I have (and have modified).

I'm currently running 3.5.0-32-generic custom, and Update Manager wants to install 3.5.0-32-generic vanilla...  

If I bring up the package in Synaptic Package Manager, and hit Package > Version, I see listed:

3.5.0-32.53-precise1 (precise-updates)
3.5.0-32.53-precise1 (now)

So again, where I didn't install the custom kernel as a package I can see in Synaptic, I can't really lock it to said package and have it ignore the updated version...  Any and all ideas welcome, thanks!

---

### Post by pbrane on 2013-06-02
I would recommend using kpkg to compile your custom kernel. That way it's a .deb package and you can lock it, remove it, or reinstall it as you need to.

See this link: [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")

I have used this method many times, it works great. I use the ubuntu kernel configuration method listed at the bottom. Once you have the control scripts for the ubuntu version your compiling you won't need to down load the entire kernel any more. Also you can get just the control scripts from git if you want to. Also you don't have to use the mainline kernel. I have used this method to build and install stable as well.

---

### Post by ProgenitorVirus on 2013-06-02
I've been looking into this, and was in error when I first said I wasn't using .deb files :s

I've followed this guide [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel), and where I just needed to add a few lines to a file, I didn't get too in-depth in the whole process.

In the end I had 3 files:

linux-headers-3.5.0-32_3.5.0-32.53~precise1_all.deb
linux-headers-3.5.0-32_3.5.0-32.53~precise1_all.deb
linux-image-3.5.0-32-generic_3.5.0-32.53~precise1_amd64.deb

I then installed them with $ sudo dpkg -i linux*3.5.0-32*.deb


I've tried renaming the files and reinstalling the kernel, this time through Ubuntu Software Center, which sees right past my name change and says it's already installed.

Where I have those 3 .deb files ready to go, is there anything I can do to just quickly rename the version to something different such that I can lock it?

---

### Post by pbrane on 2013-06-02
I always add the word 'custom' to my deb files using the '--append-to-version' option. I'm not sure if just renaming the files will accomplish anything here. You may need to re-compile.
My command line, in a script of course, is:
```

fakeroot make-kpkg --initrd --append-to-version=-custom --overlay-dir=$BASE_DIR/ubuntu-package kernel_image kernel_headers

```

I end up with only two files. the image file and the header file.

EDIT:

Actually you may be able to open the deb files with archive manager and edit the control scripts. The package names are in those scripts. You may have to hunt through the files to make sure you get them all.

---

### Post by ProgenitorVirus on 2013-06-02
Tried opening the .deb files with Archive Manager, and I found the control scripts, however it won't let me edit the files (it just saves a copy to a temporary location).

Rather than have to recompile using a different method than I'm familiar with, is there any way I can edit the file in the .deb?

---

### Post by ajgreeny on 2013-06-03
You will probably have to extract the .deb it to somewhere and work on the extracted file, not just on the listed file in archive manager, if that's what you did.

---

