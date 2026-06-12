---
title: "what is the default root password for ubuntu-21.04-desktop OEM?"
date: 2021-07-16
forum: General Help
---

### Post by sohlinux on 2021-07-16
Hello,

I just installed ubuntu-21.04-desktop OEM then opened the terminal and typed sudo apt update. it asks for the root password but what is the root password?

The password is not ubuntu and its not blank and its not the password I created for the OEM user either. so what is it?

thanks

---

### Post by deadflowr on 2021-07-16
Does *password* work?
It did here:
[https://ubuntuforums.org/showthread.php?t=2456500&p=14047650#post14047650]("https://ubuntuforums.org/showthread.php?t=2456500&p=14047650#post14047650")

Again, though, I'm not sure if you tried that or not.

---

### Post by yancek on 2021-07-16
Did you follow the steps at the Ubuntu Documentation at the link below?

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

---

### Post by sohlinux on 2021-07-16
thanks for the info

yes I followed [https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
but the oem user does not have full admin as it asks for root pass to run apt

and no password is not the root password

just followed this [http://www.microhowto.info/howto/reset_a_forgotten_root_password_using_a_live_distribution.html](http://www.microhowto.info/howto/reset_a_forgotten_root_password_using_a_live_distribution.html)

and still the password I set does not work

looks like I will have to reinstall unless anyone has any ideas.

thanks

---

### Post by ajgreeny on 2021-07-16
I thought the OEM installer meant that at the first run of the OS it would ask the person to create a user and that user would have sudo/admin privileges by default, exactly as when using a normal installation.

Perhaps I'm wrong about that?

---

### Post by sohlinux on 2021-07-16
> **ajgreeny said:**
> I thought the OEM installer meant that at the first run of the OS it would ask the person to create a user and that user would have sudo/admin privileges by default, exactly as when using a normal installation.

Perhaps I'm wrong about that?

yes thats what I thought but it doesnt work

running apt update from user oem doesnt work

sudo apt update asks for root password which I dont know and did not set

oem password doesnt work for root

weird

---

### Post by ajgreeny on 2021-07-17
Apart from possibly trying recovery mode from the grub menu at boot, I am not sure what else to suggest.

That link for OEM installation suggests that the temporary OEM user can install software, but apparently not!

---

### Post by sohlinux on 2021-07-17
I reinstalled and now all is fine
thanks to everyone for the help.

---

### Post by ajgreeny on 2021-07-17
Just out of interest, did you do another OEM installation or a normal user installation; if a second OEM install, how did you manage to update this time?

Anyway, this is good news! 
Please mark as **SOLVED** from the **Thread Tools** menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by sohlinux on 2021-07-19
> **ajgreeny said:**
> Just out of interest, did you do another OEM installation or a normal user installation; if a second OEM install, how did you manage to update this time?

Anyway, this is good news! 
Please mark as **SOLVED** from the **Thread Tools** menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

I did a normal user install. marked as solved. thanks

---

### Post by ActionParsnip on 2021-07-19
Why are you using root? In Ubuntu you use your own password and account to authenticate sudo. Leave the root account alone.

---

