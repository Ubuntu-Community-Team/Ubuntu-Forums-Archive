---
title: "Windows will not sync with Ubuntu 12.04 NTP"
date: 2013-01-04
forum: General Help
---

### Post by jdputnam19 on 2013-01-04
I am running Ubuntu 12.04 with NTP installed.  My Ubuntu laptop is able to sync with the NTP services on the Ubuntu Server however none of the Microsoft or network devices appear to be able to sync with it.  They all report server the server fails to respond. 

here is the config file minus the comment lines.. 

driftfile /var/lib/ntp/ntp.drift

filegen loopstats file loopstats type day enable 
filegen peerstats file peerstats type day enable 
filegen clockstats file clockstats type day enable 


server time.nrc.ca
server time.chu.nrc.ca
server 3.ubuntu.pool.ntp.org

server ntp.ubuntu.com

restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery

restrict 192.168.44.0 mask 255.255.255.0
restrict 192.168.55.0 mask 255.255.255.0
restrict 10.10.10.0 mask 255.255.255.0
restrict 10.10.11.0 mask 255.255.255.0

restrict 127.0.0.1

broadcast 192.168.44.255

#disable auth
#broadcastclient


I had also tried the following:

restrict 192.168.44.0 mask 255.255.255.0 notrap nomodify mstc
restrict 192.168.55.0 mask 255.255.255.0 notrap nomodify mstc
restrict 10.10.10.0 mask 255.255.255.0 notrap nomodify mstc
restrict 10.10.11.0 mask 255.255.255.0 notrap nomodify mstc

---

### Post by MSPdwalt on 2013-01-04
Windows doesn't always use traditional ntp, here's some references on the subject:

[http://technet.microsoft.com/en-us/library/cc773263(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc773263(WS.10).aspx)
[http://support.microsoft.com/kb/816042#method2](http://support.microsoft.com/kb/816042#method2)
[http://support.microsoft.com/kb/314054/en-us#EXTERNAL](http://support.microsoft.com/kb/314054/en-us#EXTERNAL)

---

### Post by jonobr on 2013-01-04
Excellent , great to read this 
I ried getting this to work a while ago >1year and couldn't.
Nice to know Im not crazy

---

### Post by jdputnam19 on 2013-01-04
So after much head banging and testing I got it to work.... 
biggest lesson ... patience...the Ubuntu server will not will not allow anything to sync with it until after at least a minute .. there is most likely a hold down timer that prevents it from doing so.  So needless to say when testing ... make your change wait a few minutes then test .. I used a Ubuntu 12.04 desktop to confirm the server was releasing time then I would test with windows.. 

Change the Windows PDC's to use internet as per Windows 2008 documentation.

---

