---
title: "HELP ! Darling Emulator on lubuntu 14.04"
date: 2014-07-02
forum: General Help
---

### Post by jhay2 on 2014-07-02
ok, anyone here already heard about Darling Emulator (OSX emulation on ubuntu)?

how did you install this succesfull on your device ? 


when i tried to install this . it failed because of umnet dependencies

> 
sudo apt-get install darling


it will return this error
"Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 darling : Depends: darling-i386:i386 (= 0.0.1-0~201407010723~rev10~pkg31~ubuntu14.04.1) but it is not installable
E: Unable to correct problems, you have held broken packages."



when i try this:
> 
sudo apt-get install darling-i386


this error appears 

The following packages have unmet dependencies:
 darling-i386 : Depends: darling-amd64 (>= 0.0.1-0~201407010723~rev10~pkg31~ubuntu14.04.1) but it is not installable
                Depends: libgnustep-base but it is not installable
                Depends: libgnustep-corebase but it is not installable
                Depends: libgnustep-gui but it is not installable
                Recommends: darling-tools but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


darling-i386 is for i386 system right ? 

my device is an i386 

but why it is depending on darling-amd64 too ?


please help if someone here already install darling-i386 on their i386 system .. :(



thanks in advance

---

### Post by bapoumba on 2014-07-02
How are you building or installing darling ?
[http://www.darlinghq.org/ubuntu-build-instructions](http://www.darlinghq.org/ubuntu-build-instructions)

---

