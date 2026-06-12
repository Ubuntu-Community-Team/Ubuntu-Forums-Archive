---
title: "HPLIP Wireless Printing Does/Dosn't Work"
date: 2018-11-28
forum: General Help
---

### Post by Quarkrad on 2018-11-28
For some years (i.e. versions of ubuntu) I have had issues re wireless printing (always using hp printers).  After install/ setup all works fine and then the communication with the printer is lost.  I've tried many many solutions suggested on the web and had this issue with numerous versions of hplip but the problem has remained over the years. I've tried dynamic and static ip addresses for the printer, installed via the hplip s/w and cups, but I'm still here - unable to communicate.  At the moment I have assigned a static ip address for the printer and installed via hp setup/terminal.  Everything initially worked fine but now it has stopped - I cannot communicate with the printer.  Pinging tells me I'm unable to communicate with the host (192.168.1.207) so little wonder the printer or scanner s/w does not work.  Any advice appreciated.

---

### Post by kc1di on 2018-11-28
I'm not sure why your having the problem you are, But mine was solved with a static IP for the printer that was out of the range of normal DHCP numbers I set mine to 252 and it's worked well ever since.  I don't think it's a HPLIP problem but a networking problem your dealing with.  I also use hplip-gui to do the setups. 
Good Luck.

---

### Post by ajgreeny on 2018-11-28
**kc1di** has got the solution I think.

The easiest way to do this in my system is in the router setup, giving the printer a reserved IP address, though there will certainly be other ways.

Once you have given the printer a static IP, setup the printer wireless connection again (you may have to use the advanced button and manually give the printer IP) and it should then remain connected without a problem, even following router reboots.

---

