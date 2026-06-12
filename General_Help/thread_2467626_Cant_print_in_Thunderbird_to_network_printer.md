---
title: "Cant print in Thunderbird to network printer"
date: 2021-10-02
forum: General Help
---

### Post by Cadryc on 2021-10-02
I have a Brother printer connected with usb cable to aRaspberry Pi running standard Rasbian and shared to my local home network.

From my Ubuntu computer I can print from writer, I can print a test page, it seems to work just fine.

But I opened up an email in Thunderbird and clicked print. A dialog with a progress bar appeared, quickly going to 100% and vanishing. But nothing is printed. And the printer que is empty.

Ubuntu 20.04 up to date

In Thunderbird print format my printer is listed twice, for some reason.

I deleted the printer in ubuntu and readded it.
The printer is set as standard
In Thunderbird config editor I reset print_printer
I renamed addons.json in my profile folder

Suggestions please

---

### Post by mIk3_08 on 2021-10-02
> **Cadryc said:**
> I have a Brother printer connected with usb cable to aRaspberry Pi running standard Rasbian and shared to my local home network.
From my Ubuntu computer I can print from writer, I can print a test page, it seems to work just fine.


I also have a DCP Brother printer with scanner and it works smoothly in  my Linux Ubuntu Operating System and also the scanner works with xsane  image scanning program an 
open source program application. I just  want to share my experience to you with my Brother printer/scanner device so  that you will know that brother printer will work smoothly on Linux  Ubuntu Operating System.
There's nothing to worry about it.

Just  want to ask, have you install all the Linux driver package of your  brother and the driver must come from the brother website?

> **Cadryc said:**
> 
But I opened up an email in Thunderbird and clicked print. A dialog with  a progress bar appeared, quickly going to 100% and vanishing. But  nothing is printed. And the printer que is empty.

And I also try to print my email coming from Thunderbird and it print successfully. 
Did you try to do a print preview of the document before printing?

> **Cadryc said:**
> 
In Thunderbird print format my printer is listed twice, for some reason.

Have you selected the right printer driver during your attempt to print a document coming from your Thunderbird?

> **Cadryc said:**
> 
In Thunderbird config editor I reset print_printer
I renamed addons.json in my profile folder
Suggestions please
I don't know what you have done to the script but I haven't touch any important script in my Thunderbird even though if its just an add-on.


> **Cadryc said:**
> 
Thunderbird
My Thunderbird version 78.13.0 (64-bit) How about yours?

---

### Post by Cadryc on 2021-10-03
Thank you mlk3_8 for your response.

The printer is plugged in to a Raspberry Pi 3 with usb. The Brother DCP 7055 was not automatically detected in Rasbian, and after a short search i found [this](https://medium.com/@alexanderbelov/how-to-use-your-brother-printer-with-cups-on-raspberry-pi-5b712cc2b4e6), installed **brlaser** , rebooted and there the printer was, a test page worked fine. I clicked share, went to Ubuntu and the printer was immediately visible. I made it standard printer and printed a test page. If I now click search for drivers the search comes up empty.

Yes I did try a print preview. The preview looks fine

I am translating this from Swedish so the wording might not be exactly what it says in Thunderbird. I click menu, then print, there are 3 options, one of which is Print format, there I can choose paper size and different printers. Thou I assume this is only setting the format for the printer, not choosing the printer for prints per se. I find no other place to choose printer in Thunderbird. Two identical printers are showing here. But settings there are only one printer. Printing from ie LibreOffice Calc brings up another dialog where I can choose to print to file or chose a printer and here is only on showing.

Renaming addons.json was a thing I found when googling. But instead of deleting the file I renamed it (to addons.json.bkp) so I could restore it if some problem should arise. The pont was to generate a new file if maybe the old was corrupt. But there is no additional addons installed other than might be in the standard install.

My Thunderbird is 78.14.0 (64bit) and Ubuntu 20.04 with the latest stable updates.


I tried the Thunderbird 91 candidate in the Ubuntu Software center snap package. Same thing.
(The snap package doesn't have fully translated, interface to Swedish, so I use Thunderbird from the repos)

---

### Post by mIk3_08 on 2021-10-03
> **Cadryc said:**
> Thank you mlk3_8 for your response.
The printer is plugged in to a Raspberry Pi 3 with usb. The Brother DCP 7055 was not automatically detected in Rasbian, and after a short search i found [this]("https://medium.com/@alexanderbelov/how-to-use-your-brother-printer-with-cups-on-raspberry-pi-5b712cc2b4e6"), installed **brlaser** , rebooted and there the printer was, a test page worked fine. I clicked share, went to Ubuntu and the printer was immediately visible. I made it standard printer and printed a test page. If I now click search for drivers the search comes up empty.


My printer is installed directly to my local router. But I still installed a brother printer driver downloaded from brother website. And also I installed a scan key tool from deb package for the scanner of my printer/scanner in my Linux Ubuntu Operating System.

> **Cadryc said:**
> I am translating this from Swedish so the wording might not be exactly  what it says in Thunderbird. I click menu, then print, there are 3  options, one of which is Print format, there I can choose paper size and  different printers. Thou I assume this is only setting the format for  the printer, not choosing the printer for prints per se. I find no other  place to choose printer in Thunderbird. Two identical printers are  showing here. But settings there are only one printer. Printing from ie  LibreOffice Calc brings up another dialog where I can choose to print to  file or chose a printer and here is only on showing.


You should have some option of printer when you click the print under the "Thunderbird File Menu print" before it prints even using any other application when you are going to do printing.
In the print option you will see under Print window a "General" tab below then your printer name, location and status and you will also see that range and number of copies of the pages you want to print.  
In your printer settings properties:  Below is the complete field printer properties when your printer driver is installed completely and successful.

Description:
Location:
Device URI:
Make and Model:

> **Cadryc said:**
> 
Renaming addons.json was a thing I found when googling. But instead of  deleting the file I renamed it (to addons.json.bkp) so I could restore  it if some problem should arise. The pont was to generate a new file if  maybe the old was corrupt. But there is no additional addons installed  other than might be in the standard install.

There is nothing wrong googling your printing problem just be sure that you knew already what you do. You knew already how the script flow so that it will not become more worst when doing some changes.
> **Cadryc said:**
> My Thunderbird is 78.14.0 (64bit) and Ubuntu 20.04 with the latest stable updates.
You have a latest Thunderbird.

---

### Post by Cadryc on 2021-10-03
[QUOTE=mIk3_08;14061503]You should have some option of printer when you click the print under the "Thunderbird File Menu print" before it prints even using any other application when you are going to do printing.
In the print option you will see under Print window a "General" tab below then your printer name, location and status and you will also see that range and number of copies of the pages you want to print.  
In your printer settings properties:  Below is the complete field printer properties when your printer driver is installed completely and successful.

Description:
Location:
Device URI:
Make and Model:

/QUOTE]

The printer is visible in Ubuntus system settings and Libreoffice, but not in Thunderbird.

I have just followed these troubleshooting steps
[https://wiki.ubuntu.com/DebuggingPrintingProblems#Network_printer](https://wiki.ubuntu.com/DebuggingPrintingProblems#Network_printer)

I get no output from ***$ /usr/lib/cups/backend/snmp***, not even if I add the IP to the raspberry pi.

This is my output from ***sudo /usr/lib/cups/backend/dnssd ***
```
DEBUG: Querying "Brother\032DCP-7055\032\064\032hallonpaj._ipp._tcp.local"...
DEBUG: Querying "Brother\032DCP-7055\032\064\032hallonpaj._ipps._tcp.local"...
DEBUG: Querying "Brother\032DCP-7055\032\064\032hallonpaj._printer._tcp.local"...
DEBUG: sent=0, count=3
DEBUG2: query_callback(browser=0x564634539ec0, interfaceIndex=2, protocol=1, event=0, fullName="Brother\032DCP-7055\032\064\032hallonpaj._ipp._tcp.local", rrclass=1, rrtype=16, rdata=0x56463453b9d0, rdlen=414, flags=5, context=0x564634539180)
DEBUG2: query_callback: "txtvers=1".
DEBUG2: query_callback: "qtotal=1".
DEBUG2: query_callback: "rp=printers/Brother-DCP-7055".
DEBUG2: query_callback: "ty=Brother DCP-7055, using brlaser v4".
DEBUG2: query_callback: "adminurl=https://hallonpaj.local.:631/printers/Brother-DCP-7055".
DEBUG2: query_callback: "note=hallonpaj".
DEBUG2: query_callback: "priority=0".
DEBUG2: query_callback: "product=(DCP-7055)".
DEBUG2: query_callback: "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf".
DEBUG2: query_callback: "URF=DM3".
DEBUG2: query_callback: "UUID=5b5ec5ce-346e-3d33-5833-b9b77a10683d".
DEBUG2: query_callback: "TLS=1.2".
DEBUG2: query_callback: "Copies=T".
DEBUG2: query_callback: "printer-state=3".
DEBUG2: query_callback: "printer-type=0x1046".
DEBUG2: query_callback(browser=0x564634539ec0, interfaceIndex=2, protocol=0, event=0, fullName="Brother\032DCP-7055\032\064\032hallonpaj._ipp._tcp.local", rrclass=1, rrtype=16, rdata=0x56463453bd40, rdlen=414, flags=5, context=0x564634539180)
DEBUG2: query_callback: "txtvers=1".
DEBUG2: query_callback: "qtotal=1".
DEBUG2: query_callback: "rp=printers/Brother-DCP-7055".
DEBUG2: query_callback: "ty=Brother DCP-7055, using brlaser v4".
DEBUG2: query_callback: "adminurl=https://hallonpaj.local.:631/printers/Brother-DCP-7055".
DEBUG2: query_callback: "note=hallonpaj".
DEBUG2: query_callback: "priority=0".
DEBUG2: query_callback: "product=(DCP-7055)".
DEBUG2: query_callback: "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf".
DEBUG2: query_callback: "URF=DM3".
DEBUG2: query_callback: "UUID=5b5ec5ce-346e-3d33-5833-b9b77a10683d".
DEBUG2: query_callback: "TLS=1.2".
DEBUG2: query_callback: "Copies=T".
DEBUG2: query_callback: "printer-state=3".
DEBUG2: query_callback: "printer-type=0x1046".
DEBUG2: query_callback(browser=0x564634539ec0, interfaceIndex=-1, protocol=-1, event=2, fullName="Brother\032DCP-7055\032\064\032hallonpaj._ipp._tcp.local", rrclass=1, rrtype=16, rdata=(nil), rdlen=0, flags=0, context=0x564634539180)
DEBUG2: query_callback(browser=0x564634539680, interfaceIndex=2, protocol=1, event=0, fullName="Brother\032DCP-7055\032\064\032hallonpaj._ipps._tcp.local", rrclass=1, rrtype=16, rdata=0x56463453bf50, rdlen=414, flags=5, context=0x564634539000)
DEBUG2: query_callback: "txtvers=1".
DEBUG2: query_callback: "qtotal=1".
DEBUG2: query_callback: "rp=printers/Brother-DCP-7055".
DEBUG2: query_callback: "ty=Brother DCP-7055, using brlaser v4".
DEBUG2: query_callback: "adminurl=https://hallonpaj.local.:631/printers/Brother-DCP-7055".
DEBUG2: query_callback: "note=hallonpaj".
DEBUG2: query_callback: "priority=0".
DEBUG2: query_callback: "product=(DCP-7055)".
DEBUG2: query_callback: "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf".
DEBUG2: query_callback: "URF=DM3".
DEBUG2: query_callback: "UUID=5b5ec5ce-346e-3d33-5833-b9b77a10683d".
DEBUG2: query_callback: "TLS=1.2".
DEBUG2: query_callback: "Copies=T".
DEBUG2: query_callback: "printer-state=3".
DEBUG2: query_callback: "printer-type=0x1046".
DEBUG2: query_callback(browser=0x564634539680, interfaceIndex=2, protocol=0, event=0, fullName="Brother\032DCP-7055\032\064\032hallonpaj._ipps._tcp.local", rrclass=1, rrtype=16, rdata=0x56463453c2e0, rdlen=414, flags=5, context=0x564634539000)
DEBUG2: query_callback: "txtvers=1".
DEBUG2: query_callback: "qtotal=1".
DEBUG2: query_callback: "rp=printers/Brother-DCP-7055".
DEBUG2: query_callback: "ty=Brother DCP-7055, using brlaser v4".
DEBUG2: query_callback: "adminurl=https://hallonpaj.local.:631/printers/Brother-DCP-7055".
DEBUG2: query_callback: "note=hallonpaj".
DEBUG2: query_callback: "priority=0".
DEBUG2: query_callback: "product=(DCP-7055)".
DEBUG2: query_callback: "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf".
DEBUG2: query_callback: "URF=DM3".
DEBUG2: query_callback: "UUID=5b5ec5ce-346e-3d33-5833-b9b77a10683d".
DEBUG2: query_callback: "TLS=1.2".
DEBUG2: query_callback: "Copies=T".
DEBUG2: query_callback: "printer-state=3".
DEBUG2: query_callback: "printer-type=0x1046".
DEBUG2: query_callback(browser=0x564634539680, interfaceIndex=-1, protocol=-1, event=2, fullName="Brother\032DCP-7055\032\064\032hallonpaj._ipps._tcp.local", rrclass=1, rrtype=16, rdata=(nil), rdlen=0, flags=0, context=0x564634539000)
DEBUG2: query_callback(browser=0x56463453adc0, interfaceIndex=2, protocol=1, event=0, fullName="Brother\032DCP-7055\032\064\032hallonpaj._printer._tcp.local", rrclass=1, rrtype=16, rdata=0x56463453ad24, rdlen=1, flags=5, context=0x564634539560)
DEBUG2: query_callback(browser=0x56463453adc0, interfaceIndex=2, protocol=0, event=0, fullName="Brother\032DCP-7055\032\064\032hallonpaj._printer._tcp.local", rrclass=1, rrtype=16, rdata=0x5646345390e4, rdlen=1, flags=5, context=0x564634539560)
DEBUG2: query_callback(browser=0x56463453adc0, interfaceIndex=-1, protocol=-1, event=2, fullName="Brother\032DCP-7055\032\064\032hallonpaj._printer._tcp.local", rrclass=1, rrtype=16, rdata=(nil), rdlen=0, flags=0, context=0x564634539560)
network dnssd://Brother%20DCP-7055%20%40%20hallonpaj._ipp._tcp.local/cups?uuid=5b5ec5ce-346e-3d33-5833-b9b77a10683d "DCP-7055" "Brother DCP-7055 @ hallonpaj" "" ""
DEBUG: sent=3, count=3
DEBUG: sent=3, count=0
DEBUG: sent=3, count=0
DEBUG: sent=3, count=0
```


*** $ lpinfo -v *** gives
```
network beh
network socket
file cups-brf:/
serial serial:/dev/ttyS0?baud=115200
network ipp
network ipps
network http
direct hp
network lpd
network https
direct hpfax
network dnssd://Brother%20DCP-7055%20%40%20hallonpaj._ipp._tcp.local/cups?uuid=5b5ec5ce-346e-3d33-5833-b9b77a10683d

```


*** $ avahi-browse -a -v -t -r***   gives (sanitized)
```
Serverversion: avahi 0.7; Värdnamn: ubuntucomputer.local
H Grän Prot Namn                                          Typ                  Domän
+ enp3s0 IPv6 HALLONPAJ                                     _device-info._tcp    local
+ enp3s0 IPv4 HALLONPAJ                                     _device-info._tcp    local
+ enp3s0 IPv6 HALLONPAJ                                     Microsoft Windows Network local
+ enp3s0 IPv4 HALLONPAJ                                     Microsoft Windows Network local
+ 
= enp3s0 IPv6 HALLONPAJ                                     Microsoft Windows Network local
   hostname = [hallonpaj.local]
   address = [blurred]
   port = [445]
   txt = []
= enp3s0 IPv6 HALLONPAJ                                     _device-info._tcp    local
   hostname = [hallonpaj.local]
   address = [blurred]
   port = [0]
   txt = ["model=MacSamba"]
+ enp3s0 IPv6 Brother DCP-7055 @ hallonpaj                  Internet Printer     local
+ enp3s0 IPv4 Brother DCP-7055 @ hallonpaj                  Internet Printer     local
+ enp3s0 IPv6 Brother DCP-7055 @ hallonpaj                  Secure Internet Printer local
+ enp3s0 IPv4 Brother DCP-7055 @ hallonpaj                  Secure Internet Printer local
= enp3s0 IPv4 HALLONPAJ                                     _device-info._tcp    local
   hostname = [hallonpaj.local]
   address = [192.168.2.201]
   port = [0]
   txt = ["model=MacSamba"]
= enp3s0 IPv4 HALLONPAJ                                     Microsoft Windows Network local
   hostname = [hallonpaj.local]
   address = [192.168.2.201]
   port = [445]
   txt = []
+ enp3s0 IPv6 Brother DCP-7055 @ hallonpaj                  UNIX Printer         local
+ enp3s0 IPv4 Brother DCP-7055 @ hallonpaj                  UNIX Printer         local
= enp3s0 IPv6 Brother DCP-7055 @ hallonpaj                  Internet Printer     local
   hostname = [hallonpaj.local]
   address = [blurred]
   port = [631]
   txt = ["printer-type=0x1046" "printer-state=3" "Copies=T" "TLS=1.2" "UUID=5b5ec5ce-346e-3d33-5833-b9b77a10683d" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(DCP-7055)" "priority=0" "note=hallonpaj" "adminurl=https://hallonpaj.local.:631/printers/Brother-DCP-7055" "ty=Brother DCP-7055, using brlaser v4" "rp=printers/Brother-DCP-7055" "qtotal=1" "txtvers=1"]
= enp3s0 IPv4 Brother DCP-7055 @ hallonpaj                  Internet Printer     local
   hostname = [hallonpaj.local]
   address = [192.168.2.201]
   port = [631]
   txt = ["printer-type=0x1046" "printer-state=3" "Copies=T" "TLS=1.2" "UUID=5b5ec5ce-346e-3d33-5833-b9b77a10683d" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(DCP-7055)" "priority=0" "note=hallonpaj" "adminurl=https://hallonpaj.local.:631/printers/Brother-DCP-7055" "ty=Brother DCP-7055, using brlaser v4" "rp=printers/Brother-DCP-7055" "qtotal=1" "txtvers=1"]
= enp3s0 IPv6 Brother DCP-7055 @ hallonpaj                  UNIX Printer         local
   hostname = [hallonpaj.local]
   address = [blurred]
   port = [0]
   txt = []
= enp3s0 IPv6 Brother DCP-7055 @ hallonpaj                  Secure Internet Printer local
   hostname = [hallonpaj.local]
   address = [blurred]
   port = [631]
   txt = ["printer-type=0x1046" "printer-state=3" "Copies=T" "TLS=1.2" "UUID=5b5ec5ce-346e-3d33-5833-b9b77a10683d" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(DCP-7055)" "priority=0" "note=hallonpaj" "adminurl=https://hallonpaj.local.:631/printers/Brother-DCP-7055" "ty=Brother DCP-7055, using brlaser v4" "rp=printers/Brother-DCP-7055" "qtotal=1" "txtvers=1"]
= enp3s0 IPv4 Brother DCP-7055 @ hallonpaj                  Secure Internet Printer local
   hostname = [hallonpaj.local]
   address = [192.168.2.201]
   port = [631]
   txt = ["printer-type=0x1046" "printer-state=3" "Copies=T" "TLS=1.2" "UUID=5b5ec5ce-346e-3d33-5833-b9b77a10683d" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(DCP-7055)" "priority=0" "note=hallonpaj" "adminurl=https://hallonpaj.local.:631/printers/Brother-DCP-7055" "ty=Brother DCP-7055, using brlaser v4" "rp=printers/Brother-DCP-7055" "qtotal=1" "txtvers=1"]
= enp3s0 IPv4 Brother DCP-7055 @ hallonpaj                  UNIX Printer         local
   hostname = [hallonpaj.local]
   address = [192.168.2.201]
   port = [0]
   txt = []
: Cachen är full
: Alla just nu

```


***ifconfig*** gives
```
enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.202  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::90a0:823b:b945:7cc6  prefixlen 64  scopeid 0x20<link>
        ether a0:blurred:a0  txqueuelen 1000  (Ethernet)
        RX packets 3152486  bytes 217421505 (217.4 MB)
        RX errors 0  dropped 2  overruns 0  frame 0
        TX packets 7047194  bytes 10635176002 (10.6 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 4495201  bytes 10330087769 (10.3 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4495201  bytes 10330087769 (10.3 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

***$ route*** gives
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         _gateway        0.0.0.0         UG    100    0        0 enp3s0
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.2.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
```

Here is a bit from ***/var/log/cups/error_log*** immediately after I clicked print in Thunderbird.
```
D [03/Oct/2021:21:18:25 +0200] CUPS-Get-Printers
D [03/Oct/2021:21:18:25 +0200] [Client 24] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost.
D [03/Oct/2021:21:18:25 +0200] [Client 24] Content-Length: 931
D [03/Oct/2021:21:18:25 +0200] [Client 24] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [03/Oct/2021:21:18:25 +0200] [Client 24] con->http=0x55f908898140
D [03/Oct/2021:21:18:25 +0200] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=931, response=0x55f9088472d0(IPP_STATE_DATA), pipe_pid=0, file=-1
D [03/Oct/2021:21:18:25 +0200] [Client 24] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [03/Oct/2021:21:18:25 +0200] [Client 24] bytes=0, http_state=0, data_remaining=931
D [03/Oct/2021:21:18:25 +0200] [Client 24] Flushing write buffer.
D [03/Oct/2021:21:18:25 +0200] [Client 24] New state is HTTP_STATE_WAITING
D [03/Oct/2021:21:18:25 +0200] [Client 24] Waiting for request.
D [03/Oct/2021:21:18:25 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Oct/2021:21:18:25 +0200] [Client 24] HTTP_STATE_WAITING Closing for error 32 (Broken pipe)
D [03/Oct/2021:21:18:25 +0200] [Client 24] Closing connection.
D [03/Oct/2021:21:18:25 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
I [03/Oct/2021:21:18:26 +0200] Expiring subscriptions...
I [03/Oct/2021:21:18:55 +0200] Saving subscriptions.conf...
D [03/Oct/2021:21:18:55 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
I [03/Oct/2021:21:18:55 +0200] Expiring subscriptions...
```

In [http://127.0.0.1:631/](http://127.0.0.1:631/) the printer is listed with same name as in Ubuntu settings. I can print a test page. I can print from ie Libreoffice Calc. But not from Thunderbird
The Raspberry Pi 3 that the printer is connected to is Running Rasbian and is up to date.

---

### Post by ajgreeny on 2021-10-03
If I open an email message in T'bird 78 I see this dialogue window appear, with three different instances of the HP Envy printer that's connected by wifi only, no USB connection or cable modem/router connection here.

I do have a static IP for the printer which I believe is probably essential for the printer to always be detected properly when needed.

I can not quite figure out from your description, what you are seeing when you try to print; does it look anything like this?

---

### Post by Cadryc on 2021-10-04
> **ajgreeny said:**
> If I open an email message in T'bird 78 I see this dialogue window appear, with three different instances of the HP Envy printer that's connected by wifi only, no USB connection or cable modem/router connection here.

I do have a static IP for the printer which I believe is probably essential for the printer to always be detected properly when needed.

I can not quite figure out from your description, what you are seeing when you try to print; does it look anything like this?

My Raspberry Pi has a static IP, and so does the computer.

In other programs I get a window like the one you showed. Calc and Firefox lists one printer, Image vie&#7811;er list the printer two times.
Here is screenshots of what I get in Thunderbird when clicking print, the first picture says "Loading content for printing.... Preparing"
The progress bar goes up to 100% and then simply vanishes.

[ATTACH=CONFIG]289237[/ATTACH][ATTACH=CONFIG]289238[/ATTACH][ATTACH=CONFIG]289239[/ATTACH]

---

### Post by Cadryc on 2021-10-04
I GOT IT WORKING! :-D

the screenshot from ajgreeny got me thinking. Why did I not get the same in Thunderbird, as I do in other programs. Maybe the progressbar that I got was supposed to lead up to that window. So I browsed through about:config (settings, general, scroll all the way down, click config editor) looking at all variables beginning with print, and changed this one to **false**

**print.always_print_silent**

And now It works, after the progressbar reaches 100% I get the window I'm supposed to, where I can select print to file or the printer. The printer is listed twice but that doesn't matter, I printed a mail and it works!

---

### Post by mIk3_08 on 2021-10-04
> **ajgreeny said:**
> dialogue window 
Here is mine also,
[IMG]https://i.imgur.com/6NFfCe6.jpg[/IMG]

> **Cadryc said:**
> My Raspberry Pi has a static IP, and so does the computer.

I think you must have to install your printer driver package coming from the brother website.

---

### Post by Cadryc on 2021-10-04
> **mIk3_08 said:**
> 
I think you must have to install your printer driver package coming from the brother website.

Brother only supplies x84 linux drivers. But there are a custom made driver called brlaser.

Anyhow, I got it working :-) See my previous post for the solution

---

