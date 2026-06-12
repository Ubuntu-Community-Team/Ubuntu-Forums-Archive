---
title: "Brother scanner problems"
date: 2021-04-01
forum: General Help
---

### Post by lesliek2 on 2021-04-01
Please excuse any mistakes that I make in technical terms.
I use Ubuntu 20.04.
I have a Brother MFC-L2730DW printer and scanner.
I have been able in the past to use both functions, but today the scanner wouldn't work.
I believe I know why, but I don't know how to fix it. I believe that the reason it stopped working is that the network changed the IP address of my printer/scanner after I configured the scanner.
When I run the command brsaneconfig4 -q, I get the following:

* MFC-L2730DW  [192.168.100.108]  MFC-L2730DW
  MFC-L2730DW  [192.168.100.101]  Brother_MFC-L2730DW_series

I assume that the asterisk means that the address the scanner looks for is the one that ends in 108. However, if I ping it, I'm told it's unreachable and if I ping the address that ends in 101, all works as expected.
If I enter my modem via my browser, I see that the printer/scanner's IP address right now is the one that ends in 101. I believe the browser used to show the address as ending in 108.

I believe that I could remove both scanner entries from brsaneconfig4 and then create a new entry using the 101 IP address, but that would only work until the printer/scanner's IP address changes again.
I rang my ISP. It said I couldn't assign a static IP address to the printer/scanner via my modem.

Is there anything else I can do so that it won't matter if the device's IP address changes?

Thanks,

Leslie

---

### Post by TheFu on 2021-04-03
If you can't set the IP in the printer/scanner, then you'll need a DHCP server that can do "DHCP reservations."  DHCP reservations are a basic capability for any router made the last 10 yrs.

Do you have a separate router from the modem?
Do you know if the scanner/printer supports zeroconf?  That let you ping it using "hostname.local" usually.   Replace "hostname" with the hostname for the scanner/printer. If so, setup the scanning software to use the hostname.local method, not the IP address.

---

