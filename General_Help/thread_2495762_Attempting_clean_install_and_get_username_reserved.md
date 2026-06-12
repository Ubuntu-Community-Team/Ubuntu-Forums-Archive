---
title: "Attempting clean install and get username reserved?"
date: 2024-02-29
forum: General Help
---

### Post by mtbdrew on 2024-02-29
Trying to do a clean install off USB thumbdrive. This will be a master backend for mythtv but when I try to assign the username as mythtv during install I get this message:-

The username you entered (mythtv) is reserved for use by the system. Please select a different one.

Is this an issue left over from the old Mythbuntu days. This problem occur on any Linux OS based on Ubuntu. 

Regards
Andrew

---

### Post by grahammechanical on 2024-02-29
I do not know. I think that the live system has a user name of ubuntu and a password of ubuntu or in your case mythtv and mythtv. 

Have your tried using capital letters? Or, adding some numbers?

Regards.

---

### Post by ian-weisser on 2024-02-29
No, it's not a leftover.

The packages wisely don't want myth to run as root. So installing myth creates a user. That user owns the database and content files.

In other words, you don't need to create the mythuser. It's already created for you.

---

### Post by mtbdrew on 2024-03-05
So when I'm to a brand new clean install from thumbdrive, I have to install under a different username instead of the one I want to use? How did the old Mythtbuntu installs get around this because they installed under the "mythtv" username. 

Secondly, how do I log into the mythtv user account once mythtv is installed? And can I set it up as the default auto login for the backend?

---

### Post by Tadaen_Sylvermane on 2024-03-05
You shouldn't need to create the myth user. The package will do it for you. You can su to that user if you need to but little to no reason for it I can think of.

---

### Post by mtbdrew on 2024-03-05
I am wanting to have the system boot and log straight into the mythtv user in the same way Mythbuntu editions use to do this. The reason being that with the user being mythtv all file access for recordings and scheduling are natively set for permissions. Scheduling is now done through json scripts that have to run as the mythtv user or they will not work. Also recordings are saved to NAS which then requires multiple permissions setup in the NAS and locally so they can be removed by both the mythtv user and the installed user, on Synology NAS this can be very complicated to get working. Basically it would be a heck of a lot easier if I could just install the OS as the user mythtv.

---

### Post by Tadaen_Sylvermane on 2024-03-07
The myth user is set to nologin if I recall. If you give it a password and change shell to bash it should do what you want

Is likely all mythbuntu does.

---

### Post by coffeecat on 2024-03-09
Support, not chat. *Thread moved to **General Help**.*

---

