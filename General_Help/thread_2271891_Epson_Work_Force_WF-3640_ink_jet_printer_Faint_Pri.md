---
title: "Epson Work Force WF-3640 ink jet printer Faint Printing"
date: 2015-04-02
forum: General Help
---

### Post by j_keiter on 2015-04-02
Bought at Costco for $89 around 1/15/15 if I remember correctly.
How to fix faint printing problem. By default the printed pages look washed-out. They look fine in Windows or Mac.  
You have to set the paper type to "plain papers-High" and
that seems to fix it. 
Must open Printers'Configue Printers' in linux
and right click on Epson printer icon and select properties - Printer
Options - Media Type - plain papers-High Link to Solution: [http://www.openprinting.org/printer/Epson/Epson-WF-3620_Series](http://www.openprinting.org/printer/Epson/Epson-WF-3620_Series) Crap!  I also had to select print - Page Setup -
Paper Type - 'plain papers-High' in whatever application I was using
as the app. would overwrite the 'Configure Printers settings.  Check
it before you print as it seems to revert back to 'plain papers'. 

I succeeded in installing the drivers in this
order on XUbuntu 12.14 and 14.04 by right clicking on downloaded .deb
files and opening with Software Center. Link for drivers: [http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?oid=232592&BV_UseBVCookie=yes&infoType=Downloads&platform=OSF_O_LINUX](http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?oid=232592&BV_UseBVCookie=yes&infoType=Downloads&platform=OSF_O_LINUX) 

iscan-data_1.33.0-1_all.deb epson-inkjet-printer-escpr_1.4.4-1lsb3.2_amd64.deb iscan_2.30.0-1~usb0.1.ltdl7_amd64.deb Now go to printers and hit the big + symbol to
add a new printer.   Give it time to find the network printers.  Also
make sure the Epson is on and log on to your router and make sure you
see the Epson in the DHCP table if your only connected by wireless. 
Select the WF-3640 when it shows up and allow it to search for
driver.  the ppd file is located in 
installed ppds are in /etc/cups/ppd. The
database is in /usr/share/ppd I had to extract the
/usr/share/ppd/Epson-WF-3640_Series-epson-inkjet-printer-escpr.ppd.gz
to /etc/cups/ppd,  The extraction prduced two files: EPSON-WF-3640-Series.ppd Epson-WF-3640_Series-epson-inkjet-printer-escpr.ppd I think I picked the escpr file during the add
printer process.   I successfully printed color test page but had
issues with it being too faint.  This was solved by changing paper
type to standard paper-High.  Also had to set in application I was
using eg. Gimp or PDF Viewer.

---

