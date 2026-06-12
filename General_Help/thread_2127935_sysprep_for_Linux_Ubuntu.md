---
title: "sysprep for Linux Ubuntu"
date: 2013-03-21
forum: General Help
---

### Post by Binary-Synapse on 2013-03-21
Hello.

Is there (in Ubuntu or Debian) an equivalent program to Sysprep for Windows?

For example I would like to create a master HDD, run the sysprep equivament and then clone that disk so I can deploy it into slightly different computers.

Than when the end-user powers up the computer for the first time, he would be asked to input his user name, password, etc...
Just like Windowzz does.

I have heard of "sys-unconfig" for Fedora...
But what about for Ubuntu and/or Debian? Is there something similar?

Thank you.

---

### Post by Cheesemill on 2013-03-21
You can boot the Ubuntu installer in OEM mode to achieve the result you are after.

When you boot the installation media, hit SHIFT to get to the installation menu, then hit F4 and select 'OEM Install'.
When Ubuntu has finished booting install the system as usual, you will be prompted for a temporary username and password.

When installation has finished, boot the system and log on with the temporary username and password you created earlier, you can now make any other alterations to the system that you want, for example installing extra software. When you're all done just double-click on the 'Prepare for shipping to end user' icon on the desktop and then shut down the machine, it's now time to take your image of the drive.

Next time the machine is booted the user will be asked to set up their account.

---

### Post by Binary-Synapse on 2013-03-27
Hello Cheesemill.

Thank you for your response.
I will certainly try that!

Do you know if I can apply that same method to Debian?

Thanks

---

### Post by slickymaster on 2013-03-27
You might also take a look at [Virt-sysprep]("http://manpages.ubuntu.com/manpages/precise/man1/virt-sysprep.1.html"). It's a simple shell script and reset or unconfigure a virtual machine so clones can be made.

---

