---
title: "issues with installing brother mfc7360n as network printer."
date: 2016-02-05
forum: General Help
---

### Post by Matthieu_van_Kints on 2016-02-05
Hey guys, 

to start i've read this post [http://ubuntuforums.org/showthread.php?t=1784369](http://ubuntuforums.org/showthread.php?t=1784369) inside and out. 
the thing is al have this printer now for some time, always used it as usb connected printer, which works like a charm. 
but i kinda bought it also for it's network ability. so since resently i got a network installed (were some construction issues that stopped me from putting onde down earlier) 
so now i took the time to try to install it over the network. 

i did everything that was mentioned in this thread, but... since ubuntu has went from 10 -> 15. things are slightly different. at least that is what i believe to be the 'cause. 

so what did i see instead of this. 

[COLOR=#000000]8b. For Network... unplug the USB cable. Go to the second drop down menu and select "Modify Printer". Again, when prompted for a login you put the same login as logging into your computer. There you will be able to select the "Current Driver" and click "Modify". After that you should get a message saying "Modification completed successfully". You should now be ready to print. If you go back to the page at "http://localhost:631/printers" you should be able to select "Print Test Page" again and see the magic happen. 

[/COLOR]so indeed 2e dropdown gives a modify printer, didn't need to log in this time. 

but instead of select current driver, i have this: 
[TABLE]
[TR]
[TH="class: label, align: right"]Current Connection:[/TH]
[TD] dnssd://Brother%20MFC-7360N._pdl-datastream._tcp.local/[/TD]
[/TR]
[TR]
[TH="class: label, align: right"]Local Printers:[/TH]
[TD] Serial Port #1 
 HP Printer (HPLIP) 
 Brother MFC-7360N (Brother MFC-7360N)
 HP Fax (HPLIP) [/TD]
[/TR]
[TR]
[TH="class: label, align: right"]Discovered Network Printers:[/TH]
[TD] Brother MFC-7360N (Brother MFC-7360N)[/TD]
[/TR]
[TR]
[/TR]
[TR]
[TH="class: label, align: right"]Other Network Printers:[/TH]
[TD] Internet Printing Protocol (ipps) 
 Internet Printing Protocol (https) 
 Internet Printing Protocol (ipp14) 
 Internet Printing Protocol (http) 
 Internet Printing Protocol (ipp) 
 LPD/LPR Host or Printer 
 AppSocket/HP JetDirect 
[/TD]
[/TR]
[/TABLE]
so i selected the discovered network printer.. which seems logical. and the correct printer. 
than i modified it . which it does.. but when i want to print a test page.. it can't find it... 

don't know what goes wrong, seems al so simple and logical. 
typing this i feel like i might need to reboot. well i will do that in a minute but doubtfull it wil help 
,
what i also did is make use of the brother printer scanner installation tool that is available from brother, which really didn't do that much different then when doing it manually. 

so if any of you guys have an idea. i would really welcom it !!

kind greatings matt. 

ps: pitty that earlier topic is closed, i could've just added this question to it.

as expected, reboot didn't help, should've done it before i posted this but still, no effect: 
over time after i give the command to print test page it says 
[I]1) "Unable to locate printer "BRN30055C3491CB.local"."
[/I]2)*"Connecting to printer."*
3)[I]"The printer is not responding."

[/I]soi knows the printers id, it found it on the net.. connection is still there (network lights are on) 

anyway. just though i add this info 
also Ubuntu 15.10

---

### Post by Matthieu_van_Kints on 2016-02-05
i got it solved myself, it was simple basically. 

in the printer itself i needed to set the correct network parameters so..  once done it was visible on the network and printing.

---

