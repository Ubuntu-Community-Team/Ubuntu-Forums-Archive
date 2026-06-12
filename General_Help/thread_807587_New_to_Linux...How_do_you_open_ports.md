---
title: "New to Linux...How do you open ports"
date: 2008-05-25
forum: General Help
---

### Post by DeanZ on 2008-05-25
I just made the migration from vista about 3 days ago and I am having trouble opening ports for the transmission bittorrent client...when i set it to use port 6881 which i have open on my router it shows it as "Port is Closed" is there anything else I have to do to open this?

And a second question...where are program files in Linux...I click into file system and then I have no clue what any of those files do and for the life of me i cannot find any of my program files.

Any help is greatly appreciated

---

### Post by damis648 on 2008-05-25
There is no firewall installed by defualt in Ubuntu. If you installed firestarter, you should open the ports there. About the program files, there is no such directory in linux. The folder with all executables, however if you are looking for all program executables they are found in /usr/bin but you will probably never need to visit this directory. If you need to run an application, it will most likely be in the main panel menu ("Applications") and if it is not, press Alt+F2 and type the name of the app.

---

### Post by molotov00 on 2008-05-25
> **damis648 said:**
> There is no firewall installed by defualt in Ubuntu. If you installed firestarter, you should open the ports there. About the program files, there is no such directory in linux. The folder with all executables, however if you are looking for all program executables they are found in /usr/bin but you will probably never need to visit this directory. If you need to run an application, it will most likely be in the main panel menu ("Applications") and if it is not, press Alt+F2 and type the name of the app.

I was under the impression iptables was installed but not configured to block any ports by default.

Either way, the ports are not blocked by default.

M

---

### Post by DeanZ on 2008-05-25
I haven't installed firestarter yet so i guess it just must be an error with the program...Thanks for the help

---

### Post by molotov00 on 2008-05-25
> **DeanZ said:**
> And a second question...where are program files in Linux...I click into file system and then I have no clue what any of those files do and for the life of me i cannot find any of my program files.

Any help is greatly appreciated

First question looks to me like a router issue because of my post above. With respect to your second question, Linux uses a vastly different directory structure. 

This should help you understand the structure and that there is no "Programme Files" as Windows has it:

[http://www.debianadmin.com/linux-directory-structure-overview.html](http://www.debianadmin.com/linux-directory-structure-overview.html)

M

---

### Post by damis648 on 2008-05-26
This was kind-of my point, i just wanted point out where the executables were if that was somehow important.

---

### Post by geo909 on 2008-05-26
> **molotov00 said:**
> First question looks to me like a router issue 

+1 to that. Having open the ports on my router, I never had a port-forwarding problem with any program

---

### Post by damis648 on 2008-05-26
Ah I have just found out *most* ports are blocked by default with iptables, including the ones you wanted unblocked. What you will have to do is install firestarter to unblock these.

note: this is wierd, because i use torrents all the time and i never had to open any ports....

---

### Post by chrisccoulson on 2008-05-26
The default configuration for iptables in Ubuntu is all ports wide-open. This is because there are no services listening by default:
```
chr1s@chris-desktop:~$ sudo iptables -L
[sudo] password for chr1s: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

If Transmission doesn't work, then it is almost certain to be a router issue (unless you've played with the default firewall configuration on your Ubuntu machine)

---

