---
title: "VM doesnt install windows!"
date: 2007-09-26
forum: General Help
---

### Post by light-angel on 2007-09-26
I've installed VM server from  add/remove programs and i everything went fine. i created a new virtual machine compatible with windows xp professional without a problem. 

But when i tried to install windows in it nothing happends, the screen becomes black after the vm logo appears.

the first time i tried to install it, it worked but i wasn't sure the CD were burn well so i close it.It hasn't done the same ever since. i test the cd in my computer and it worked fine so its defenily vm.

by the way is there any way to delete an existin g virtual machine?

Thanx in advance

---

### Post by bionnaki on 2007-09-26
use virtualbox instead

---

### Post by light-angel on 2007-09-29
i followed your advice and installed virtualbox but still can install it.

i get the following message when i turn on the virtual machine on Virtualbox:

> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}



where do i change those sentings :S

---

### Post by bodhi.zazen on 2007-09-29
For VirtualBox, go to :

System -> Administration -> Users and Groups

Enter password

Click the "manage groups" button

Add your user to the "vboxusers" group

You then need to log out an back in for the changes to take effect

Re-start VirtualBox

---

