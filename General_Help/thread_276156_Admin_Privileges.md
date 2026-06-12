---
title: "Admin Privileges"
date: 2006-10-12
forum: General Help
---

### Post by shallow on 2006-10-12
when i log onto Ubuntu now i seem to have lost some admin privileges.
the add software in applications is gone
and Administration in system a bunch of programs are gone

i have been using the same user name since the install of the software. how do i go about getting that stuff back please

---

### Post by Hmarroqu on 2006-10-12
System-administration-usersandgroups-user properties-user privelages...if u havent tried that already

---

### Post by PriceChild on 2006-10-12
Could you open up alacarte menu editor and see if the options have been hidden (checkbox unchecked)

---

### Post by shallow on 2006-10-12
to let you know i am a Noob at linux and ubuntu

Hmarroqu
i used to have that icon on the administration folder, but that is one of the shortcuts that is gone. 
that is what i am hoping to get back.

PriceChild
i dont know what a "alacarte menu editor" is or where to find it

---

### Post by shallow on 2006-10-12
in the Administrtion folder all i have is

Device Manager
Network tools
Printing
System Log
System Monitor

---

### Post by shallow on 2006-10-13
any one else have ideas how to get this stuff back?

---

### Post by jd65pl on 2006-10-13
I found [this]("http://www.psychocats.net/ubuntu/sudo") which is a guide on how you would do it.

---

### Post by PriceChild on 2006-10-13
Personally i don't think he's lost admin privelages.. just  icons.
> **shallow said:**
> i dont know what a "alacarte menu editor" is or where to find it

Alt+F2

Type in "alacarte"

Navigate to the System tab on the left and see if there are applications unchecked and so invisible.

---

### Post by jd65pl on 2006-10-13
You probably just want to get it done so....

[LIST=1]
[*]Reboot in recovery mode (selected from grub)
[*]Type the command
[*]```
addgroup {*Your user ID}* admin
```
[*]Reboot and you should be reinstated as a sudoer.[/LIST]

---

### Post by jd65pl on 2006-10-13
>  	Personally i don't think he's lost admin privelages.. just  icons.

The view the user is experiencing sounds a lot like one of someone who is not in the group "admin"

---

### Post by shallow on 2006-10-18
PriceChild i did the "alacarte" thing but some of the icons were checked off but still didnt show up. so i unchecked them then rechecked them. didnt work

so i :

   1. Reboot in recovery mode (selected from grub)
   2. Type the command
   3.
      Code:

      addgroup {Your user ID} admin

   4. Reboot and you should be reinstated as a sudoer.

like jd65pl said that worked

i have a silly question what is a "sudoer"?
and thank you for your help

---

### Post by aysiu on 2006-10-18
a sudoer is an administrator who can preface commands with *sudo* in order to make system-wide changes.

Users who do not belong to the admin group cannot make system-wide changes, no matter what they preface commands with.

---

