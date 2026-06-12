---
title: "Password?"
date: 2023-08-19
forum: General Help
---

### Post by billywyatt2 on 2023-08-19
I recently ordered a new Ultima WS Home Office Workstation which had Microsoft Windows as the default OS. But i told the people from wired2fire.co.uk that i only wanted Ubuntu 22.04.2 installed on the machine and they did as requested. So the machine arrived yesterday 18/08/2023 and it worked out of the box i was literally over the moon lol.

When i powered up the machine Ubuntu 22.04.2 appeared, great! But unfortunately i am unable to update the machine, 
install or uninstall any unwanted software. I can't even add a new user because i am being asked for a password?
I have tried using "root", "admin", even "user" all without success.

Can anyone help me out here please?

---

### Post by MAFoElffen on 2023-08-19
Have you contacted "the people from wired2fire.co.uk" and asked them what the User Name and password they installed the OS as "is"? If they set it up traditionally, then these are set during installation. If they had used the OEM install option to install the OS, the the first boot of the OS goes directly to some screens to set user options, a User Name and password. The first User setup in the OS, is the Adminstrative User...

The following is assuming you are honest and are the owner. Physical Security a of a device is paramount. There is a way to reset what was setup by them... But the proper thig to do is to try to contact them first. You bought it from them. Access to what you bought from them should come with it, right?

At the Grub2 menu, choose option Advanced ad choose a kernel boot option with "Recovery". While at the Recovery menu, first choose network, then root. The first option will enable networking, and mount the filesystem in read/write mode. The second option will drop you to a root prompt, where you could list what user was setup, then reset the password for that user... Or alternately setup another user with elevated permissions.

Tell me how is goes, what happened with the vendor, and if you needs more instructions to do what I mentioned as options.

---

### Post by #&amp;thj^% on 2023-08-19
> **MAFoElffen said:**
> Have you contacted "the people from wired2fire.co.uk" and asked them what the User Name and password they installed the OS as "is"? If they set it up traditionally, then these are set during installation. If they had used the OEM install option to install the OS, the the first boot of the OS goes directly to some screens to set user options, a User Name and password. The first User setup in the OS, is the Adminstrative User...

The following is assuming you are honest and are the owner. Physical Security a of a device is paramount. There is a way to reset what was setup by them... But the proper thig to do is to try to contact them first. You bought it from them. Access to what you bought from them should come with it, right?

At the Grub2 menu, choose option Advanced ad choose a kernel boot option with "Recovery". While at the Recovery menu, first choose network, then root. The first option will enable networking, and mount the filesystem in read/write mode. The second option will drop you to a root prompt, where you could list what user was setup, then reset the password for that user... Or alternately setup another user with elevated permissions.

Tell me how is goes, what happened with the vendor, and if you needs more instructions to do what I mentioned as options.
+1
This still works as well and again providing your honest. ;)
[https://linuxconfig.org/ubuntu-20-04-reset-root-password](https://linuxconfig.org/ubuntu-20-04-reset-root-password)

---

### Post by billywyatt2 on 2023-08-20
By the time that the machine was delivered on Friday afternoon and i had it set to boot up it was round 5 o clock and when i emailed and telephoned the company i purchased the machine from [https://www.wired2fire.co.uk](https://www.wired2fire.co.uk) it was too late for a reply. I am the owner of the machine so there is no attempt of dishonesty on my part.

Big thanks for the replies and also the link for the root password but i think i'll wait until tomorrow when i hope the company concerned will get back to me with the required password.

I will of course let you know if the company response and the outcome of this problem

---

### Post by aljames2 on 2023-08-20
Glad to hear your system is booting & running nicely, but for this inconvenience..

Odd that a vendor would not include some basic instructions on getting started with your new system, and have the foresight to provide the username and password in separate communications, or give instructions on how to establish your own credentials.

---

### Post by ajgreeny on 2023-08-20
I note that the link shown by 1fallen seems to give you a system with an active root password rather than just a user password as is the norm when installing Ubuntu. It also says to use the shift key to get to a grub menu which is now usually incorrect as UEFI systems require repeated stabbing of the Esc key at power-on to show grub.

Another link that I know used to work well in your situation is shown at [https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword) and if followed this will reset the user password only, leaving the root account and password inactive.

---

### Post by #&amp;thj^% on 2023-08-20
> **billywyatt2 said:**
> By the time that the machine was delivered on Friday afternoon and i had it set to boot up it was round 5 o clock and when i emailed and telephoned the company i purchased the machine from [https://www.wired2fire.co.uk](https://www.wired2fire.co.uk) it was too late for a reply. I am the owner of the machine so there is no attempt of dishonesty on my part.

Big thanks for the replies and also the link for the root password but i think i'll wait until tomorrow when i hope the company concerned will get back to me with the required password.

I will of course let you know if the company response and the outcome of this problem

How do you login? Is it set to Auto-Login?

---

