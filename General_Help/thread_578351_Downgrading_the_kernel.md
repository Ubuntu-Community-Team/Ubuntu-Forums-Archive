---
title: "Downgrading the kernel"
date: 2007-10-17
forum: General Help
---

### Post by gerdemb on 2007-10-17
I am running fiesty with kernel 2.6.20-16-generic. Unfortunately, I have a 3rd software package (FPGA tools from Xilinx) that will only work with kernel 2.6.18. How can I downgrade? In Synaptic I can only see 2.6.20.* kernels when I go to Package | Force Version....

---

### Post by DagMan on 2007-10-17
Will it by chance work with the 2.6.17 kernel or is it 2.6.18 specifically?  I'm asking because if it's the case of the 2.6.17 then you can download the kernel source and pull a config file out of the image package then compile it on your current system.  Otherwise you'll need to download the 2.6.18 kernel from kernel.org and compile it.  Unless you know well what options you want, the best thing would be to download the 2.6.17 image package and pull it apart with file-roller untill you get the config file from /boot/config-2.6.17-whatever-something then run make oldconfig and make menuconfig on the 2.6.18 kernel.  If this is too obscure of instructions, post agian and I or someone else can be more detailed at it.

The downside of compiling the 2.6.18 kernel is that it will lack the ubuntu patches and restricted drivers so if you need anything for example wireless that doesn't have support in the kernel or some graphics card drivers, then it will take compiling separately.  The 2.6.17 ubuntu one was fully patched last I saw it but it may have been separated since then into differant packages as well.

---

### Post by gerdemb on 2007-10-18
Thanks for your reply! I should be able to work with any kernel, 2.6.18 or earlier, so 2.6.17 would be fine.  I couldn't follow your directions about pulling a config file out of the image package. Do you mean pulling the config file from the 2.6.20 kernel I'm using now and applying it to the 2.6.17 kernel? Can you explain in more detail or maybe there's some documentation somewhere? Sorry, I'm a bit of a beginner at all this and need a little more hand holding. :)

Also, how do I download the 2.6.17 kernel package if it's not listed in Synaptic.

Cheers,
Ben

---

### Post by DagMan on 2007-10-18
alrighty, this is the dowload link for the edgy kernel-source which is 2.6.17
[http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-source-2.6.17_2.6.17.1-12.41_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-source-2.6.17_2.6.17.1-12.41_all.deb)
but it will be a .deb file, make sure you select to download it and not install it.  

Then open it with archive manager by right clicking on it and selecting archive manager or file-roller.

Extract the file that says data by highlighting it and selecting extract with 'selected file' or something like that as the option but this has always been and automatic settng for me, and this too will be a comprssed file called data.

Open the extracted file called data with the archive manager, then navigate aroud in it before extracting and get to /usr/src/linux-source-2.6.17.tar.bz and with it highligted select to extract it as above.

mv it to /usr/src
```
sudo mv linux-source-2.6.17.tar.bz /usr/src
```
and you can now delete all the files you downloaded and extracted.
Getting the kernel-source this way is better because the edgy kernel still has the ubuntu patches in it and not extra modules, however if you need restricted modules then that is another persuit in itself and building neither this nor a kernel from kernel.org will get you them.  You'll have to compile them separately or look at patching this kernel before you compile.  Keep in mind that with many things such as firmware, especially for some of the wireless cards, can be considered restricted but in reality doesn't need a recompile but just a symlink or copying the existing firmware to a new one changing the name to the kernel being built.  If you know you're using restricted drivers then it's worth looking into what to do before compiling.


Now to get the config file:
download the linux-image package for this kernel
this is for i386 or 32 bit arch 
[http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-12-generic_2.6.17.1-12.41_i386.debhttp://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-12-generic_2.6.17.1-12.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-12-generic_2.6.17.1-12.41_i386.debhttp://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-12-generic_2.6.17.1-12.41_i386.deb)
and this is if you're running the 64 bit install
[http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-12-generic_2.6.17.1-12.41_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-12-generic_2.6.17.1-12.41_amd64.deb)
Make sure you choose the right one.
I'm finding all these packages here btw, it's pretty handy [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Okay same thing, right click on the package, and select to open it with the archive manager or file-roller and exrtact the file called data.  Then open the file called data with archive manager and find in it /boot/grub/config-2.6.17-12-generic and extract it.
this next step isn't necisarry but more organised for me
move that file to /usr/src
I'de rename it to make it simpler as well
```
sudo mv config-2.6.17-12-generic /usr/src/config-downgrade
```

you can delete all the downloaded and extracted files left over again.


Now to compile
From this thread: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) and modified, more credit though to the old UDSF Dapper kernel compilation article by TsEliot but it isn't there anymore.
Do the following:
```
cd /usr/src
sudo tar -xvjf linux-source-2.6.17.tar.bz2
sudo rm linux
sudo ln -s linux-source-2.6.17.tar.bz2 linux
cd linux
sudo cp /usr/src/config-downgrade ./.config
```
you make get an error when you type rm linux... ignore it if it happens.

It's worth saying here that you can build the kernel to be of your processor architecture and get a little boost possibly and since your compiling it, it's silly not to do it.

```
sudo make menuconfig
```
go to processor type and features and hit enter
go to proccessor family and hit enter.  if you see that you can change it to something more specific to what you have then do so by using the arrow keys to highlight it and then hit space.  exit exit exit on the bottom selection until your out of it, and if you indeed made a change to something then it will ask you if you want to save the config, choose yes if it asks and you changed the processor type or changed another setting.

```
sudo make-kpkg clean
```
and to compile, which will take a very long time, hours if you have a slow processor.
```
sudo make-kpkg --initrd --append-to-version=-benrocks kernel_image kernel_headers
```
and if you have modules to compile and know what your'e doing there, then this instead
```
sudo make-kpkg --initrd --append-to-version=-benrocks kernel_image kernel_headers modules_image
```
I think you can just use the second one in general and get an error without it killing the compile but I wouldn't take the chance.  Use the first route if you are unsure.

When it's done compiling and if it did not exit with errors, it will have build .deb packages to install.
```
cd ..
ls *.deb
```
Hopefully there's a couple of packages there to install that say 2.6.17 somewhere in the long filename that they have in which case

```
sudo dpkg -i *2.6.17*deb
```
and if you get any errors about firmware or something that you can't work out then post here and maybe someone can help with that.  I have to do a few small and easy things to ensure some firmware is there named correctly for the new kernel.

You'lle need to select this kernel at grub or if you plan on it being your primary kernel then move it to the top of your menu.lst file in /boot/grub so it is the default one to boot into, but if you have your grub set to hidden menu then on reboot you need to hit escape or whatever it tells you, so you can select this kernel.

After all of this, if the software you're trying to use doesn't work, you type into the terminal
```
This sucks
```
then go and do something you really like so you don't stay angry... Good luck!

---

