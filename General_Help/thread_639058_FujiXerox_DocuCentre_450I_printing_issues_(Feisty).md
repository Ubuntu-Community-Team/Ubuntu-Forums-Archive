---
title: "FujiXerox DocuCentre 450I printing issues (Feisty)"
date: 2007-12-12
forum: General Help
---

### Post by noctis_vulpes on 2007-12-12
There's a FujiXerox DocuCentre 450I at my workplace. Obviously, printing is an essential thing here, so I tried to set up Feisty so that it can print.

To my delight, Feisty detects the printer and correctly identifies it - that is, when I try to add printer, it finds the printer on the correct IP address as FUJI XEROX DoceCentre 450 I (FUJI XEROX DocuCentre 450I [IP address]). 

However, when I tried to continue further, I realized that there were no printer drivers available for this model (or any FujiXerox, for that matter). So I had all but given up until I found this:

[http://blogs.sun.com/wind/entry/install_fuji_xerox_docucentre_450](http://blogs.sun.com/wind/entry/install_fuji_xerox_docucentre_450)

I followed this direction and added the printer, but when I try to print out anything (including the test page) it prints out what appears to be postscript code. The printer spews out all this code in plain text instead of interpreting them into a proper document. 

Further googling found people saying they could get their printer to work on generic postscript printer. No dice for me. It wields same results - pages after pages of code. 

Does anyone have any idea what I should do from here? It looks like I'm so close to getting this to work. When I say that it's printing out code, I don't mean incomprehensible garbage, but proper, readable code - with comments and everything. Here's part of the output for the test page:

%!PS-Adobe-3.0
%%LanguageLevel: 1
%%DocumentData: Clean7Bit
%%DocumentSuppliedResources: procset testprint/1.2
.
.
.
% Loop through 100 shares...
0 0.010101 0.98 {
% Set the color...
dup 0.75 le {
. 
.
.

So on and so forth. Anyone know what I need to do?

Thank you in advance for your help.

P.S. I don't know if this means anything, but "printing" to a PDF file works perfectly.

---

### Post by noctis_vulpes on 2007-12-17
Solved. -_- It seems that all I had to do was apply generic PCL driver. Printing web pages is still a little funky... Image sizes are all wrong. 

But it's better than nothing I guess.

---

