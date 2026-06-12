---
title: "virtualbox permission error"
date: 2007-05-28
forum: General Help
---

### Post by uthturn on 2007-05-28
i follwed this howto
[http://ubuntuforums.org/showthread.php?t=433359&highlight=virtualbox+howto](http://ubuntuforums.org/showthread.php?t=433359&highlight=virtualbox+howto)
i got to the part where i boot up the virtual machine and install windows when i click start i get this error

VirtualBox kernel driver not accessible, permission problem. Make sure that the current user has write permissions to /dev/vboxdrv by adding him to the vboxusers groups. Don't forget to logout to take the change effect.
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 i tried creating a group vboxusers and put checked my user for it

---

### Post by chrisLACHCIK5084 on 2007-05-28
haha i knew this question would come up. ok it was weird for me cuz i looked all over and no one had answered my questions so i figured out the problem to this question.

first goto system->admin->users and groups

then click on manage groups

scroll down all the way to the bottom where you'll see vboxusers

click PROPERTIES and click the box next to your username (or all of them if you want)

then restart your computer and try again and it should work! 

:) easy guide for this problem.

---

### Post by chrisLACHCIK5084 on 2007-05-28
also there is already a group called vboxusers...it should've been created when you made a profile in Virtualbox

---

### Post by uthturn on 2007-05-28
I Did All That Still Get The Error Thanks For T He Reply

---

### Post by uthturn on 2007-05-28
nevermind i shut her down and now it works stay cool dude

---

