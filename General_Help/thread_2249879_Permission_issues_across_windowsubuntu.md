---
title: "Permission issues across windows/ubuntu"
date: 2014-10-25
forum: General Help
---

### Post by hopelessone on 2014-10-25
Hi,

In Ubuntu I right clicked folder_1 and selected >> properties >> local network share Clicked share folder & allow others to modify files n folders and guest acces. Jumped over to windows and logged in as ubuntu user/pass and can then access the folders/files

I have permission issues depending who creates the folder/saves the file, If I created the folder in windows I cant save anything in that folder_1, it says in Ubuntu: owner:nobody, group:nogroup on the folder_1

What can I do to get things right here?

Thanks

---

### Post by bab1 on 2014-10-27
> **hopelessone said:**
> Hi,

In Ubuntu I right clicked folder_1 and selected >> properties >> local network share Clicked share folder & allow others to modify files n folders and guest acces. Jumped over to windows and logged in as ubuntu user/pass and can then access the folders/files

I have permission issues depending who creates the folder/saves the file, If I created the folder in windows I cant save anything in that folder_1, it says in Ubuntu: owner:nobody, group:nogroup on the folder_1

What can I do to get things right here?

Thanks
When you added **guest access** all files created are owned by nobody, group:nogroup.  Since you are not nobody and not part of the nogroup those files are not accessible.  Un-tick the guest access box and reboot the computer.  You will now have to login as a known Samba user and you will have access to files that you create after that.

Guest access means that all users are not verified and are therefore considered nobody:nogroup.  You can modify that by setting the guest user attributes in the /etc/samba/smb.conf file using the terminal CLI and a text editor.  See the man pages for smb.conf ```
man smb.conf
```...from the terminal

---

### Post by hopelessone on 2015-08-04
with the "windows 10" upgrade this now works for me :)

---

