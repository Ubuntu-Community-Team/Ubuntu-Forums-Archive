---
title: "File Permissions Issue"
date: 2019-03-28
forum: General Help
---

### Post by sheenlim08 on 2019-03-28
Hello and Good Day,

I have a Xubuntu Installation.

My current user is.
```

sheenlim08@HPZ820-WKS:~$ whoami
sheenlim08
sheenlim08@HPZ820-WKS:~$ 

```

For me to not accidentally delete or move files from a folder structure I devided to issue the command
```

sheenlim08@HPZ820-WKS:~$ sudo chown -R sheenlim08:sheenlim08 /mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/
sheenlim08@HPZ820-WKS:~$ 

```
then
```

sheenlim08@HPZ820-WKS:~$ sudo chmod uog-wx -R "/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/"
sheenlim08@HPZ820-WKS:~$ 

```

However, I am no longer able to access the Tutorials folder from the File Explorer. I'm not sure, maybe because I used sudo when i owned and changed the permission?
I am not able to list the contents of that folder using ls in my own login context.
```

sheenlim08@HPZ820-WKS:~$ ls /mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/ -la
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/MCSA Windows 10': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/MCSE Microsoft Exchange 2016': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/CEH': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/Deploying Windows 8.1 and Windows Server 2012 R2 using MDT 2013': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/Writing in the Workplace Email, Memos, Reports, and Social Messaging': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/PowerShell': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/GNS3': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/CBT Nuggets VMware vSphere 6.5 VCP6.5-DCV': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/CBT Nuggets CompTIA Network+ (N10-007)': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/.': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/LPIC': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/Kali': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/MCSE Windows Server 2012': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/CCNA': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/Linux': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/Microsoft Network Monitoring': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/Mastering Layers in Photoshop CC': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/MCSA Windows Server 2016': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/Lynda - DevOps Fundamentals': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/..': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/Managing DHCP with PowerShell': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/MCSA Windows Server 2012 R2': Permission denied
ls: cannot access '/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/Nagios': Permission denied
total 0
d????????? ? ? ? ?            ?  .
d????????? ? ? ? ?            ?  ..
d????????? ? ? ? ?            ? 'CBT Nuggets CompTIA Network+ (N10-007)'
d????????? ? ? ? ?            ? 'CBT Nuggets VMware vSphere 6.5 VCP6.5-DCV'
d????????? ? ? ? ?            ?  CCNA
d????????? ? ? ? ?            ?  CEH
d????????? ? ? ? ?            ? 'Deploying Windows 8.1 and Windows Server 2012 R2 using MDT 2013'
d????????? ? ? ? ?            ?  GNS3
d????????? ? ? ? ?            ?  Kali
d????????? ? ? ? ?            ?  Linux
d????????? ? ? ? ?            ?  LPIC
d????????? ? ? ? ?            ? 'Lynda - DevOps Fundamentals'
d????????? ? ? ? ?            ? 'Managing DHCP with PowerShell'
d????????? ? ? ? ?            ? 'Mastering Layers in Photoshop CC'
d????????? ? ? ? ?            ? 'MCSA Windows 10'
d????????? ? ? ? ?            ? 'MCSA Windows Server 2012 R2'
d????????? ? ? ? ?            ? 'MCSA Windows Server 2016'
d????????? ? ? ? ?            ? 'MCSE Microsoft Exchange 2016'
d????????? ? ? ? ?            ? 'MCSE Windows Server 2012'
d????????? ? ? ? ?            ? 'Microsoft Network Monitoring'
d????????? ? ? ? ?            ?  Nagios
d????????? ? ? ? ?            ?  PowerShell
d????????? ? ? ? ?            ? 'Writing in the Workplace Email, Memos, Reports, and Social Messaging'
sheenlim08@HPZ820-WKS:~$

```

However, I am able to list the contents when I issue the sudo before the ls.
```

sheenlim08@HPZ820-WKS:~$ sudo ls /mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/ -la
total 144
dr--r--r-- 23 sheenlim08 sheenlim08  4096 Mar 29 08:50  .
drwx------ 12 sheenlim08 sheenlim08  4096 Mar  1 10:07  ..
dr--r--r--  2 sheenlim08 sheenlim08 57344 Mar 25 14:27 'CBT Nuggets CompTIA Network+ (N10-007)'
dr--r--r--  2 sheenlim08 sheenlim08  4096 Mar 29 09:01 'CBT Nuggets VMware vSphere 6.5 VCP6.5-DCV'
dr--r--r--  3 sheenlim08 sheenlim08  4096 Feb 26 09:03  CCNA
dr--r--r--  3 sheenlim08 sheenlim08  4096 Feb 26 08:38  CEH
dr--r--r--  8 sheenlim08 sheenlim08  4096 Feb 26 08:41 'Deploying Windows 8.1 and Windows Server 2012 R2 using MDT 2013'
dr--r--r--  2 sheenlim08 sheenlim08  4096 Feb 26 09:21  GNS3
dr--r--r--  5 sheenlim08 sheenlim08  4096 Mar 10 17:09  Kali
dr--r--r--  6 sheenlim08 sheenlim08  4096 Feb 26 11:12  Linux
dr--r--r--  4 sheenlim08 sheenlim08  4096 Feb 26 07:43  LPIC
dr--r--r--  2 sheenlim08 sheenlim08  4096 Feb 26 10:51 'Lynda - DevOps Fundamentals'
dr--r--r--  8 sheenlim08 sheenlim08  4096 Feb 26 08:41 'Managing DHCP with PowerShell'
dr--r--r--  6 sheenlim08 sheenlim08  4096 Feb 26 08:41 'Mastering Layers in Photoshop CC'
dr--r--r--  4 sheenlim08 sheenlim08  4096 Feb 26 09:33 'MCSA Windows 10'
dr--r--r--  2 sheenlim08 sheenlim08  4096 Feb 26 09:31 'MCSA Windows Server 2012 R2'
dr--r--r--  2 sheenlim08 sheenlim08  4096 Feb 26 09:31 'MCSA Windows Server 2016'
dr--r--r-- 10 sheenlim08 sheenlim08  4096 Feb 26 12:33 'MCSE Microsoft Exchange 2016'
dr--r--r--  4 sheenlim08 sheenlim08  4096 Feb 26 12:09 'MCSE Windows Server 2012'
dr--r--r-- 13 sheenlim08 sheenlim08  4096 Feb 26 08:43 'Microsoft Network Monitoring'
dr--r--r--  2 sheenlim08 sheenlim08  4096 Feb 26 10:35  Nagios
dr--r--r--  5 sheenlim08 sheenlim08  4096 Feb 26 07:18  PowerShell
dr--r--r-- 15 sheenlim08 sheenlim08  4096 Feb 26 08:43 'Writing in the Workplace Email, Memos, Reports, and Social Messaging'
sheenlim08@HPZ820-WKS:~$

```

Any Ideas? I didn't realize that using sudo to change the permission would require the accessing of these files with sudo. I don't want to run my desktop environment with sudo just to access these files.

---

### Post by sheenlim08 on 2019-03-28
Well, so it turns out i need an execute permission for me to list a content of a folder. I guess thats what the File Explorer does when it opens it.
Adding the Execute permission to the owner solved my issue. See below.


```

sheenlim08@HPZ820-WKS:~$ sudo chmod u+rx -R "/mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/"
sheenlim08@HPZ820-WKS:~$ ls /mnt/2addb157-3aab-42fd-b329-2e9d47fe148c/Tutorials/ -la
total 144
dr-xr--r-- 23 sheenlim08 sheenlim08  4096 Mar 29 08:50  .
drwx------ 12 sheenlim08 sheenlim08  4096 Mar  1 10:07  ..
dr-xr--r--  2 sheenlim08 sheenlim08 57344 Mar 25 14:27 'CBT Nuggets CompTIA Network+ (N10-007)'
dr-xr--r--  2 sheenlim08 sheenlim08  4096 Mar 29 09:01 'CBT Nuggets VMware vSphere 6.5 VCP6.5-DCV'
dr-xr--r--  3 sheenlim08 sheenlim08  4096 Feb 26 09:03  CCNA
dr-xr--r--  3 sheenlim08 sheenlim08  4096 Feb 26 08:38  CEH
dr-xr--r--  8 sheenlim08 sheenlim08  4096 Feb 26 08:41 'Deploying Windows 8.1 and Windows Server 2012 R2 using MDT 2013'
dr-xr--r--  2 sheenlim08 sheenlim08  4096 Feb 26 09:21  GNS3
dr-xr--r--  5 sheenlim08 sheenlim08  4096 Mar 10 17:09  Kali
dr-xr--r--  6 sheenlim08 sheenlim08  4096 Feb 26 11:12  Linux
dr-xr--r--  4 sheenlim08 sheenlim08  4096 Feb 26 07:43  LPIC
dr-xr--r--  2 sheenlim08 sheenlim08  4096 Feb 26 10:51 'Lynda - DevOps Fundamentals'
dr-xr--r--  8 sheenlim08 sheenlim08  4096 Feb 26 08:41 'Managing DHCP with PowerShell'
dr-xr--r--  6 sheenlim08 sheenlim08  4096 Feb 26 08:41 'Mastering Layers in Photoshop CC'
dr-xr--r--  4 sheenlim08 sheenlim08  4096 Feb 26 09:33 'MCSA Windows 10'
dr-xr--r--  2 sheenlim08 sheenlim08  4096 Feb 26 09:31 'MCSA Windows Server 2012 R2'
dr-xr--r--  2 sheenlim08 sheenlim08  4096 Feb 26 09:31 'MCSA Windows Server 2016'
dr-xr--r-- 10 sheenlim08 sheenlim08  4096 Feb 26 12:33 'MCSE Microsoft Exchange 2016'
dr-xr--r--  4 sheenlim08 sheenlim08  4096 Feb 26 12:09 'MCSE Windows Server 2012'
dr-xr--r-- 13 sheenlim08 sheenlim08  4096 Feb 26 08:43 'Microsoft Network Monitoring'
dr-xr--r--  2 sheenlim08 sheenlim08  4096 Feb 26 10:35  Nagios
dr-xr--r--  5 sheenlim08 sheenlim08  4096 Feb 26 07:18  PowerShell
dr-xr--r-- 15 sheenlim08 sheenlim08  4096 Feb 26 08:43 'Writing in the Workplace Email, Memos, Reports, and Social Messaging'
sheenlim08@HPZ820-WKS:~$

```

---

### Post by Skaperen on 2019-03-28
i am unsure of my understanding of what you want to accomplish.  it seems you want to have some files or folders be made so that *YOU* can read them normally but in order to change them or delete them, you cannot unless you use the **sudo** command.  the simple way is to create a 2nd user for this.  i call mine "*share*".  make everything be owned by (and in the group) "*share*".  then you have 2 ways to change the files: 1: use **sudo**, or 2: login as "*share*".

to change the ownership of existing files and folder:  [B]man chown
[/B]
you will need to user **sudo** when you really run chown.

---

