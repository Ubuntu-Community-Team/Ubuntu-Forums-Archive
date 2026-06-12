---
title: "Samba Problem"
date: 2008-05-08
forum: General Help
---

### Post by wiggst3r on 2008-05-08
Hi

I've setup samba in order to share a folder on our file server.

I have made sure the folder I'm sharing has been given the permissions to be shared and I've also made sure that it's in the same workgroup as the windows machines.

I edited the smb.conf, but I'm not sure If I have got everything correct.

When I go to places -> network ->nameofgroup

There is only the file-server listed.

When i logon to a windows machine, there is also nothing.

Could the fact that the mac users (i.e me ) are running on an IP range of 192.168.100.100 and the windows users running 192.168.100.1 be a reason?

Just seems strange that I cannot see the file server in windows explorer/my network places



Thanks

---

### Post by AlbertTatlocksCap on 2008-05-08
Hi 

Have a look at this - it is a good and straightforward guide and tells you what to edit in smb.conf

Hope it helps

OOP sorry - here is the link

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

---

### Post by wiggst3r on 2008-05-08
\well I've managed to connect via my mac (finder -> go -> connect to server)

But I cannot see the workgroup in windows explorer/my network places etc

Any ideas how I could connect using a windows machine, considering i've managed to do it via a mac?

---

### Post by AlbertTatlocksCap on 2008-05-08
Have you got file and print sharing enabled on your Windows PC?

I presume that is in the same workgroup?

---

### Post by wiggst3r on 2008-05-08
File and print sharing are both on and the workgroup is named ABA

Every computer is given the workgroup ABA.

I don't understand.

I have a windows PC next to the linux server. The linux server configuration is as follows
IP - 192.168.100.124
Gateway - 192.168.100.100
DNS - 192.168.100.100

Windows PC(s)
IP - 192.168.100.xx
Gateway - 192.168.100.1
DNS - 192.168.100.1

The reason we have 2 DNS is that, the linux and mac machines are running off one ISP and the windows machines are running off another ISP. But all are networked via a router.

I changed the windows Pc next to the linux server to have a DNS and gateway of 192.168.100.100 and everything worked.

But when I change any other windows PC in the room next door, I can't see the linux server.

---

### Post by SonicSteve on 2008-05-08
> **wiggst3r said:**
> Hi

Could the fact that the mac users (i.e me ) are running on an IP range of 192.168.100.100 and the windows users running 192.168.100.1 be a reason?

Just seems strange that I cannot see the file server in windows explorer/my network places

Thanks

Bye the way your range is fine. The range you're using is from 192.168.100.1-255 any IP in that 100.1-255 range will be on the same subnet. 
IP addressing is assigned by four sets of 3 digits. Each of them can range from 1-255. None of the four numbers can less than 1 or more than 255.  There is one address that is reservered. 127.0.0.1 it's assigned to each computer and is called the loopback address.

For example

192.168.0.1-255 would be a different network
192.168.1.1-255 ditto
yours is 192.168.100.1-255 as long as the first 3 octets (ie.sets of numbers) are the same you'll be on the same network, as long as your subnet mask is 255.255.255.0  I wouldn't recommend you stray from this unless you know what your doing. The easiest thing to do is let your router act as a DHCP server (assigns the ip address automatically). If you don't have a router manually setting the IP is ok too it's just a bit more tricky if you're new to IP addressing.

---

### Post by wiggst3r on 2008-05-08
I'm aware of the IP addresses.

We are using static IP addresses throughout for simplicity and to avoid IP address conflicts, amongst other reasons.

I am just really confused as to why I cannot connect via a windows machine and only a mac!

It makes no sense.

Would posting my smb.conf help? It might show whether or not the configuration is correct.
It must be correct in some sense though, otherwise it wouldn't let me connect using a mac.

Thanks

---

### Post by SonicSteve on 2008-05-08
> **wiggst3r said:**
> I'm aware of the IP addresses.

We are using static IP addresses throughout for simplicity and to avoid IP address conflicts, amongst other reasons.

I am just really confused as to why I cannot connect via a windows machine and only a mac!

It makes no sense.

Would posting my smb.conf help? It might show whether or not the configuration is correct.
It must be correct in some sense though, otherwise it wouldn't let me connect using a mac.

Thanks

Posting the smb.conf file wouldn't hurt. I think there is a bug in Samba or Nautilus causing this right now. I have similar strange issues with networking that I never had in previous version of Ubuntu. 

I can browse the network and see the windows computers in my schools domain. But if I double click to choose a computer, the window that should show all the shares is empty. However If I add the name of the share to the path in the Nautilus explorer the shares show up. It seems that the root shares for each computer are invisible. I wonder if I tried Dolphin instead of Nautilus if it would make any difference. I'm going to try that tomorrow.

---

### Post by Iowan on 2008-05-08
Verify that the Windows computer has the "Client for Microsoft Networks" option enabled under "Local Area Connection Properties".

---

