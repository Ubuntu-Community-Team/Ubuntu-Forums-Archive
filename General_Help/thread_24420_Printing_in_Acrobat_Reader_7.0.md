---
title: "Printing in Acrobat Reader 7.0"
date: 2005-04-06
forum: General Help
---

### Post by dilerra on 2005-04-06
Installed Acrobat Reader 7.0 and have tried some documents for printing. Now it turns out that not all documents are printed! If I try to print (using the standard "lpr" command) certain documents, it "seems" like they go to the printer (it blinks) but then it stops and nothing comes out. Tried the same document in GPDF and viola - it worked. Can someone enlighten me on this one? Maybe I need to use another alternative as my print command in Acrobat Reader?

Thanks / Matthew

---

### Post by soul_rebel on 2005-04-07
It's better to ask support for open source apps only. The linux community is not working for adobe for free. Try using gpdf or kpdf. At least for printing.

---

### Post by gbil on 2005-04-07
> It's better to ask support for open source apps only. The linux community is not working for adobe for free. Try using gpdf or kpdf. At least for printing.

If you can't answer you better not. He is not starting a debate here he just wants an answer.

> Adopt an unanswered post!
I really like your signature. Is this your way of answering unaswered posts? I hope not.


> Installed Acrobat Reader 7.0 and have tried some documents for printing. Now it turns out that not all documents are printed! If I try to print (using the standard "lpr" command) certain documents, it "seems" like they go to the printer (it blinks) but then it stops and nothing comes out. Tried the same document in GPDF and viola - it worked. Can someone enlighten me on this one? Maybe I need to use another alternative as my print command in Acrobat Reader?

Back to the real problem now. In my system the default command for printing in Acrobat 7 is /usr/bin/lp and not /usr/bin/lpr and it works fine. Can you try that and tell us?

---

### Post by soul_rebel on 2005-04-07
I had the feeling dilerra is a new linux user, so I thought it was good to tell him why there is community support for open source apps and usually there is no community support for closed source apps, because we don't get anything back for that.
I think that closed source software related questions should be asked to the vendor.

Anyway i have read this post because i had a similar problem and I gave that answer because I simply started using gpdf as my main pdf app.

If you check my comments you will find that I answer the best I can, sometimes being very informative; but sometimes I just give a small and not definitive answer to posts getting old  I want to put back the first page for a while.

---

### Post by Leif on 2005-04-07
I really can't shed any light on this one, my solution is to reset the printer - and remove and resend jobs, of course. Crude, but seems to work.

---

### Post by dilerra on 2005-04-08
Hi everyone,

I will remember what you've said about open source. Unfortunately, I'm more or less forced to use Acrobat due to some limitations of gpdf and xpdf, it's not that I'd like Adobe better.

Whatever, tried both /usr/bin/lp and /usr/bin/lpr without success. The strange thing is that only some documents behave this bad...

Thanks for the help anyway!

/ Matthew

---

### Post by felix.rommel on 2005-04-13
The same problem appears in my Hoary installation. I tried the following Adobe Reader 7.0 packages:

- tar.gz
- rpm with Alien
- deb from Marillat

but none of them worked. Reader do not print anything. Even if I print into an post script file and want to open it with ggv it says that it's no valid postscript format. Seems as Reader cannot produce valid postscript under Hoary!?

I installed Adobe Reader 7 fine under SUSE 9.2 and there it prints without any problems.

Maybe there is a problem with the lp/lpr commands under Hoary?

I also tried it with gtklp - which is a very nice Gnome printing GUI - but even with this nothing happens. The job is send to the printer but it is not printed.

My printer works cause I can also print with the other Gnome apps.

I need Adobe Reader because I want to fill out forms with it.

Has anyone an idea?

---

### Post by felix.rommel on 2005-04-13
I found a solution:

I deleted the directory

**.adobe**

in my home directory. After that I removed the installed Adobe Reader 7.0 packages and chosed instead these packages:

[http://xn.pinkhamster.net/blog/tech/acroread_7_for_linux.html](http://xn.pinkhamster.net/blog/tech/acroread_7_for_linux.html)

I'm not sure if it was the fault of not removing the .adobe directory from my previous SUSE 9.2 installation, but the packages worked for me.

Nevertheless the problem is solved. :)

---

### Post by linuxchemist on 2006-07-09
> **dilerra said:**
> Installed Acrobat Reader 7.0 and have tried some documents for printing. Now it turns out that not all documents are printed! If I try to print (using the standard "lpr" command) certain documents, it "seems" like they go to the printer (it blinks) but then it stops and nothing comes out. Tried the same document in GPDF and viola - it worked. Can someone enlighten me on this one? Maybe I need to use another alternative as my print command in Acrobat Reader?

Thanks / Matthew

In Acrobat Reader change printing command from **/usr/bin/lp** to **lpr -PYourPrinterName **
Look in setting how your printer is recognized
For example I have printer HP PSC-1600 series and it's cup is PSC-1600.
When I changed **/usr/bin/lp** to **lpr -PPSC-1600** my printer has started to print.

---

### Post by saltydog on 2006-07-17
I have also tried to change /usr/bin/lp to lpr -PPrinterName, but this problem still exists: everything works (prints) if I print ALL the document. If I try to print a subset (few pages, odd or even pages) the print job is sent to the printer and then it is "stopped" and never prints... :(

---

### Post by tubunu on 2006-07-25
Hey thanks, it worked with my printer, HP DeskJet 710C!

I changed **/usr/bin/lp** to **/usr/bin/lpr -PHPDeskJet710C**

:)

---

### Post by randcoop on 2006-07-25
lpr -P[printername] worked for me and it worked even when printing only odd or even pages.  So people should definitely give it a try.

---

### Post by gabba on 2006-08-05
I wonder if Adobe Reader is sending the correct command to the printer. For all of you who had problems, did /usr/bin/lp work from the command line? Trying to save your pdf from Acrobat Reader and print it from the command line with:

$ /usr/bin/lp test.pdf

or

$ lp test.pdf

Anyways, it works for me now, even in Acrobat. Does using it once from the command line help it to work??

For those who are using the HPLIP driver and have correctly set it up (google "ubuntu hplip"), and want to get a dialog box with more options when you print, you can also use the following command as a replacement for /usr/bin/lp:

hp-print -dhp:/usb/photosmart_7150?serial=MY2CI463F42F

Replace the adress after the -d with the URI of your own printer, obtained with the command:

$ hp-options

Hope this helps someone.

---

### Post by mhamilton on 2006-08-07
If you find that **/usr/bin/lpr -P<printer>** works for you, then you may want to set your default printer.

To do this, choose System|Administration|Printing, and then choose "Make Default" on the context menu (right-click menu) on the printer that you would like to make the default printer. Then /usr/bin/lp should work on its own.

---

### Post by desicrew on 2006-08-07
I was having the same problems with printing through Adobe....but once I assigned my printer as the default through System->Administration->Printing Adobe picked up automatically and printed it.  Also: I had usr/bin/lp in the printer command textbox....

---

### Post by lukketto on 2006-08-19
> **randcoop said:**
> lpr -P[printername] worked for me and it worked even when printing only odd or even pages.  So people should definitely give it a try.
Even for me...it works!

---

