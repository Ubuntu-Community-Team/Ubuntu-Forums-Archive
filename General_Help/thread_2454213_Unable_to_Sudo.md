---
title: "Unable to Sudo"
date: 2020-11-24
forum: General Help
---

### Post by ulrichkenneth on 2020-11-24
Hi All, below should be the info you need for my Linux Version

```
usertest1@TestServer:~$ cat /etc/os-release
NAME="Ubuntu"
VERSION="20.04.1 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.1 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal

```

```
usertest1@TestServer:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:        20.04
Codename:       focal

```

```
usertest1@TestServer:~$ hostnamectl
   Static hostname: TestServer
         Icon name: computer-vm
           Chassis: vm
        Machine ID: 70989dc536db446196bb97820909964b
           Boot ID: c343f8ea344d452886718d0f898a67f8
    Virtualization: kvm
  Operating System: Ubuntu 20.04.1 LTS
            Kernel: Linux 5.4.0-51-generic
      Architecture: x86-64
```

```
usertest1@TestServer:~$ uname -r
5.4.0-51-generic

```
I've been trying to see how to add my user to the Sudo group for a while now. 
I know in verision 14 and lower (maybe 16 and lower), that I would just add my user to the "wheel" group and I have sudo permissions.
That doesn't seem to be the case anymore since wheel is no longer a group.

```
[sudo] password for usertest1:
usertest1is not in the sudoers file.  This incident will be reported.
usertest1@TestServer:~$


```
Does anyone know how I can add my user to the sudo group now?

Here is what I've tried through other forums, and help subjects.

```
adduser usertest1 sudo
username -aG sudo,adm usertest1
usermod -aG sudo,adm usertest1
/sbin/usermod -aG sudo,adm usertest1
adduser hyrazues sudo
adduser hyrazues1 sudo
adduser usertest11 sudo
useradd -m usertest11 sudo
adduser usertest11 sudo
usermod -aG sudo usertest1
usermod -G sudo usertest1
```

---

### Post by ActionParsnip on 2020-11-24
What is the output of:
```

groups usertest1

```
Thanks

---

### Post by ActionParsnip on 2020-11-24
Have you modified your sudoers file manually too? You most likely won't need to. To add a user to the sudo group, run:
```

sudo usermod -a -G sudo usertest1

```
Log off, then log back in again (just like you would in Windows) and off you go.

---

### Post by ulrichkenneth on 2020-11-24
> **ActionParsnip said:**
> Have you modified your sudoers file manually too? You most likely won't need to. To add a user to the sudo group, run:
```

sudo usermod -a -G sudo usertest1

```
Log off, then log back in again (just like you would in Windows) and off you go.

That actually worked.
Why did that work but the command " usermod -aG sudo usertest1" did not?
The only difference is that I put the flags together.

---

### Post by ulrichkenneth on 2020-11-24
> **ActionParsnip said:**
> What is the output of:
```

groups usertest1

```
Thanks

I thought my post was sent.

usertest1 : usertest1 sudo

---

### Post by TheFu on 2020-11-24
If your userid isn't in the sudo group already, you'll need to use a different account that is to make any group changes.

Or you'll need to hack into the system to make the change. If you have to ask how to do that, well ...

---

