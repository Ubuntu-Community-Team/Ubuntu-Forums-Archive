---
title: "broken fglrx &amp; xorg"
date: 2005-03-28
forum: General Help
---

### Post by Strider on 2005-03-28
Hi all,
Here's my system:

- Hoary 5.04, custom kernel (recompile to support battery on an ASUS Laptop).
- Downloaded fglrx drivers from ATI and compiled separately.

This evening I did some updates from the repository and now fglrx is broken.  When I try to run glxgears I get the following error:

glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory.

I also received an error from the updates when it tried to apply the "xlibmesa-gl" libraries.

Has anyone else experienced a similar issue/problem?  I'm thinking of reinstalling the fglrx module but not sure if that will fix the problem.

Thanks in advance.

---

### Post by StacyWebb on 2005-03-28
if you had it running prior to the update, just run:
 
sudo apt-get update
sudo apt-get dist-upgrade

again from a terminal (not in x) then restart x 
should solve your problems

---

### Post by Strider on 2005-03-28
Since the fglrx was done outside of the respository the libGL library was conflicting.  I think if I forced the overwrite, the library would be overwritten with the xlibmesa-gl library, which I don't want.  So I ended up doing the following to solve the problem and get the system working again with the fglrx drivers from ATI.  

> 
1. Stop gdm.  From the text based terminal do the following.
2. sudo modprobe -r fglrx.
3. sudo apt-get remove fglrx-6-8-0.
4. sudo /bin/rm -R /lib/modules/fglrx.
5. sudo apt-get install xlibmesa-gl (this was giving me problems when trying to update from within synatic).  Now it runs fine and updates the system.
6. locate the fglrx-6-8-0_8.10.19-2_i386.deb (this was created with alien using the RPM package from ATI).
7. sudo dpkg -i --force-overwrite <PATH>/fglrx-6-8-0_8.10.19-2_i386.deb.  This will install necessary libraries and create the module source under /lib/modules/fglrx.
8. change to /lib/modules/fglrx/build_mod.
9. sudo sh make.sh.  Change to /lib/modules/fglrx.
10. sudo sh make_install.sh.
11. modprobe fglrx.
12. Restart gdm.


Some of the steps above may not be necessary but that's what I did and system is working again... no broken libraries for fglrx.

Hope it helps.

---

### Post by Dracontopes on 2005-03-29
Yay thanks, worked fine :)

---

### Post by burnit on 2005-03-30
Hi all im administrator user Ubuntu just say Ubuntu the best distro i've try about this 5 years thanks for developer and any all make this one (sorry for my good english)^^
But got a prob with fglrx ati driver ok i begin
I install with synaptic all driver fglrx-xorg xorg-server common and all need to be work but dont work error module and fglrx gear 3d deosnt work 
now i try with your setting like erase and reinstall with ati driver rpm 
i do it alien for deb after dpkg i do sh make.sh but not work say 
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h
i search it not exist version.h or links its not corret maybe i download source kernel same not work not exist on source this file version.h
any idea some one thank for help please ^^
 got a hoary 5.04 last version on dvd install and my card is ati 9200 all update do it

---

### Post by StacyWebb on 2005-03-30
burnit
you need to download the header files for your running kernel

---

### Post by burnit on 2005-03-30
Thank you verry much its work fine but its not easy no way to find some one talk about header for roockie user not possible to know it ^^

---

### Post by meatball117 on 2005-03-31
Sorry for the dumb question, but I'm experiencing this same trouble and I haven't been able to find out how to actually install the header files for my kernel.. Can you point me in the right direction? I've been unsuccessful with google and STF'ing.. :(

Edit: Figured out how to do it. Since I've got a 386 kernel the command will be

sudo apt-get install linux-headers-386 

and it seemed to put the proper headers in.

---

### Post by burnit on 2005-04-05
Hi use synaptic and look search for header then choose your version kernel 
when you start computer you c your kernel version like that 2.6.10-5-686 then choose header 2.6.10-5-686 if its your version then say ok and its work

---

### Post by elasticwings on 2005-04-14
Hi, I've tried following your directions, but I continually keep getting 
[fglrx:firegl_init] *ERROR* Device not found!
FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-686/kernel/drivers/char/drm/fglrx.ko): No such device
failed.

I get this error upon running the sh make_install.sh

Any insight as to what to do to fix it?

---

### Post by elasticwings on 2005-04-14
Nevermind, I found the answer to my own question.  Apparently, the Radeon Mobility M6 LY is not supported by that driver.  *@$!  That sucks. :(

---

