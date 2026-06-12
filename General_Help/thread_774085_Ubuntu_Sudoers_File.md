---
title: "Ubuntu Sudoers File"
date: 2008-04-29
forum: General Help
---

### Post by 200mg on 2008-04-29
I was interested in seeing how the sudoers file was laid out so i checked /etc/sudoers

I am confused as to why my user name is not in the file.  The only user in the sudoers file is root.  Where is my username that I setup during install, the one I use all the time that has sudo permissions?

OS: Hardy Heron

---

### Post by kavon89 on 2008-04-29
> **200mg said:**
> I was interested in seeing how the sudoers file was laid out so i checked /etc/sudoers

I am confused as to why my user name is not in the file.  The only user in the sudoers file is root.  Where is my username that I setup during install, the one I use all the time that has sudo permissions?

OS: Hardy Heron

Well the user account you login with doesn't have full admintrative rights without entering any passwords unless you did somthing special.

Being logged in as root or on an account with root privileges is not reccomended, it poses security risks etc.

---

### Post by mali2297 on 2008-04-29
The sudoers file contains a line that gives privileges to **admin**, does it not? 

If you run **groups** in the terminal, then you will see that you are a member of this admin group. 

For more information, see
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by 200mg on 2008-04-29
> **mali2297 said:**
> The sudoers file contains a line that gives privileges to **admin**, does it not? 

If you run **groups** in the terminal, then you will see that you are a member of this admin group. 

For more information, see
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

thanks mali, thats what i was looking for

---

