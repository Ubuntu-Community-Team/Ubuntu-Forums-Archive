---
title: "FORScan OBD2 Code Reader ELM327 Scan Tool USB to Serial COM with CH340 chip"
date: 2023-03-27
forum: General Help
---

### Post by 777funk on 2023-03-27
I spent over a half day trying to get this scan tool to work with FORScan software to do some diagnostics on my Ford Powerstroke Diesel (7.3L) and this may save someone else some time. I followed this:

[https://forscan.org/forum/viewtopic.php?t=6](https://forscan.org/forum/viewtopic.php?t=6)

Other than that this user is on 32 bit (in the wine configuration file). I left it as 64 bit since I'm running a 64 bit os. 

AND... for the life of me it would not connect. The computer could not find the USB adapter cable. This command wouldn't output anything:
```
ls /dev/ttyUSB*
```

where as it should output:
```
/dev/ttyUSB0
```

if all is well. So since the computer didn't see it, FORScan also could not connect to the adapter. 

Finally, I found that the USB to OBDII cable was conflicting with a Braille package. So to fix, here is what I did:

 Unless you are using a braille display this should do the trick:
 ```
sudo apt remove brltty 

``` Don't forget to plug your dongle off and on

     
                                                                                         
taken from [this]("https://askubuntu.com/questions/1403705/dev-ttyusb0-not-present-in-ubuntu-22-04") solution. Hopefully this saves some other poor soul some headaches. It was also trouble to install in Windows. I had to install the drivers for the CH340 chip manually.

---

