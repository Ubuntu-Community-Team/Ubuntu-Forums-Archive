---
title: "/home not accessible after reinstall"
date: 2012-12-04
forum: General Help
---

### Post by hardeepr on 2012-12-04
Hi everyone, 

I'm in desperate need of some help getting my Ubuntu 12.04 system back up and running. I had upgraded to 12.10 and was unhappy, so a reinstall was in order. I used the 'something else' option to leave the filesystem unformatted for the install from a 12.04 cd, and made sure to point to my 3TB disk as /home. When everything came back up, I am unable to login with the credentials I gave during the install, and all of the other users are missing at the login window. After logging in as guest I find the /home is mounted but inaccessible with the message "You do not have the permissions necessary to view the contents of "home"". 

Please help! 

Sincerely,

Hardeep

---

### Post by oldfred on 2012-12-05
Welcome to the forums.

When you reinstalled did you use the same name & password? /home had the original name & passwork so any change would be seen as a different user which then would be permission issues.
       [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)

---

### Post by rnerwein on 2012-12-05
> **hardeepr said:**
> Hi everyone, 

I'm in desperate need of some help getting my Ubuntu 12.04 system back up and running. I had upgraded to 12.10 and was unhappy, so a reinstall was in order. I used the 'something else' option to leave the filesystem unformatted for the install from a 12.04 cd, and made sure to point to my 3TB disk as /home. When everything came back up, I am unable to login with the credentials I gave during the install, and all of the other users are missing at the login window. After logging in as guest I find the /home is mounted but inaccessible with the message "You do not have the permissions necessary to view the contents of "home"". 

Please help! 

Sincerely,

Hardeep
if you solve your problem with login to your home don't forget (you said you have more users on the system) that if you don't add them to the new system in the same order as the old they got differnt UID's. the username is only sonic and reek the id is importend.
if the UID's are different you can use the command: usermod (see man usermod)
cheers

---

