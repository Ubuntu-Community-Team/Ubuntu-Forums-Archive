---
title: "Need Help Setting Up Printer"
date: 2006-12-01
forum: General Help
---

### Post by jlacroix on 2006-12-01
Hello everyone.

I feel rather silly. I've recompiled kernels, installed software from source, and all that other stuff, but I've never set up a printer before.

We have an Epson Stylus c86 printer and are using Ubuntu Edgy.

We installed the printer via USB and then went into System > Administration > Printers and then clicked "New Printer". Ubuntu detected it just fine.

After rebooting we tried to print a random open office document and Firefox and the printer pulls the paper through, the printer head makes noise as it should and then slides accross the paper like its supposed to.

The paper comes out blank, I have tried both sides of the paper. The ink cartridges are installed as the included install guide said and the ink cartridges are full.

Is there something special I may have to do in order to get it to recognize? Is it needing to be aligned?

---

### Post by ciscosurfer on 2006-12-02
This gives new meaning to "ghostscript".

Sorry, I couldn't resist, and I know that was of no help.

Hmm.  Have you tried printing a test page (from the printer, not from the computer).  Can you print in other OS's like Windows?  Have you recently modified your system in any way?

---

### Post by jlacroix on 2006-12-02
Yeah we tried a printer test page and I have no other OS's.

---

### Post by ciscosurfer on 2006-12-02
I would recommend hooking your printer up to another computer (an extra one lying around, a friends computer maybe) and see if it works there (ideally, a Ubuntified machine).  If it works there, then we know its something with Ubuntu on your machine, otherwise, its the printer that is the culprit.

---

### Post by jlacroix on 2006-12-02
I'll see if I can try that tomorrow, I'll let you know if it fixes it or not. :)

---

### Post by ciscosurfer on 2006-12-02
Okeedokee!

---

### Post by indytim on 2006-12-02
A couple of other options that may apply:

- when you installed the printer, did you have more than one driver to use for your printer?  I know that when I installed my Lexmark E322, I had two different drivers as options....

- I got really messed up in printing (did get output) until I figured out that I wasn't printing in A4 (in the "States")... duh

In the event that this helps.

Good Luck,

IndyTim

---

### Post by jlacroix on 2006-12-02
It is set to A4. So I suppose that's probably not the problem.

---

### Post by ciscosurfer on 2006-12-02
> **jlacroix said:**
> It is set to A4. So I suppose that's probably not the problem.It's a new day.

Any progress?

---

### Post by wpshooter on 2006-12-02
> **indytim said:**
> A couple of other options that may apply:

- when you installed the printer, did you have more than one driver to use for your printer?  I know that when I installed my Lexmark E322, I had two different drivers as options....

- I got really messed up in printing (did get output) until I figured out that I wasn't printing in A4 (in the "States")... duh

In the event that this helps.

Good Luck,

IndyTim

Make sure you try all of the available drivers listed for your particular printer.  I believe the A4 options should be changed to LETTER.

---

### Post by ciscosurfer on 2006-12-02
> **wpshooter said:**
> Make sure you try all of the available drivers listed for your particular printer.  I believe the A4 options should be changed to LETTER.The A4 options are the default.  They work just fine.

---

### Post by wpshooter on 2006-12-02
> **ciscosurfer said:**
> The A4 options are the default.  They work just fine.

I agree A4 is the default, BUT I believe that they should be changed to letter for normal printing purposes.

---

### Post by ciscosurfer on 2006-12-02
I print using A4 format everyday.  I can assure you that this is normal.

---

### Post by wpshooter on 2006-12-03
Can you tell me what A4 format is ?  Everyone I have asked has had no idea as to what this is !!!

---

### Post by steve.horsley on 2006-12-03
A4 is the standatd paper size in Europe, and maybe everywhere except the US. [http://www.cl.cam.ac.uk/~mgk25/iso-paper.html](http://www.cl.cam.ac.uk/~mgk25/iso-paper.html)

I don't mean to be insulting, but are you sure the printer has ink? I had exactly this problem - I installed Linux, the printer went through all the motions but the print came out maroon - no green. I spent hours trying to figure it out and eventually found that the printer had run out out of green just as I changed O/S. Just an inconvenient coincidence.

I don't know that particulat printer, but Epson in general are very well supported in Linux.

---

### Post by wpshooter on 2006-12-03
> **steve.horsley said:**
> A4 is the standatd paper size in Europe, and maybe everywhere except the US. [http://www.cl.cam.ac.uk/~mgk25/iso-paper.html](http://www.cl.cam.ac.uk/~mgk25/iso-paper.html)



That is sort of what I was inclined to think and since I am in good ole USA, that's why I change from A4 to LETTER.

Thanks.

---

### Post by jlacroix on 2006-12-03
The ink cartridges are brand new. I will try a different paper size later.

---

### Post by ciscosurfer on 2006-12-03
> **wpshooter said:**
> That is sort of what I was inclined to think and since I am in good ole USA, that's why I change from A4 to LETTER.

Thanks.I'm in the US and I print using A4 everyday, but whatever.  If Letter suits you better, then use it.

[http://en.wikipedia.org/wiki/A4_paper_size](http://en.wikipedia.org/wiki/A4_paper_size)

---

### Post by indytim on 2006-12-04
I must apologize as I must not have been clear on my original thread posting.  The printer did print with the A4 setting but pagination was messed up due to the A4 setting and printing on US Letter sized paper.  In addition, under those conditions, the printer would drive to an error-mode after each print job.  These conditions went away when I set the printer to US Letter to match with the paper size I am using.  I just wanted to point out my experiences and resolution for the users in the "States".

Sorry for any confusion caused by my posting.

IndyTim

---

