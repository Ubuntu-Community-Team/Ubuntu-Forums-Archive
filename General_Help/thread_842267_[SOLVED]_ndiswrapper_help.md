---
title: "[SOLVED] ndiswrapper help"
date: 2008-06-27
forum: General Help
---

### Post by Blackprint on 2008-06-27
hi,

i should mention i am a complete linux noob but would like very much to learn.

i am trying to get my netgear wg111v3 wireless adapter working. i have found out that i need ndiswrapper. i have downloaded this and when i try to "make" it gives me an error mentioning the kernel source code. after looking around for hours now i cannot find a real solution. i have found this info

"Requirements:

· You need a recent kernel at least 2.6.6 or 2.4.26 with source. Under Red Hat or Mandrake, the sources can be installed using the package kernel-source< kernel-version >.rpm. Make sure there is a link to the kernel source from the modules directory. /lib/modules/VERSION/build should be a link to the kernel source, where VERSION is the version of the kernel you are running. If there is no link, you'll get an error at the make install step. To create a link, assuming the kernel sources are present, use the command

ln -s /usr/src/linux-< kernel-version > /lib/modules/VERSION/build

· Make sure you have started compiling the kernel sources, so needed header files are present. Some vendors ship ndiswrapper in their distributions. Either use it or make sure you remove it before installing ndiswrapper by yourself. Make sure you have the Wireless Tools installed. Again, there is a package that comes along with Red Hat and Mandrake distributions. If you are using Debian you can install the wireless-tools package from the mirror"

my problem now being, how do i find my kernel version so i know what to put in < kernel-version > in the command above. and it says assuming the sources are present. how do i check they are and if not how do i get them. i have LAN access for now so I can download things straight from the net to the box.

sorry for all the questions but it seems everytime i find a solution to one problem i get pushed back one more step!

i am trying to use eAR os which is based on ubuntu. if you need any more info let me know and i will try to provide it.

---

### Post by ajmorris on 2008-06-27
hi there,
are you trying to compile the ndiswrapper source? because you can just install it from the repositories using ```
sudo apt-get install ndiswrapper-common ndiswrapper-utils
```
And also ndisgtk if you want a GUI front-end

AJ

---

### Post by Blackprint on 2008-06-27
Hi,

To be honest I have no idea what I am trying to do, lol.

I basically want to get the drivers working for my wireless usb adapter.

If there is an easier way to do this and I am making a right mess of it, let me know. I could really use some instructions right from the beginning. I will try to install using the command you have given above. unfortunately I am at work now so cant test.

---

### Post by ajmorris on 2008-06-27
yep, just run that command i gave when you can.

Then, download the windows drivers for your card.
Extract them somewhere (cabextract <driver.exe>)  (cabextract is installed along with wine, sudo apt-get install wine)
then run sudo ndiswrapper -i <driver.inf> (from the .exe file you just extracted)
then run sudo ndiswrapper -l to verify it is installed
Then run sudo modprobe ndiswrapper, and sudo iwconfig should show your card :)

AJ

---

### Post by Blackprint on 2008-06-27
thanks for all that info. i will give it a try tonight. i have managed to get the files from somewhere and extract the contents to my home folder last night. does it matter where they are extraced to? do i have to point "sudo ndiswrapper -i <driver.inf>" anywhere or do I "cd" to the directory and run it from there.

---

### Post by Taxman415a on 2008-06-27
The latter. ndiswrapper -i will install it where it needs to go.

---

### Post by issih on 2008-06-27
As a new user, your best bet is to use ndis-gtk, which is a nice litle gui front end to ndiswrapper.

Provided you have a hardwire connection to the internet set up, just enter:

```
sudo apt-get install ndisgtk
```

Which will install ndiswrapper and its gui front end. You can now go to System->Administration->Windows Wireless Drivers, and just use the gui to set ndiswrapper up using the files you have extracted from your windows drivers.

---

### Post by Blackprint on 2008-06-27
i do have a hardline i can try when i get home. will post the results tonight.

thanks for all the help!

---

### Post by Blackprint on 2008-06-27
worked perfect with the GUI. wireless connection up and running right now!

cheers for all the help

---

