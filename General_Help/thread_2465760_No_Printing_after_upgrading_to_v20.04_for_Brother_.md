---
title: "No Printing after upgrading to v20.04 for Brother Laser"
date: 2021-08-10
forum: General Help
---

### Post by Rick St. George on 2021-08-10
After upgrading from UbuntuStudio v18.04 to v20.04 can't get my Brother Laser printer (HL-L2395DW) to work. It is installed with latest Brother drivers and Cups v2.3.1, and even shows up on USB port. But Cups Admin shows "waiting for printer to become available". Here are some commands and what I see.

```

avahi-browse -rt _ipp._tcp
+     lo IPv4 HL-L2395DW series                             Internet Printer     local
=     lo IPv4 HL-L2395DW series                             Internet Printer     local
   hostname = [stephen-MS-7640.local]
   address = [127.0.0.1]
   port = [60000]
   txt = ["rfo=ipp/faxout" "Fax=T" "Duplex=T" "PaperMax=legal-A4" "URF=W8,CP1,IS4-1,MT1-3-4-5-8,OB10,PQ3-4-5,RS300-600-1200,V1.4,DM1" "pdl=application/octet-stream,image/urf,image/pwg-raster" "product=(Brother HL-L2395DW series[en])" "ty=Brother HL-L2395DW series[en]" "note=" "Color=F" "kind=document,envelope,label,postcard" "mopria-certified=1.3" "UUID=e3248000-80ce-11db-8000-3c2af454f1e0" "adminurl=http://127.0.0.1:60000/net/net/airprint.html" "qtotal=1" "txtvers=1" "priority=60" "usb_MDL=HL-L2395DW series" "usb_MFG=Brother" "rp=ipp/print"]

lpstat -a
HLL2395DW accepting requests since Tue 10 Aug 2021 02:54:51 PM CDT

scanimage -L
device `brother4:bus7;dev1' is a Brother HL-L2395DW USB scanner
device `escl:http://127.0.0.1:60000' is a ESCL HL-L2395DW series flatbed scanner

sudo ss -nap | grep 631: 
tcp               LISTEN                 0                   5                                                                           127.0.0.1:631                                               0.0.0.0:*                                   users:(("cupsd",pid=616,fd=7))                                                 
tcp               TIME-WAIT              0                   0                                                                           127.0.0.1:59970                                           127.0.0.1:631                                                                                                                
tcp               TIME-WAIT              0                   0                                                                           127.0.0.1:59962                                           127.0.0.1:631                                                                                                                
tcp               TIME-WAIT              0                   0                                                                           127.0.0.1:59968                                           127.0.0.1:631                                                                                                                
tcp               TIME-WAIT              0                   0                                                                           127.0.0.1:59972                                           127.0.0.1:631                                                                                                                
tcp               ESTAB                  0                   0                                                                           127.0.0.1:59974                                           127.0.0.1:631                                 users:(("palemoon",pid=1507,fd=52))                                            
tcp               TIME-WAIT              0                   0                                                                           127.0.0.1:59964                                           127.0.0.1:631                                                                                                                
tcp               TIME-WAIT              0                   0                                                                           127.0.0.1:59958                                           127.0.0.1:631                                                                                                                
tcp               ESTAB                  0                   0                                                                           127.0.0.1:631                                             127.0.0.1:59974                               users:(("cupsd",pid=616,fd=11))                                                
tcp               LISTEN                 0                   5                                                                               [::1]:631                                                  [::]:*                                   users:(("cupsd",pid=616,fd=6))     


```


Any ideas or suggestions? Any help is appreciated.

---

### Post by Rick St. George on 2021-08-11
Found a patch from Brother, and Steps outlined to fix this problem. Not necessarily for this specific printer, but probably most printers with Ubuntu v20.04 OS. 
FYI ... follow the steps outlined here. Worked for me as I had already downloaded the Driver deb, BrScan deb and Skey deb.

[https://support.brother.com/g/b/faqend.aspx?c=us_ot&lang=en&prod=mfcj4335dw_us_eu&faqid=faq00100729_000]("https://support.brother.com/g/b/faqend.aspx?c=us_ot&lang=en&prod=mfcj4335dw_us_eu&faqid=faq00100729_000")

---

