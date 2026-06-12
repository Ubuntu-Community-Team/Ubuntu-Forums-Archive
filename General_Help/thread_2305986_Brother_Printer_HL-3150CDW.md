---
title: "Brother Printer HL-3150CDW"
date: 2015-12-11
forum: General Help
---

### Post by angel mike on 2015-12-11
Can someone give me a link to any easy way of installing a network Brother Printer HL-3150CDW which is not listed on Brother Site.Tried using Install Tool but without success.
Have installed the printer on my desktop PC with Ubuntu as a network printer using CUPS but having trouble with my Dell Laptop. Thanks

---

### Post by SeijiSensei on 2015-12-11
I used the install tool with my HL-3170CDW without a problem, and it sounds like you have it working on one Ubuntu machine.  What "trouble" are you having with the Dell laptop?  Is it running Ubuntu?  If so, have you tried using the browser-based CUPS utility?  Point a browser at [http://localhost:631/](http://localhost:631/) and follow the steps to install the printer.  You should see it listed under available network printers.

---

### Post by angel mike on 2015-12-12
Thanks SeijiSensi for response - I have used the [http://localhost:631/](http://localhost:631/) link but did not result in a working printer network connection.
 I did have one thought though - The Dell XPS is 64bit and it appears that Brother Drivers will work in either 32 or 64bit mode but the latter needs some extra commands ? I found this                          **[I'm using a Linux 64 bit edition. Can I use the Brother Linux printer drivers?** 


Yes. Brother printer drivers are created and optimized for 32 bit version of Linux,
but those can be used for 64 bit Linux also. Some additional steps are required.


 Copy brlpdwrapperXXX files under /usr/lib/cups/filter/ to /usr/lib64/cups/filter/

      [B]Command: cp     /usr/lib/cups/filter/brlpdwrapper* /usr/lib64/cups/filter ]

No idea what this means though ! Mike
[/B]

---

### Post by SeijiSensei on 2015-12-13
Open a terminal and run the command:
```
sudo cp /usr/lib/cups/filter/brlpdwrapper* /usr/lib64/cups/filter
```

I will say I have 64-bit Linux installations and didn't need to do this on my systems.

> Have installed the printer on my desktop PC with Ubuntu as a network printer using CUPS
How is the printer connected, via a USB cable to the desktop PC or via an Ethernet cable directly to the network?  I'm using the latter method.  I just gave the printer a static IP address in my local network outside the DHCP-assigned range, and everything worked fine.  CUPS shows the printer in the network section when I run the web interface on a client machine.  I did have to use the 3070CDW driver since there was none available for my 3170CDW.  As I expected, it didn't matter in the least.

---

