---
title: "[SOLVED] Setting up printers in Gutsy"
date: 2007-10-26
forum: General Help
---

### Post by speed145a on 2007-10-26
Is it just me, or is it much more difficult to setup printers in gutsy?  In feisty I was pleased to see it automatically detected my network printer and setup was through a wizard that made sense.

Now, I get some difficult dialog that talks about connecting to server (talking about my CUPS server?) and then I get some weird list on the left after clicking on "new" and I don't feel like the list really makes sense (let alone finding the printer that is connected through USB)

If anyone could shed some light on how to make sense of it all that would be amazing!!

---

### Post by Unicycle on 2007-10-27
I did a fresh install of Gutsy, and my printer was recognized immediately through using the wizard.  No real "configuration" needed, I just selected it...

---

### Post by tech9 on 2007-10-30
> **speed145a said:**
> Is it just me, or is it much more difficult to setup printers in gutsy?  In feisty I was pleased to see it automatically detected my network printer and setup was through a wizard that made sense.

Now, I get some difficult dialog that talks about connecting to server (talking about my CUPS server?) and then I get some weird list on the left after clicking on "new" and I don't feel like the list really makes sense (let alone finding the printer that is connected through USB)

If anyone could shed some light on how to make sense of it all that would be amazing!!

no it's not just you... it is a little more complicated

---

### Post by tech9 on 2007-10-30
> **speed145a said:**
> Is it just me, or is it much more difficult to setup printers in gutsy?  In feisty I was pleased to see it automatically detected my network printer and setup was through a wizard that made sense.

Now, I get some difficult dialog that talks about connecting to server (talking about my CUPS server?) and then I get some weird list on the left after clicking on "new" and I don't feel like the list really makes sense (let alone finding the printer that is connected through USB)

If anyone could shed some light on how to make sense of it all that would be amazing!!

I am not sure about printers connected via USB. Does your printer have a built-in NIC - you could always print to it via IP address. All my printers are networked and work just fine.

---

### Post by speed145a on 2007-10-31
I think I got it figured out!  My firewall was blocking the connections because I had the default to "drop" everything unless I allow it.  It was blocking the connection to my network printer.  I hate it when I bang my head against a firewall  :-)

After I fixed this problem I found that the printer actually did appear in that long list on the left of the "wizard"
Still not too sure about the usb thing but I'll look at that some other time.

Setting up a printer still seems somewhat more complex than in Feisty, but I'm sure there is added functionality.  But at least I can figure out what is going on now that my printer actually shows up in the list.

thanks

---

