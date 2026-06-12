---
title: "How to setting blocksize in TFTP server?"
date: 2015-08-10
forum: General Help
---

### Post by tanmanh0707 on 2015-08-10
Dear,

I am working an embedded system project. It downloads a firmware put at TFTP server. I communicated and downloaded successfully with TFTP, but the speed is slow (the fault maybe in my code). Now I want to improve the speed by increasing blocksize up to 1024 bytes. I did as below

```
[COLOR=#333333]cd /etc/default/[/COLOR]
[COLOR=#333333]nano tftpd-hpa[/COLOR]

[COLOR=#333333]in the option quotes add --blocksize 1024[/COLOR]

[COLOR=#333333]save it and then restart tftpd [/COLOR]

[COLOR=#333333]/etc/init.d/tftpd-hpa restart[/COLOR]
```

But TFTP server still transfers with blocksize 512 bytes.

If anyone has idea of changing blocksize, please tell me that.

Thank you and best reagards.

P/s: I'm using Ubuntu 14.04

---

### Post by bab1 on 2015-08-11
> **tanmanh0707 said:**
> Dear,

I am working an embedded system project. It downloads a firmware put at TFTP server. I communicated and downloaded successfully with TFTP, but the speed is slow (the fault maybe in my code). Now I want to improve the speed by increasing blocksize up to 1024 bytes. I did as below

```
[COLOR=#333333]cd /etc/default/[/COLOR]
[COLOR=#333333]nano tftpd-hpa[/COLOR]

[COLOR=#333333]in the option quotes add --blocksize 1024[/COLOR]

[COLOR=#333333]save it and then restart tftpd [/COLOR]

[COLOR=#333333]/etc/init.d/tftpd-hpa restart[/COLOR]
```

But TFTP server still transfers with blocksize 512 bytes.

If anyone has idea of changing blocksize, please tell me that.

Thank you and best reagards.

P/s: I'm using Ubuntu 14.04

It appears that the tftp server does not set the block size to be transferred.  The client asks an the server complies.  In other words you set the ***max*** block size to be sent.  If the client ask for 512 then the client will get that if you have set the max greater.  See the man page exerpt below```
--blocksize max-block-size, -B max-block-size
              S*pecifies the **maximum permitted** block size*.  The permitted range
              for  this parameter is from 512 to 65464.  Some embedded clients
              request large block sizes  and  yet  do  not  handle  fragmented
              packets  correctly;  for these clients, it is recommended to set
              this value to the smallest MTU on your network  minus  32  bytes
              (20  bytes for IP, 8 for UDP, and 4 for TFTP; less if you use IP
              options on your network.)  For example, on a  standard  Ethernet
              (MTU 1500) a value of 1468 is reasonable.
```

Maybe the fault is in your code.  See if you can increase the requested block size.

---

### Post by tanmanh0707 on 2015-08-12
@bab1:
Thank you very much for your support. I found blocksize option in RRQ packet too at [https://tools.ietf.org/html/rfc2348](https://tools.ietf.org/html/rfc2348)

I checked and modified my code to send blksize option in RRQ packet as RFC2348. But I still received 512 octets per block from server.

I wonder if I have to configure TFTP server too???

---

