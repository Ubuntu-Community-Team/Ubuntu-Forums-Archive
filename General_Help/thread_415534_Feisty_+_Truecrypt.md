---
title: "Feisty + Truecrypt"
date: 2007-04-20
forum: General Help
---

### Post by raymond3 on 2007-04-20
I'm trying to get truecrypt 4.3 installed on a fresh Feisty install.

I have in /usr/src linux-headers-2.6.20-15, linux-headers-2.6.20-15-generic, and I downloaded and untarred linux-source-2.6.20.

When I do the ./build.sh and point the truecrypt build script to the linux-source folder I get the following error: Error: Kernel source version in /usr/src/linux-source-2.6.20 is not 2.6.20-15-generic


When I point it to the header folders I get: Error: Kernel source code is incomplete - /usr/src/linux-headers-2.6.20-15/drivers/md/dm.h not found.

help!

---

### Post by lynxus on 2007-04-20
Ive had this issue before.

do a 

# locate dm.h

and copy to /usr/src/linux-headers-2.6.20-15/drivers/md/

if you dont have it already do a google search.

i think you may also be prompted for another file aswell a bit like dm.h  ( been a while )

But shortly after overcoming this problem it all went smoothly for me.. So fingers crossed...

---

### Post by raymond3 on 2007-04-20
After doing that this is what I get:

ray@linux-desktop:~/truecrypt-4.3-source-code/Linux$ sudo ./build.sh 
Checking build requirements...
Linux kernel (2.6.20-15-generic) source directory [/usr/src/linux]: /usr/src/linux-headers-2.6.20-15-generic
Building kernel module... /home/ray/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.c: In function &#8216;truecrypt_map&#8217;:
/home/ray/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.c:511: error: dereferencing pointer to incomplete type
/home/ray/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.c: In function &#8216;truecrypt_status&#8217;:
/home/ray/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.c:609: error: dereferencing pointer to incomplete type
/home/ray/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.c:609: error: dereferencing pointer to incomplete type
make[2]: *** [/home/ray/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.o] Error 1
make[1]: *** [_module_/home/ray/truecrypt-4.3-source-code/Linux/Kernel] Error 2
make: *** [truecrypt] Error 2
Error: Failed to build kernel module

---

### Post by lynxus on 2007-04-20
Not sure what to suggest here..

I found installing build-essential  fixed a lot of my build issues... ( apt-get install build-essential ) i think essential spelt right...

---

### Post by raymond3 on 2007-04-20
Yeah, bummer.  I have build-essential installed already.

It's weird because others running 7.04 have it installed and I really haven't done anything out of the ordinary with this system...

---

### Post by lynxus on 2007-04-20
im about to do a fresh install of truecrypt myself..

Lets see what happens..

---

### Post by raymond3 on 2007-04-20
do share!

---

### Post by lynxus on 2007-04-20
Gah, same error:

root@broken-trumpet:/home/gsmart/Downloads/truecrypt-4.3-source-code/Linux# ./install.sh Checking installation requirements...
Checking build requirements...
Linux kernel (2.6.20-15-generic) source directory [/usr/src/linux]: /usr/src/linux-headers-2.6.20-15-generic/
Building kernel module... /home/gsmart/Downloads/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.c: In function &#8216;truecrypt_map&#8217;:
/home/gsmart/Downloads/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.c:511: error: dereferencing pointer to incomplete type
/home/gsmart/Downloads/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.c: In function &#8216;truecrypt_status&#8217;:
/home/gsmart/Downloads/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.c:609: error: dereferencing pointer to incomplete type
/home/gsmart/Downloads/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.c:609: error: dereferencing pointer to incomplete type
make[2]: *** [/home/gsmart/Downloads/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.o] Error 1
make[1]: *** [_module_/home/gsmart/Downloads/truecrypt-4.3-source-code/Linux/Kernel] Error 2
make: *** [truecrypt] Error 2
Error: Failed to build kernel module
Error: Build failed - installation aborted
root@broken-trumpet:/home/gsmart/Downloads/truecrypt-4.3-source-code/Linux#



oot@broken-trumpet:/home/gsmart/Downloads/truecrypt-4.3-source-code/Linux# ./install.sh Checking installation requirements...
Checking build requirements...
Linux kernel (2.6.20-15-generic) source directory [/usr/src/linux]: /usr/src/linux-headers-2.6.20-15
Building internal kernel modules (may take a long time)... make[2]: *** No rule to make target `ubuntu/acpi/dev_acpi.c', needed by `ubuntu/acpi/dev_acpi.o'. Stop.
make[1]: *** [ubuntu/acpi] Error 2
make: *** [ubuntu] Error 2
Error: Build failed - installation aborted
root@broken-trumpet:/home/gsmart/Downloads/truecrypt-4.3-source-code/Linux# 





Looks like its just meant to be :( no matter what sorces ya use to build :(

---

### Post by raymond3 on 2007-04-20
I don't get the feeling that the truecrypt folks care too much about Linux either.  Any alternatives to truecrypt?

---

### Post by lynxus on 2007-04-20
a couple, but i have true crypted usb drives.. so i will have to get this working somehow..

---

### Post by lynxus on 2007-04-20
Ohhh checkthis...


[http://ubuntuos.wordpress.com/2007/04/08/automatix2-now-available-for-ubuntu-704-feisty-fawn/](http://ubuntuos.wordpress.com/2007/04/08/automatix2-now-available-for-ubuntu-704-feisty-fawn/)


It mentions it comes with truecrypt and forcefeild!

Testing Testing.....

---

### Post by lynxus on 2007-04-20
Sorry mean here..

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Im testing now.. will post results.

---

### Post by raymond3 on 2007-04-20
I downloaded the 2.6.20 kernel source untared it and copied the dm.h file from there and it built without errors.

---

### Post by lynxus on 2007-04-20
FFS , it isnt included now :(

Sigh

---

### Post by lynxus on 2007-04-20
> **raymond3 said:**
> I downloaded the 2.6.20 kernel source untared it and copied the dm.h file from there and it built without errors.



Ahh , k ..trying now :)

Where did you get the source from ?

---

### Post by raymond3 on 2007-04-20
I did an apt-get linux-source-2.6.20 and it installed a tar ball in /usr/src

I could just post the file but I'm thinking that since this is a security software install you might want to make sure you are getting the real thing!

Oh, I have it up and running without errors now!

---

### Post by lynxus on 2007-04-20
AH HA,

Freaking sweet man!
Soo freakin sweet.

kernel headers and kernel sources allways annoy me..


in summary for any future people searching. :

- Download truecrypt source and untar
- Download the latest kernel headers and kernel sources  ( #  uname -r ) for your version
- Copy the dm.h file from the sources directory/archive and place in /usr/src/kernel source dir
- Change to teh truecrypt dir then into the Linux dir inside that.
- Run:
- ./build.sh
- ./install.sh


Game on baby!

---

### Post by argusBR on 2007-04-21
When I try to build Truecrypt 4.3 on Feisty, I get the following output:

```

Checking build requirements...
Building kernel module... make[1]: *** No rule to make target `and'.  Stop.
make: *** [truecrypt] Error 2
Error: Failed to build kernel module
```

I tried copying dm.h to the headers directory, but the error persists. Any idea of what might be the problem?


EDIT: Sorry, it was a stupid error of mine: I had placed the truecrypt source in a directory called "software and sources" (with spaces). I removed the spaces in the directory name and voilà! It worked.

---

### Post by Borisdieklinge on 2007-04-24
Hi I copied the dm.h from 

/usr/src/linux-source-2.6.20/drivers/md/dm.h

to /usr/src/linux-source-2.6.20/ and /usr/src/linux-headers-2.6.20-15/

but I got still this error:

```
Preparing kernel build system in /usr/src/linux-source-2.6.20... .config:1396:warning: trying to assign nonexistent symbol SATA_INTEL_COMBINED
.config:3539:warning: trying to assign nonexistent symbol RTL818X
make[2]: *** [silentoldconfig] Fehler 1
make[1]: *** [silentoldconfig] Fehler 2
make: *** Keine Regel, um »modules_prepare« zu erstellen.  Schluss.
```

any ideas?

thanks
Borisdieklinge

---

### Post by orb9220 on 2007-04-24
This worked for me without copying or modifying anything.

[http://forums.truecrypt.org/viewtopic.php?p=30365#30365](http://forums.truecrypt.org/viewtopic.php?p=30365#30365)

---

### Post by mtrudgia on 2007-04-24
> **raymond3 said:**
> After doing that this is what I get:

ray@linux-desktop:~/truecrypt-4.3-source-code/Linux$ sudo ./build.sh 
Checking build requirements...
Linux kernel (2.6.20-15-generic) source directory [/usr/src/linux]: /usr/src/linux-headers-2.6.20-15-generic
Building kernel module... /home/ray/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.c: In function ‘truecrypt_map’:
/home/ray/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.c:511: error: dereferencing pointer to incomplete type
/home/ray/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.c: In function ‘truecrypt_status’:
/home/ray/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.c:609: error: dereferencing pointer to incomplete type
/home/ray/truecrypt-4linux-headers-2.6.20-15-generic.3-source-code/Linux/Kernel/Dm-target.c:609: error: dereferencing pointer to incomplete type
make[2]: *** [/home/ray/truecrypt-4.3-source-code/Linux/Kernel/Dm-target.o] Error 1
make[1]: *** [_module_/home/ray/truecryplinux-headers-2.6.20-15t-4.3-source-code/Linux/Kernel] Error 2
make: *** [truecrypt] Error 2
Error: Failed to build kernel module

You are getting this problem because you haven't un-tarred the source tarball that was downloaded when you did an <apt-get install linux-source-2.6.20. This downloads two directories and one tarball into /usr/src:
  1) linux-headers-2.6.20-15
  2) linux-headers-2.6.20-15-generic
  3) linux-source-2.6.20.tar.bz2

If you don't untar the source tarball, you get the error above. Hope this helps you.

---

### Post by Yuzem on 2007-04-25
> **orb9220 said:**
> This worked for me without copying or modifying anything.

[http://forums.truecrypt.org/viewtopic.php?p=30365#30365](http://forums.truecrypt.org/viewtopic.php?p=30365#30365)

I am not a member.
Can you post the solution?
Thanks.

---

### Post by orb9220 on 2007-04-25
thats the way i have compiled truecrypt with feisty 7.04, i hope it's a little help some other ubuntu feisty truecrypt users who have problems with the compile process.

Code:

> sudo apt-get install build-essential dmsetup gawk linux-source linux-headers-`uname -r`

Thats to install the required software for the build process.

then

Code:

   > cd /usr/src/

    sudo tar xvjf linux-source-2.6.20.tar.bz2

    sudo ln -s linux-source-2.6.20 linux

    sudo make -d -C linux modules_prepare


i have downloaded linux-source via synaptic, no idea how to download it via comand line ;)

Go Here for Truecrypt Source Code  [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

back to the truecrypt download directory

Code:

    > tar xzvf truecrypt-4.3-source-code.tar.gz

    cd truecrypt-4.3-source-code/Linux/


to start the build process:

Code:

> sudo ./build.sh

this will take a long time ...

when it says 'Building truecrypt... Done'

Code:

> sudo ./install.sh


install process questions:

Quote:

> /dev/mapper/control not found - create? [Y/n]: y
Install binaries to [/usr/bin]: #PRESS_RETURN#
Install man page to [/usr/share/man]: #PRESS_RETURN#
Install user guide and kernel module to [/usr/share/truecrypt]: #PRESS_RETURN#
Allow non-admin users to run TrueCrypt [y/N]: y



On my P4 1.3ghz with 640mb ram compile took like 2.5-2.75 hrs.
And forcefield is a gui for truecrypt and in the repo's

truecrypt should work now.

---

### Post by Yuzem on 2007-04-25
Thank a lot for your help!!!

---

### Post by TheWizzard on 2007-04-26
works like a charm. thanks!

---

### Post by TheWizzard on 2007-04-26
if you don't want truecrypt in your terminal history, add:

```
# don't record truecrypt entries
export HISTIGNORE="&:*truecrypt*"

```
to ~/.bashrc

---

### Post by shields on 2007-04-26
Wow -- thanks for the info.  I followed your steps and they worked well.  

Does it work as a gui?  

How do I get it to show in my menus?

---

### Post by TheWizzard on 2007-04-26
> **shields said:**
> Wow -- thanks for the info.  I followed your steps and they worked well.  

Does it work as a gui?  

How do I get it to show in my menus?

it's command line. if i'm not mistaken there exists a GUI, but i've never used that.

---

### Post by orb9220 on 2007-04-27
Forefield GUI
[http://bockcay.de/forcefield](http://bockcay.de/forcefield)

---

### Post by fotherington on 2007-05-05
.deb Truecrypt package for Feisty now downloadable from [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php). The name implies it's for the 386 architecture only.

---

### Post by BlueN1nja on 2007-05-12
I'm new to really messing with the kernel, so bear with me here...

After having no success with the .deb from the website, I've been trying to compile from source.I haven't had any errors like the ones posted earlier in the thread, but build.sh is taking an EXTREMELY long time. It's been going for over two hours now. I'm running on an 850MHz P3... Is this kind of build time normal?

I don't want to have to go through this for every kernel upgrade. Is there a quicker way?

Everything works fine with the .deb up until when I try to mount the container-it gives me an error about not finding the Truecrypt module.

Thanks in advance.

---

### Post by shields on 2007-05-12
I see you posted this eight hours ago.  It should be done by now.  I used the same machine as you and it took all day.  After about three or four hours, I had to run.  When I came back a couple of hours later, it was done.

Let us know how it works, please.  :)

---

### Post by BlueN1nja on 2007-05-14
> **shields said:**
> I see you posted this eight hours ago.  It should be done by now.  I used the same machine as you and it took all day.  After about three or four hours, I had to run.  When I came back a couple of hours later, it was done.

Let us know how it works, please.  :)

I gave up since I was going to bed, but I've got it going again now and I'll let you know how it turns out.

---

### Post by BlueN1nja on 2007-05-14
> **BlueN1nja said:**
> I gave up since I was going to bed, but I've got it going again now and I'll let you know how it turns out.

Ok... Let it sit for a few hours and it eventually compiled (and works) but I'm wondering how to let a user without sudo privileges use it. I'm using version 4.3, and wasn't asked about non-root users when I ran install.sh.

Thanks for the advice.

EDIT: Added the user to /etc/sudoers with a command alias for truecrypt. Works fine now.

---

### Post by kjj on 2007-05-16
Am I missing the point here?

If I install truecrypt from the repositories, should I not expect it to work?

If there is a .deb for feisty on the truecrypt site, should this not just install as with other .debs?

Tried both and still getting the same terminal error about kernel module.

I would love to convert to using Linux full time, but it just seems that at every turn there is an issue that needs to be resolved and I end up rebooting to WinXP to make things work.

---

### Post by MiF on 2007-07-21
Before I could "make -d -C linux modules_prepare", I needed to:
   cp /boot/config-<version>-generic linux/.config

---

### Post by lynxus on 2007-07-21
> **kjj said:**
> Am I missing the point here?

If I install truecrypt from the repositories, should I not expect it to work?

If there is a .deb for feisty on the truecrypt site, should this not just install as with other .debs?

Tried both and still getting the same terminal error about kernel module.

I would love to convert to using Linux full time, but it just seems that at every turn there is an issue that needs to be resolved and I end up rebooting to WinXP to make things work.



you may be missing the point yes.

The reason this thread was created was because we couldn't install the latest version on the latest Ubuntu.
( Because no Deb files etc were created at that time )

Now you can just click and install.

Before hand we had to compile from source


If you look at the first 2 pages, try following wht we did and compile from source if it doesnt work normally

---

### Post by mali2297 on 2007-07-22
> **kjj said:**
> Am I missing the point here?

If I install truecrypt from the repositories, should I not expect it to work?

If there is a .deb for feisty on the truecrypt site, should this not just install as with other .debs?

Tried both and still getting the same terminal error about kernel module.

I would love to convert to using Linux full time, but it just seems that at every turn there is an issue that needs to be resolved and I end up rebooting to WinXP to make things work.

I got truecrypt working by following these instructions:
[http://blog.gnu-designs.com/truecrypt-on-ubuntu-fiesty-fawn-or-later/]("http://blog.gnu-designs.com/truecrypt-on-ubuntu-fiesty-fawn-or-later/")

It involves compiling from source.

---

