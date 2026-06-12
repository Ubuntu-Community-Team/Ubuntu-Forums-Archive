---
title: "abt shared folders samba"
date: 2006-12-27
forum: General Help
---

### Post by shashi123 on 2006-12-27
recently i installed xubuntu  6.06 it was really cool when i wanted to share a folder  on network 

i was immediately able to do it with shared folder utility  it immediately  installed samba services and i was through

after some time i installed xubuntu 6.10 instead of upgrading since there were some problems 

so i did a fresh installation but now if i want to share folders in network the shared folder utility says u need to either install nfs or smb for windows or linux sharing when i say install it dosent do it and again gives me same message again and again eventhough the fusesmb utility is also installed

what could be the problem?

can any one help me with this ur help would be highly appriciated

---

### Post by shashi123 on 2006-12-27
sorry i forgot to mention that samba service is already installed

---

### Post by dannyboy79 on 2006-12-27
i don't use 6.10, I use Dapper. I don't think samba changed from 6.06 to 6.10 but it's possible that when you click on the share folder within Xubuntu it doesn't know how to install all the packages needed. did you try to just install everything by hand first and then chose to share the folder? Also, you say that samab is installed, is it started? do a ps aux | grep smbd and ps aux | grep nmbd. both should return 2 results. 1 being the search you're doing with the grep and the other should be the actual service running! also, please post your /etc/samba/smb.conf file so we can make sure it has the same workgroup that your other computers have. it might be a lot of trouble, but you could install 6.06 again, do exactly what you did to get it working, then simply save a copy of your smb.conf onto a usb stick or floppy, then install 6.10 again, then install samba and smbfs and everything it wanted you to, then simply overwrite the default smb.conf with the one you saved. just a thought. samba for xubuntu on dapper is version 3.0.22-1ubuntu3.1
and all that it includes is:
 samba - LanManager-like file and printer server for Unix.
 samba-common - Samba common files used by both the server and the client.
 smbclient - LanManager-like simple client for Unix.
 swat - Samba Web Administration Tool
 samba-doc - Samba documentation.
 samba-doc-pdf - Samba documentation in PDF format.
 smbfs - Mount and umount commands for the smbfs (kernels 2.2.x and above).
 libpam-smbpass - pluggable authentication module for SMB/CIFS password database
 libsmbclient - Shared library that allows applications to talk to SMB/CIFS servers
 libsmbclient-dev - libsmbclient shared libraries
 winbind: Service to resolve user and group information from Windows NT servers
 python2.4-samba: Python bindings that allow access to various aspects of Samba
you can find this out by doing a sudo aptitude show samba from a command line.make sure it says. State: installed on the second line of the results.

---

### Post by shashi123 on 2006-12-30
thanx for ur reply 

but the real problem was i did not had the universe repository installed once i did that it was immedieatly able to do that

i want to have one more help if u can help me in this 

I am currently using windows as a server with cmailserver as a mailserver and ccprroxy as a internet connection sharing and all my client PC are xubuntu 6.10 its worikng great now i want to use linux server with appropriate packages insted of cmailserver and ccproxy which r the gui based packages available as i was unable to do it with firestarter is there anything else for internet connection sharing since i am noob in linux i dont know much abt dhcp files editing and all so if u can plz suggest me something gui i also tried webmin it was too confusing 

can u help me with this since the only windows PC i have is server and now i also want to replace that with ubuntu for server i want to use ubuntu 6.06 or 6.10 which i am currently downloading

---

### Post by dannyboy79 on 2007-01-01
i can't help because I don't have Ubuntu as a mailserver. I only set up sendmail so that it sends me mail from cron and tripwire etc etc. there's plenty of guides for setting up mail servers though. as far as sharing a internet connection can't help you either because I have a router which makes sharing my broadband connection simply, just connect wires and you're set! there's guides I am sure though, use either gogle or the search function within this forum

---

