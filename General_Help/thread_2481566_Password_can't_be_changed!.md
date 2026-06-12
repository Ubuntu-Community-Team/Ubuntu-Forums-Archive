---
title: "Password can't be changed!"
date: 2022-12-03
forum: General Help
---

### Post by anon-rafiki on 2022-12-03
OS Name : Ubuntu 20.04.2 LTS
OS Type  : 64-bit
GNOME Version : 3.36.8
Windowing System : X11

Right, I decided to have Ubuntu on my old PC and it worked great. I got busy and laptop lied in a corner for a few months until I decided to work on it again.
I was asked to update Ubuntu which was fine. Problem is my USER PASSWORD won't authenticate.
I changed the ADMINISTRATOR PASSWORD and USER PASSWORD in the boot menu. I even changed my password for my online account. Yet nothing works.
I even tried it with the GRUB menu. Nothing seems to work to fix this password.

So before I throw this laptop in the trash and stick with Windows that works, is there anything I can do? Should I try to re-install the OS from start?
I am at a loss at how changing every conceivable account's password fails to change the password. Every time it takes me about an hour just to get the timing right to get to the boot menu, so I am very tired of this.

For the record. Every time I changed the password I got the prompt that it was successful and I am connected to the internet. This is the only OS on my laptop as I got rid of Windows as I couldn't quite figure out the boot stuff and always ended up booting up Windows which is why I got rid of it.
Any help would be appreciated.

---

### Post by tea for one on 2022-12-03
I can't quite understand where you want advice/help?
>  Problem is my USER PASSWORD won't authenticate
Is this your login to Ubuntu?
> I changed the ADMINISTRATOR PASSWORD and USER PASSWORD in the boot menu
UEFI settings password for disks or something else?
> I even tried it with the GRUB menu
Grub passwords are separate from UEFI and Ubuntu login.
> Every time I changed the password I got the prompt that it was successful and I am connected to the internet
Are you referring to your Router or ISP password?
> Every time it takes me about an hour just to get the timing right to get to the boot menu, so I am very tired of this
Is this the Grub menu or PC UEFI boot menu?
-------------------------------------------------------------------
As it is difficult to follow what has happened, I would suggest:-
Backup your Ubuntu personal data.
Remove all passwords in UEFI settings (if you can).
Reset UEFI settings to default.
Install Ubuntu from scratch.

---

### Post by yancek on 2022-12-03
When you install Ubuntu, you are required to create one user.  That user will have root (use sudo) permissions and will be the password you would use to log in.  There is no separate user or password for that user unless you created one.  Answering the questions in post 2 will go a long way toward getting help.  You will have a password for the primary user (for sudo) and additional passwords for other users you created.  You can also have a password for your BIOS which is not OS specific, a password for Grub and a separate passphrase for your network which is also separate and not OS specific.  Probably need to do some basic reading on how Ubuntu works if you plan to use it.  See the documentation at the links below.


[https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)

[https://help.ubuntu.com/](https://help.ubuntu.com/)

Changing the root (primary user) password is explained at the link below.

[https://itsfoss.com/change-password-ubuntu/](https://itsfoss.com/change-password-ubuntu/)

---

