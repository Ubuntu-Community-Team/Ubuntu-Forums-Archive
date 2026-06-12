---
title: "OpenGL and Xubuntu 12.04"
date: 2012-10-18
forum: General Help
---

### Post by oaxacamatt1 on 2012-10-18
I am trying to install a piece of software (Starlogo TNG) that requires openGL on my gateway laptop.  I cannot properly install the software, I can run gdeb installer but it just seems to drops out.

I cannot figure if I have openGL already installed or not and if so how to setup openGL. I have intslled Java jre 1.7 recently into /usr/java so I thought should do the trick...

Gateway NV51B08u: powered by a 1.0GHz AMD FUsion C-50 series APU, 3GB RAM and a 320 GB hard drive. The laptop has a AMD Radeon HD 6250 graphics GPU.

Any help would be greately appreciated,

---

### Post by Frogs Hair on 2012-10-18
Have you enabled compositing under window  manager or window manager tweaks ?  I'm logged into a different desktop at the moment and can't check which one it is.

---

### Post by efflandt on 2012-10-18
Under **Additional Drivers**, is **FGLRX** activated and in use?

if you do not have mesa utilities installed do:```
sudu apt-get install mesa-utils
```Then see what vender an versions show for:```
glxinfo | grep string
```I thought my Acer W500P 2 GB tablet PC w/C-50 cpu had HD 6250, but OpenGL renderer shows HD 6310.  It has Win7 Pro on 32 GB SSD and I boot 64-bit Ubuntu (or Lubuntu) from its SD card slot.

I don't know if I can try StarLogo TNG (not sure if the deb version includes 64-bit) and it says it requires Sun JRE (actually it has been Oracle Java for some time) which requires special installation instructions for Ubuntu.  I only have openjdk-6 on the tablet PC (for minecraft), and openjdk-7 on my desktop for minecraft related tekkit server.

There is something in the Ubuntu Software Center called eToys that is apparently similar to starlogo and other LOGO like programs, although, it may use scripting rather than drag and drop.

PS: Now that I think about it, for java, bits of the OS should not matter.  And control file in the deb file says "Depends: sun-java6|openjdk-6-jre" (is it still sun-java or is it oracle-java now?).  However, I have trouble installing it.  When I use sudo dpkg -i to try, it says:

```
dpkg: error processing starlogotng_1.0_all.deb (--install):
 unable to open file '/var/lib/dpkg/tmp.ci//.svn': is a directory
Errors were encountered while processing:
 starlogotng_1.0_all.deb
```But not sure what that means because afterwards there is no tmp.ci in /var/lib/dpkg

PPS: If you have 32-bit Linux the starlogotng_1.0_i386.tgz version may work by just extracting it and running it from there.  But unfortunately it does not include 64-bit versions of a bunch of 32-bit only libj...so files, so even with the ia32 libs in 64-bit Linux and java, it gets as far as displaying the starlogo opening logo, then chokes with wrong bit version for the first .so it tries to use.

---

