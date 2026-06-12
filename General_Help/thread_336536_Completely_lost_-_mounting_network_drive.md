---
title: "Completely lost - mounting network drive"
date: 2007-01-11
forum: General Help
---

### Post by puppy on 2007-01-11
Hi everyone, I have a Buffalo network drive which is connected ny ethernet directly to my router (which connects out to the outside world). The router assigns IPs to the connected devices by DHCP, and both my PC and the network drive (which I have been able to access from a windows machine) also gets its IP assigned by DHCP.

I can access the net with no problems using DHCP with my PC connecting wirelessly to the router , but how on earth can I access the network drive?? What do I need to install etc. etc? Sorry I haven't a clue about this so please be very basic in your reply or at least please point me in the right direction (getting to other devices on the network under linux is completely new to me)

Many thanks

OK Edit

After doing some searching I have found the following command (remember the IP address of the network drive is NOT static so this may change) - so I can *see* it - how do I connect to it??

pete@Auberdine:~$ smbclient -L 192.168.2.3
Password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 2.2.8a-ja-1.1]

        Sharename       Type      Comment
        ---------       ----      -------
        lp              Printer   Network Printer for Windows
        info            Disk      LinkStation information
        pete            Disk      share
        darren          Disk      share
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 2.2.8a-ja-1.1]

        Server               Comment
        ---------            -------
        IRONFORGE            LinkStation

        Workgroup            Master
        ---------            -------
        WORKGROUP            IRONFORGE

---

