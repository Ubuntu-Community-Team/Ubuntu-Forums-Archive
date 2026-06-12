---
title: "Virtualbox problem"
date: 2007-08-06
forum: General Help
---

### Post by baz.g on 2007-08-06
please help :)

ok, i installed virtual box and set up a virtual machine but when i click start i get:

```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

```

and when i try to add the user i get:

```

administrator@administrator-laptop:~$ usermod -G vboxusers -a administrator
usermod: unable to lock password file

```

:( i thought i was getting somewhere too :(

lol oh well everybody has to start somewhere ey? :)

pleeeez help again :)

---

### Post by be4truth on 2007-08-06
How did you install VirtualBox?

---

### Post by nitro_n2o on 2007-08-06
probably you need to append "sudo" to your commands

---

### Post by soxs on 2007-08-06
I downloaded it from virtualbox.org and added my user via the gui to the vboxusergroup and rebooted and everything was fine.

---

### Post by be4truth on 2007-08-06
Means your problem is solved?

---

### Post by soxs on 2007-08-06
well, if I was baz.g.. yes
but I am not..
me == soxs

---

### Post by baz.g on 2007-08-07
lol yeh this got a bit confusing this thread but, yes i can now start virtualbox with no probs many thanks, its just now i realise that i was very naiive in not realising i actually needed a windows disc to install with lol, i only have the recovery disks that came with my laptop, so maybe i need to try something different now.

any suggestions gratefully received :)

many thanks in advance

Baz :)

---

### Post by forestpixie on 2007-08-07
I did for a short while have my existing windows install running inside vmware - can't remember whether it was player or server though. Didn't actually use it much as the only thing I used win for was printing - but once I had an HP printer it all went bye bye along with windows.

Effectively I used their converter to convert my win install to a virtual machine - it did take quite a bit of HDD space (you can still access win as normal) - then the vmware 'thing' would load it as a virtual machine.

[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

---

### Post by baz.g on 2007-08-07
its annoying, the only thing i want access to microshite for is tomtom home to update my gps every so often :(

---

### Post by forestpixie on 2007-08-07
sorry I can't help more - give tomtom a good earbashing, (I do assume you've had a look for software) - relieve some stress :)

good luck with it though

Edit - have you seen this

[http://www.opentom.org/Hosted_Software](http://www.opentom.org/Hosted_Software)

---

### Post by baz.g on 2007-08-07
thanx so much for your help, unfortunately none of those sites programs will do what i need them to so i will be sending a few emails to tomtom instead :)

again thanx very much for your input mate :)

Baz

---

