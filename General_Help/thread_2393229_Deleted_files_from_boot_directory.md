---
title: "Deleted files from boot directory"
date: 2018-05-31
forum: General Help
---

### Post by abhijit10 on 2018-05-31
I have been using Ubuntu 16.04 LTS. Recently I have copied some files and directory from the boot directory to a new directory named boot1. Then I deleted those files from the boot directory. Then I shut down my PC. After that when I tried to login my Ubuntu OS, a error massage appears on the screen saying some files are missing and those are exactly the files I have deleted from my boot directory. Can anyone please suggest me a solution so that I can log in to my Ubuntu OS and recover my files ? Moreover, some of my important files are located in directories which are password protected with Cryptkeeper application. Will I be able to recover those files ? Any suggestion from your side would be highly appreciated.

thanks
Abhijit

---

### Post by TheFu on 2018-05-31
Welcome to the forums.

/boot is important for booting the OS.   Put them back. Restore from the backup you made or boot using alternate boot media (flash drive), then mount the boot area and put the files back.

Files that are installed through the package manager need to be removed through the package manager.

I have no idea about cryptkeeper.

---

### Post by abhijit10 on 2018-05-31
Thanks a lot. I'll try this out and hope it will work. If there is any other alternative, please let me know.
thanks 
Abhijit

---

### Post by TheFu on 2018-05-31
> **abhijit10 said:**
> Thanks a lot. I'll try this out and hope it will work. If there is any other alternative, please let me know.
thanks 
Abhijit

There are 500+ other alternatives, but they all result in putting the files back, with the correct permissions and ownership.

The best way to learn Unix is by breaking things, then fixing it. But learning that way means having backups is strongly required - or practice dangerous things on systems you can blow away without concerns.

---

### Post by abhijit10 on 2018-06-01
Thanks for your suggestions. The error massage I got is 
" file /vmlinuz-4.4.0-124-generic.efi.signed not found
alloc magic is broken at 0x79ccd420: 79b733c0 "

Can you please help me out with this? Also can you please suggest how to install a package in "try ubuntu" ?

thanks
Abhijit

---

### Post by oldfred on 2018-06-01
Boot-Repair has an advanced mode. You can totally reinstall grub2 and have it add the most recent kernel.

That may be quicker than trying to copy files back and setting permissions.

 Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by TheFu on 2018-06-02
> **abhijit10 said:**
> Thanks for your suggestions. The error massage I got is 
" file /vmlinuz-4.4.0-124-generic.efi.signed not found
alloc magic is broken at 0x79ccd420: 79b733c0 "

Can you please help me out with this? Also can you please suggest how to install a package in "try ubuntu" ?

thanks
Abhijit

You can install packages under "try ubuntu", but they will not be written to the disk.  It is just a temp file system in that environment. 

I'm curious.  By deleting /boot, what did you expect to happen?

---

### Post by abhijit10 on 2018-06-05
Thanks a lot brother. With boot repair the problem is solved. Thank you for your suggestion.

---

### Post by abhijit10 on 2018-06-05
The problem is solved with boot repair. Thank you for your valuable suggestion. Actually I when I tried to auto update my ubuntu, a massage was popped up saying that there is not enough memory in the boot directory. So, I move some files from the boot directory to another directory. I am not sure about the actual cause of the problem, but, the problem was solved with boot repair. Thank you for your suggestion brother.

---

### Post by oldfred on 2018-06-05
Most desktops do not need a separate /boot partition. But if using LVM or LVM and full drive encryption you will normally have a /boot partition.
And then you need to regularly houseclean old kernels.
You need to use dpkg to remove kernels or else you can have other problems as the dpkg database maintaining what you have installed may get out of sync.

       [https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

---

### Post by TheFu on 2018-06-05
> **abhijit10 said:**
> The problem is solved with boot repair. Thank you for your valuable suggestion. Actually I when I tried to auto update my ubuntu, a massage was popped up saying that there is not enough memory in the boot directory. So, I move some files from the boot directory to another directory. I am not sure about the actual cause of the problem, but, the problem was solved with boot repair. Thank you for your suggestion brother.

Any files installed through a package manager must be removed via the package manager.  Don't manually touch those files.   Things in /boot/  are that type of files almost always.  If you perform weekly maintenance using "apt", it should automatically remove old kernels, while keeping 2-3  of them.

Boot-repair used to be a good choice 90% of the time, but things have become more complicated and it is probably 50% or less correcting current systems. Happy that you got lucky, this time.

If this is solved, please help the community - Thread Tools button near the top.

---

