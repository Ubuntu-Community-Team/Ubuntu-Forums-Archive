---
title: "Kubuntu 7.10 Konsole unable to type password into sudo"
date: 2008-01-10
forum: General Help
---

### Post by Mr_Roach on 2008-01-10
Having just installed Kubuntu 7.10 32 bit, I am unable to input the root password into sudo while using Konsole.  
Eg "sudo [command]" returns 

"sudo: password for edward:"

When I attempt to type the password, nothing appears.  The only responsive key is the enter key (the use of which returns a failed password attempt).

This error has persisted after a reinstall, and was not present in Kubuntu 7.04 when it was installed on the same computer.

Help!!!

---

### Post by wieman01 on 2008-01-10
Could you post a screenshot? I am on Kubuntu and have not heard of this yet...

---

### Post by Mr_Roach on 2008-01-10
Sure, I've attached a screenshot.  I took it after entering the command and attempting to enter my password as normal.

---

### Post by samwyse on 2008-01-10
It doesn't display anything when you type. Just type your password correctly and hit enter.

---

### Post by wieman01 on 2008-01-10
I think your user does not have admin rights... that's the issue. So 'sudo' is deactivated. Read this to enable it:

[https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29]("https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29")

_**EDIT:**_

This one rather: [https://help.ubuntu.com/community/Sudoers?highlight=%28sudo%29]("https://help.ubuntu.com/community/Sudoers?highlight=%28sudo%29")

You need to run:
> su root
> visudo

---

### Post by mcduck on 2008-01-10
> **samwyse said:**
> It doesn't display anything when you type. Just type your password correctly and hit enter.

This is correct. When you are typing your password in command-line nothing is printed on screen. Just don't let it confuse you, type your password and hit enter.

---

### Post by Mr_Roach on 2008-01-10
Ah, thanks guys.  That was the problem.

---

