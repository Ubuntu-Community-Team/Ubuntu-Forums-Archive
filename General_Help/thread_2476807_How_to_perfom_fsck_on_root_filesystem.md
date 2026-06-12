---
title: "How to perfom fsck on root filesystem"
date: 2022-07-08
forum: General Help
---

### Post by veedub67 on 2022-07-08
Hello,

I'm using 22.04

I'm trying to follow the instructions here [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

At step 7: I'm prompted to give the root password for maintenance.

To the best of my knowledge 22.04 root doesn't have a password. If it does, I don't know it. So I can't comply.

The other option is Ctrl-D, which returns me to the Recovery Menu

There is an fsck option in the Recovery Menu, although the Wiki makes no mention of this option.

So I try fsck since it seems to be the only option available

It then says that /dev/sda2 is mounted. So I can't see how fsck can be performed

This is confirmed when it says e2fsck cannot continue.

And it returns to the Recovery Menu.

Surely it should not be this hard?

Hopefully someone can point me in the right direction. 

Do I need to use a LiveCD environment to access the filesystem offline?

Thanks

VW

---

### Post by veedub67 on 2022-07-08
I forced a check using

```
sudo tune2fs -c 1 /dev/sda2
```

Not the preferred approach.

I'd still like to know how to access the file system via the console at startup

---

### Post by TheFu on 2022-07-08
We can edit the grub boot options PRE-boot and ask for an fsck to be run.  I think using the 'e' button will provide a line editor for modifying the boot options.
fsck.mode=force

This entire problem was cause when systemd took over booting and removed the ```
sudo touch /forcefsck
```.  They've refused to add it back. It is was a simple and elegant solution. Create a file named forcefsck at the root of any partition and at mount time, if it exists, run an fsck and **removed** the file.  Sigh.

[https://askubuntu.com/questions/1359037/how-to-run-fsck-on-the-root-partion-from-the-grub-menu](https://askubuntu.com/questions/1359037/how-to-run-fsck-on-the-root-partion-from-the-grub-menu) has a longer, harder, method that really makes no sense to me.

The other option is to boot from a flash drive into *Try Ubuntu* mode, then use fsck to check all file systems on the other storage, not on the flash drive.

In theory, using the recovery console, waiting for the text menu, and choosing the "fsck all partitions" option should work.  I've used that previously, but have never tested it on 22.04. Earlier this week, I saw someone claim that the recovery console boot was mounting the root partition, so preventing running fsck.  That is a bug.  Linux can be booted into RAM and the recovery console really needs to do that, IMHO.

---

### Post by ajgreeny on 2022-07-08
It is much easier to do this from a live system.

Boot to a USB live system of Ubuntu, eg, the one you probably used to install in the first place, then run command ```
sudo e2fsck /dev/sdx#
``` where **/dev/sdx#** is your root file system,

That will run and if it finds problems should offer to repair them for you.

---

### Post by TheFu on 2022-07-08
> **ajgreeny said:**
> It is much easier to do this from a live system.

Boot to a USB live system of Ubuntu, eg, the one you probably used to install in the first place, then run command ```
sudo e2fsck /dev/sdx#
``` where **/dev/sdx#** is your root file system,

That will run and if it finds problems should offer to repair them for you.

It is only easier if you are physically in the same location as the computer.  The removal of the /forcefsck option really has screwed remote management of systems if they didn't install an IPMI/DRAC/RIBLO adapter into the system.  And those devices bring their own security fails, unfortunately.  For example, the Dell iDRAC tool had a bug for years [https://www.datacenterknowledge.com/security/hackers-can-turn-your-dell-servers-remotely-using-newly-found-idrac-vulnerability](https://www.datacenterknowledge.com/security/hackers-can-turn-your-dell-servers-remotely-using-newly-found-idrac-vulnerability)  Remote consoles that support powering off and on a system, not just a reboot, are not cheap.

---

### Post by veedub67 on 2022-07-08
Thanks for the responses.

The fundamental issue here is not allowing root to have a password.

There is always a need to balance security against ease-of-use.

My view is that in not allowing root to have a password under any circumstances, that Ubuntu have gone overboard. 

The developers are certainly entitled to have a preference, a "best practice" from their perspective. But once you start enforcing choices unilaterally, I think that is a step too far.

Ultimately it should be up to the user to decide how to configure their systems. By all means, have root locked down by default, so that the user has to make an explicit choice to override the default (supposedly) best practice. But the user should have the choice.

As it stands, this is a mess.

---

### Post by TheFu on 2022-07-08
> **veedub67 said:**
>  The fundamental issue here is not allowing root to have a password.

There is always a need to balance security against ease-of-use.

My view is that in not allowing root to have a password under any circumstances, that Ubuntu have gone overboard. 


Well, anyone who knows how to provide root with a password, and feels the way you do, would have already handled that. It is trivial, just not the default.  

There is **nothing** special about the root name on the account. Again, anyone with sufficient basic Unix knowledge could do something else to get around any root password need too. This 2nd method is also trivial, just not documented anywhere. An intermediate Unix user should able to intuit this 2nd method from their knowledge of standard unix users and groups.  If not, they are probably assuming things that aren't actually valid.

There is no need for root to have a password on ANY Unix system.  sudo works fine.  I'm saying this with about 28 years as an Admin, developer and enterprise architect.  

But is is just my opinion.  You are free to have your own.  It won't change anything with Ubuntu or any of the other systems which have leveraged sudo the last 20+ yrs.

---

### Post by veedub67 on 2022-07-08
@TheFu

Thanks for responding.

I had another go at setting a password for the root account, as I had tried previously.

The issue, was that I was then trying to logon at the GUI to confirm that the root password had been set. This either doesn't work because of the security model, some other setting, or perhaps this is an undocumented feature.

In any event, I was able to login via recovery mode, so the password change had in fact worked.

As you say, the 22.04 recovery console is mounting the root partition, and it's not possible to unmount it, so in this instance the point is moot. But at least I'm learning how more of the Linux components operate and interact.

---

### Post by yancek on 2022-07-09
The 'root' password being requested is the password of the primary user you created when you installed the sysem so you would prefix and command requiring 'root' privileges with sudo, then enter the password of that primary user.

---

