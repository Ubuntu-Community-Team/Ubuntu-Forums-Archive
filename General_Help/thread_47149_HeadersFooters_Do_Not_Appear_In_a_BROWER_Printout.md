---
title: "Headers/Footers Do Not Appear In a BROWER Printout"
date: 2005-07-07
forum: General Help
---

### Post by ernst on 2005-07-07
I've tried both Firefox 1.0.2 and Mozilla 1.7.6 to have headers/footers print when printing a page using these browsers.  They do not. 

Using File - Page Setup - Margins & Header/Footer, I can select whatever items I would like to appear in headers and footers.  Reviewing these using Print Preview, they all appear; but, when actually printing the page they do not appear.

Has anyone else had this problem?  (I'm not even sure if the problem relates to Firefox or Mozilla or Ubuntu - Coud it be a printer driver?).

Ernst

---

### Post by supertabular on 2005-07-31
Not sure if this is the same problem that I was having but maybe they are related. In my case, Firefox would print headers and footers but they were placed outside the printable area.  The result being that you'd see them in postscript but not in the printout.  That's because the default offset is 0.05in or some ridiculous value like that.  What's confusing is that there are actually _two_ dialogs that control printing margins and offsets in Firefox: the first is in File > Page Setup > Margin & Header/Footer tab (set margins there),  and the second in Print > Properties (set header and footer offsets there).  I changed the settings to 1in margins and 0.5in offsets, and now it prints fine.  Hope this helps.

---

### Post by sql on 2008-04-09
i succesfully solved this problem for myself.
i have printer named 3120.
go about:config
enter keyword "edge"
then i change this values so :

print.printer_CUPS/3120.print_edge_bottom=60

print.printer_CUPS/3120.print_edge_left=40

print.printer_CUPS/3120.print_edge_right=40

print.printer_CUPS/3120.print_edge_top=40


by the way sucha variables as

print.print_edge_bottom
print.print_edge_left
print.print_edge_right
print.print_edge_top

DOES NOTHING.

then i go to file-page options-margins & header/footer- 

i setup margins :
top=0.8 inch
bottom=0.8 inch
left=0.5 inch
right=0.5 inch

and my paper size is set as "letter (8,5x11 inch)", though i print on A4. but unfortunately firefox do not print properly on paper A4 when it is on A4. that is paradox for me.

that is all. :)

and i don not understand. why so long ( now we have firefox 2.0.0.13) firefox have such basic stupid mistake. 

by the way if firefox have 
top=0.9 or top=0.7 then it printed page only about 25% of its content. 

and that is not all.

if top position of page intersect  position of header, then top part of page destroy header. and in this case header did not print.

---

