---
title: "can't change userid or password for internet connection"
date: 2020-12-20
forum: General Help
---

### Post by schmitta on 2020-12-20
It looks like someone got into my Ubuntu machine and changed my userid and password for my internet connection. When I try to change it back it immediately reverts back to the attacker's UID and PW. I imagine I will have to use an editor to change it where it is located. I need your expertise as to how to do so. Have you seen this type of incident before? Thank you for your help.

---

### Post by ajgreeny on 2020-12-20
I am not sure what you mean by your question; is it your username that has been changed?

You should be able to see the users on the machine by rebooting into Recovery Mode from the grub menu then running command ```
ls /home
``` and if you need to reset your user password there are ways to do that including the method shown at [https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword)

If you mean that the password used to connect to your router, which I assume is something you did when your ISP contract was set up, I am not sure where you go from here, other than contacting the ISP.

---

