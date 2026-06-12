---
title: "Vmware: Running Solaris or FreeBSD"
date: 2007-04-10
forum: General Help
---

### Post by Kizilbas on 2007-04-10
Hello :)

Where can I download and install VMware. then download a Solaris OS and run it in the VMware window?

Do I have to install Solaris or is there a liveCD of Solaris or freeBSD?

thanks in advance.

---

### Post by rufius on 2007-04-10
Well I would personally recommend QEMU with kqemu over VMWare. Here's a link to some info about QEMU (and KVM if you have modern hardware):

[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

Even though it mentions WindowsXP you can easily modify those to work with FreeBSD or Solaris.

If you want VMWare then do the following: 
```
sudo apt-get install vmware-player vmware-player-kernel-modules vmware-tools-kernel-modules
```

I don't know of any Solaris live cd's. You'd probably have to get it from Sun and install it. [FreesBIE](http://www.freesbie.org/) is probably the most popular of the live cd versions of FreeBSD.

Hope this helps.

---

### Post by Kizilbas on 2007-04-10
Yes rufius this is actually more than a help, thanks so much to you :)

_**A few wonderings:**_

~What do these commands mean and what do they do:
'ls -al'
'finger' - what is finger used for? 

~Can I do a whois about an Internet Protocol address on the default Terminal window? What would I type into the terminal if I wanted to do whois?. Is pinging a host the same as in windows, i.e. **ping**?

'sudo' - What's the meaning of sudo?

---

### Post by rufius on 2007-04-10
'ls -al' - This is a command to list all the contents of a directory and list extra information like permissions and file size.

'finger' - This was an early form of remote directory services. Not really all that useful nowadays since most internet visible servers have it disabled. Its really only used on intranets.

You can run a whois from a terminal. Pinging is the same as windows.

Sudo is a commond to gain access to the super user account without actually logging into the super user account. Sudo allows you to run commands as root. It comes from the original command 'su' that allows you to login as the super user.

---

### Post by Kizilbas on 2007-04-10
> **rufius said:**
> 'ls -al' - This is a command to list all the contents of a directory and list extra information like permissions and file size.

'finger' - This was an early form of remote directory services. Not really all that useful nowadays since most internet visible servers have it disabled. Its really only used on intranets.

You can run a whois from a terminal. Pinging is the same as windows.

Sudo is a commond to gain access to the super user account without actually logging into the super user account. Sudo allows you to run commands as root. It comes from the original command 'su' that allows you to login as the super user.

Thanks very much rufius, you was all very helpful :)

When I installed Xubuntu it asked me to create a username and a password so I did, but sometimes when I try to run a few commands it says you should be on root or something like that, but I do have all privileges I think because from the Users and Groups menu I selected my username and ticked all the boxes.

any idea rufius?

---

### Post by rufius on 2007-04-10
There are some commands that only root can run. Just depends on the command.

---

