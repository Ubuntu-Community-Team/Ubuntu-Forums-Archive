---
title: "Samba printing problem (Gutsy)"
date: 2007-10-23
forum: General Help
---

### Post by 1d2n on 2007-10-23
I am unable to see printers shared on xp systems with gutsy. they worked fine on fiesty and on windows systems. I can see a shared directory on that system but not the printer.

smbclient can see the printer but not gnome or kde here is the output from smbclient -L

Domain=[PRINT] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        faxes           Disk
        printer         Printer   printer
Domain=[PRINT] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

thank you

---

### Post by 1d2n on 2007-10-23
I set up another gutsy system and I am having the same problem on both. I set up another printer on a different windows machine, shared it and can not access it from either gutsy system, but it works fine from feisty and windows. Is this a bug? should I submit a bug report?

thanks

---

### Post by 1d2n on 2007-10-24
anyone?

---

### Post by tubasoldier on 2007-10-25
I am having the same issue with samba all together. I figure it is an issue with the newer version of samba. Basically, as far as I can tell, samba is just plain broken in Gutsy. 

Search the forums and there are all sorts of threads on the matter but no real answers. There is even one thread where a guy is more worried about the internet connection than he is with samba. 

I have used different programs to rewrite my smb.conf. Swat made a nice simple config file, gsambad made quite the intense smb.conf file while at the same time completely made it so samba would not start. I just need a simple way to share files between computers. SSH is fine for me but the wife would complain a lot if she had to use the terminal for file transfers. 

I personally think its amazing that there are such blaring bugs in Gutsy that were not taken care of before the release. This should not have gone out the door with samba in such bad shape.

---

### Post by tubasoldier on 2007-10-25
After searching, and trying this How-To and that How-To and that setup procedure and that setup program, I've pretty much figured it out. 

Here is my smb.conf file. It works for me.
> 
[global]

workgroup = PUT_YOUR_WORKGROUP_NAME_HERE
netbios name = PUT_YOUR_COMPUTERS_NAME_HERE
security = SHARE
auth methods = guest
domain master = No
wins support = Yes


[print$]
path = /var/lib/samba/printers
browseable = yes
guest ok = yes
read only = yes
write list = root
create mask = 0664
directory mask = 0775


[printers]
path = /tmp
printable = yes
guest ok = yes
browseable = no


[SHARE1]
comment = YOUR FIRST SHARED DIRECTORY
path = /PATH/TO/SHARE/IN/LOWERCASE/LETTERS
read only = No
guest ok = Yes


I put the things needed changing in all uppercase letters. Change those few things for your needs and you will have a simple samba network to share your printers and files.

---

### Post by willz06jw on 2007-10-29
This worked except for one problem:

It found PDF (I guess this is the PDF writer) but it won't show my HP printer that works in Ubuntu. Do I need to add something somewhere?

Thanks for your help ... I know that I couldn't have figured out that smb.conf file.

Will

---

### Post by bastubis on 2008-01-04
I use Ubuntu at home & work - having problems with samba print shares on both networks. 

At home:

Ubuntu standalone peer server which uses samba (flatmate/visitors with xp laptops need to access it). The printer works fine on the gutsy server but I can't connect to it with my gutsy laptop using samba. GNOME printer configuration GUI can see the printer and adds it but I can't use it, access is denied. Tried enabling @lpadmin in smb.conf and generally tweaking samba but nothing helps. 

this is the printer bit of my smb.conf (worked fine on feisty and samba is otherwise working fine, I can connect to smb shares):

   load printers = yes
;   printing = bsd
;   printcap name = /etc/printcap
   printing = cups
   printcap name = cups
;   printer admin = @lpadmin

I've always used samba so have no idea how to use cups - cruised some forums and tried this:
ipp://192.168.1.x:631/printers/Deskjet_3740
and this:
[http://192.168.1.x:631/printers/Deskjet_3740](http://192.168.1.x:631/printers/Deskjet_3740)

then I tried to install it as LPD:
lpd://192.168.1.x/Deskjet_3740

None worked - I get 'no queues available'. Probably I need to install a load of stuff but, frankly, I wanna use samba, I've always used samba - pleeeezzzzeees let me use samba! 

At work: 
I use gutsy on a laptop and everyone else uses Windows so I use samba to connect to the network. I can connect to one HP Laserjet network printer by mapping a port to its IP, The other HP Laserjet is on a Netgear samba print server. I can't connect to the samba printer. I can see the printer on the network but GNOME printer config can't see it at all (unlike home where at least GNOME can see it). Again, any which way I've tried to connect to it fails. 

Several days later, I've exhausted my small store of knowledge and can't find any kind of solution that actually works by googling. I really need to be able to print!

---

### Post by bastubis on 2008-01-10
Finally fixed it - commented out this line in smb.conf
invalid users = root

Suddenly I can connect to the printer and also to folders which aren't set as shared which I couldn't access before. Don't know if this is a good idea security-wise but I can print! 

:popcorn:

---

