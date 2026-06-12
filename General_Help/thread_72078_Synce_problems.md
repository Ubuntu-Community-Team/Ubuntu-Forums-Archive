---
title: "Synce problems"
date: 2005-10-05
forum: General Help
---

### Post by docmanny on 2005-10-05
I've followed the howto but keep getting stuck.
I installed all the required repositories then :
> manny@ubuntu:~$ sudo synce-serial-config ttyUSB0
You can now run synce-serial-start to start a serial connection.
manny@ubuntu:~$ dccm
manny@ubuntu:~$ sudo synce-serial-start
/usr/share/synce/synce-serial-common: line 58: kill: (17968) - No such process
synce-serial-start is now waiting for your device to connect
manny@ubuntu:~$ sudo synce-pstatus
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
manny@ubuntu:~$ sudo synce-matchmaker
[rapi_context_connect:100] DCCM not running with pid 6986
[main:23] Failed to initialize RAPI
manny@ubuntu:~$ synce-matchmaker
[synce_info_new:31] unable to open file: /home/manny/.synce/active_connection
[rapi_context_connect:88] Failed to get connection info
[main:23] Failed to initialize RAPI
manny@ubuntu:~$

I've already spent too much time trying to set this up. Its a Dell Axim X30...
How do I initialize RAPI???

---

### Post by hanzj on 2005-10-05
Hello, I'm following the steps on [http://synce.sourceforge.net/synce/howto.php](http://synce.sourceforge.net/synce/howto.php).

I get my first error message when i run the "synce-serial-start" command (in root, of course).




I got the following files from repository:

synce-dccm (version 0.9.0-1)
synce-multisync-plugin (0.9.0-3)
synce-serial (0.9.0+cvs041204-1)
libsynce0 (0.9.0-3)
librra0
librra0-tools 
librapi2-tools 

I did not compile synce myself. I used Ubuntu's precompiled version.

Linux kernel is 2.6.10

Linux Distribution: Ubuntu 5.04 (Hoary Hedgehog)

Pocket PC info: HP Jornada 540 series
Microsoft Windows CE
Version 3.0.9348 (Build 9357)
Processor: SHx SH3

I connect with a USB cable.
My pocketpc is not password-protected.


relevant output of cat /proc/bus/usb/devices 

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=16 #Cfgs=  1
P:  Vendor=03f0 ProdID=1016 Rev= 0.00
C:* #Ifs= 1 Cfg#= 1 Atr=40 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=ipaq
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=1ms
 

The command that works for me (I say it works because there isn't an error message) is: sudo synce-serial-config tty0.
When I run that I get the following output.


"You can now run synce-serial-start to start a serial connection."

--------------------------
So I run synce-serial-start
Output:

/usr/share/synce/synce-serial-common: line 58: kill: (9851) - No such process

synce-serial-start is now waiting for your device to connect
--------------
Does that line starting with "/usr/share" mean that the synce-serial-start command is trying to kill something that isn't there ? Is it something that I can ignore?


-----------------
I proceed with  the next step.

I type dccm. Nothing displays on the screen (even when I unplug the USB plug from the computer).

-----
I try: synce-pstatus.

Output is:
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred


---------------


I have spent many hours trying to set this up. Please help me.



Thank you very much for your help.





p.s.  I wish that in the future it will be easier to sync pdas with ubuntu/linux.

---

