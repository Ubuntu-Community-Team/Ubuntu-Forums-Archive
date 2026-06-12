---
title: "Windows Printer Share to Ubuntu"
date: 2007-02-22
forum: General Help
---

### Post by gejr on 2007-02-22
I have a windows machine with a HP Deskjet 3745 shared on my network. I've went to add printers, I found the printer, I entered the proper username/password for the guest account on my winXP machine, and tried to print a page. The print job appears on the XP machine as:

 "Remote Downlevel Document" with 
"Owner: Guest" and 
"Pages: N/A"

All good (I hope), the printer starts making some sounds and everything seems right, until it suddenly stops. No more sounds, no nothing. And then the print job just hangs there and can't be canceled unless i do some service hacking in windows.

Can anyone help me pinpoint something that'll make me able to print this way?

---

### Post by netkid91 on 2007-02-22
> **gejr said:**
> I have a windows machine with a HP Deskjet 3745 shared on my network. I've went to add printers, I found the printer, I entered the proper username/password for the guest account on my winXP machine, and tried to print a page. The print job appears on the XP machine as:

 "Remote Downlevel Document" with 
"Owner: Guest" and 
"Pages: N/A"

All good (I hope), the printer starts making some sounds and everything seems right, until it suddenly stops. No more sounds, no nothing. And then the print job just hangs there and can't be canceled unless i do some service hacking in windows.

Can anyone help me pinpoint something that'll make me able to print this way?
You sure you used the right driver on the Ubuntu side?

---

### Post by gejr on 2007-02-22
No, I have a HP deskjet 3745 and the printer installer suggested/recommended the driver hpijs for HP Deskjet 3740. Do you think that could be the reason?

---

### Post by netkid91 on 2007-02-22
Possibly, what other options does it give?  Try Gutenprint if it's available.

---

### Post by gejr on 2007-02-22
I will try that. I just did an apt-get install hpijs and hpijs-ppds. Obviously they weren't already installed. Might mean I've done something right now. I'll get back to you :)

---

### Post by gejr on 2007-02-22
It didn't work. Gutenberg High Quality image was available for the printer below. I think it was Deskjet 3810. I tried it, but it didn't work either. Weird that 3745 isn't listed. Only 3740.

---

### Post by netkid91 on 2007-02-22
Just read up on your printer, I'd recommend trying the HPLIP driver next (the 3745 is similar to the 3740, which is why it isn't listed).  I'm not sure what else could be the issue.

---

