---
title: "Print job stuck on pending, printer refuses to 'enable' itself"
date: 2023-02-11
forum: General Help
---

### Post by xanizen on 2023-02-11
I have 2 computers in the household set up with Ubuntu 22.04.
The first one is a 12 year old Gateway DX-4300-15e desktop with an integrated graphics card.
The second computer is a 'custom' built one featuring a UEFI 'Bios', on a 2013 intel chipset for Core i3 to i7 processors.

The Gateway was able to successfully send a print job to the printer, the latter computer could not.

The printer is a Brother HL-2270DW laser printer, acquired in 2013 connected to a router (network printer).

I was able to successfuly print a test page, when I first installed Ubuntu 22.04 2 weeks ago, but now jobs are stuck on pending. 
I can successfully ping the printer's IP address from the problem computer.

I went to CUPS, [http://localhost:631](http://localhost:631), and the test page refused to print.

Output of, dpkg -l | grep Brother:
```
ii  printer-driver-brlaser    6-3        amd64    printer driver for (some) Brother laser printers
ii  printer-driver-ptouch    1.6-2build1    amd64    printer driver Brother P-touch label printers

```

'sudo systemctl restart cups' did nothing.

Apparently the printers are disabled.

```
$ lpstat -p
printer Brother_HL_2270DW_series disabled since Fri 10 Feb 2023 11:57:01 PM EST -
    reason unknown
printer HL-2270DW disabled since Fri 10 Feb 2023 07:38:28 PM EST -
    Rendering completed
    
```

HL-2270DW, 2nd in the output, is the desired/default printer.

System Settings GUI says printer stopped, so I click the restart button. The button goes away so I execute lpstat -p, again, and it's still saying disabled.
I go to additional printer settings, right click on the printer and select 'Enable', and the Stopped sign comes up on the printer again along with 'Restart'.
I decide to 'trash'/terminate all jobs, then when I click restart, the printer refuses to enable and the restart button keeps appearing.

I've ensured, systemctl status cups, displays CUPS as 'Running'.

I went ahead an downloaded the CUPS driver from the Brother website
[https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hl2270dw_all&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hl2270dw_all&os=128)

But I'm wondering if that's necessary and if so, should (and how to) I remove the old default drivers?

**Edit**: Going to advanced printer settings, then selecting the appropriate network printer (which will have its LAN IP next to its name), and then selecting 'LPD/LPR queue ï¿½BINARY_P1', may have fixed the problem. I did disable cups with systemctl before doing this, and did not have to re-enable it.
[https://i.imgur.com/8Rv9my7.png](https://i.imgur.com/8Rv9my7.png)

---

