---
title: "Xerox Phaser 7400DN"
date: 2014-01-20
forum: General Help
---

### Post by John Jason Jordan on 2014-01-20
My computer has Xubuntu 13.10. In the following "printer" means the CUPS setup on my computer. I have several laser printers on my home ethernet, and I can print to all of them except the one I need for the job at hand. This printer worked fine as recently as a few days ago.

Nothing has changed in the printer properties window for this printer. When I try to print to it I get an error message that it is not connected, yet I can ping it (192.168.0.135). The
Xubuntu 13.10 GUI says under Printer State: "Processing - The printer is in use."  The printer's control panel says it is ready to print. I have stopped and restarted CUPS, but I still can't get the computer to recognize that the printer is ready to accept a job. From the print device's control panel I can print a test page without problem.

When I try to print from any application now, next to this printer in the applications print dialog box is the message "the printer is in use." I have duplicated the printer, and the new printer tries to print a test page once, then immediately says the printer is in use. The test page never gets to the printer. I also recreated the printer from scratch, and got the same results. My current favorite printer uses the PPD file for this printer (Phaser 7400DN), but I have other printers configured for it using the Xerox driver. If I try to print to this printer from any of these other printers I get the same results - first it says it is accepting jobs, then as soon as I send it a job it goes to "the printer is in use" and the print job never gets to the printer.

>From the command line lpstat -a gives me:  

Xerox-Phaser-7400DN-PPD3 accepting requests since Mon 20 Jan 2014 06:33:09 PM PST

Searching the forums for this issue was not very successful because you can't search on "the printer is in use" as one string, and without the quotes the search engine gives me any post with any of the words in them. However, I did stumble across something I was unaware of before - using your browser (e.g., Firefox) you can go to [http://localhost:631/](http://localhost:631/) and there are all your printers, with ways to manage them. Cool tool! Unfortunately, none of the options there solved my problem. But it may be helpful if I paste in here what it said about the print device (it says the same thing for all the printers that I have installed for this print device):

Xerox Phaser 7400DN PPD3		Local Raw Printer	Processing - "The printer is in use."

Needless to say, the printer's control panel indicates "Ready" and there are no print jobs in the queue. Of course, I have also turned the print device off and back on again, and rebooted the computer, but still no joy.

How can it be that I can ping the printer, but CUPS gets stuck thinking that the printer is in use? Is there a config file somewhere that CUPS uses to get information about printers, that I can modify or delete? I have spent two hours so far googling, with no solution in sight. I need some brilliant suggestions.

Edit: Problem solved.

I found the phasersmart.com website which purports to fix problems with Xerox printers. You start by entering the address of the printer, but when I did the site could not find the printer. In frustration eventually I just entered its IP address in the Firefox URL bar, and guess what popped up? MY HDHomeRun TV tuner. Then I remembered that there had been a brief power outage a couple of weeks ago. Apparently when the HDHomeRun came back up it decided it should be 192.168.0.135. This was not a wise choice, as that was the address of the Xerox. Needless to say, that is why I was able to ping the printer, except that it was the HDHomeRun that was sending the response. And that explains the goofy "the printer is in use" error message.

---

