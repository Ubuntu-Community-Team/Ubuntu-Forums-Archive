---
title: "Printin Checks With GNUcash"
date: 2015-09-03
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-09-03
Hello,

I'm trying to figure out how to print checks with GNUcash. Does anyone know how to do this?

Thanks, Hannibal

---

### Post by QDR06VV9 on 2015-09-03
Never used it my self but see if this helps you.
[http://gnucash.org/docs/v2.4/C/gnucash-help/print-check.html](http://gnucash.org/docs/v2.4/C/gnucash-help/print-check.html)
It is muti-paged
Regards

---

### Post by coljohnhannibalsmith on 2015-09-04
Thanks, that was helpful.

---

### Post by bobdodds2 on 2016-06-01
This tells me to use gnucash to print on the check, at the suggested gnucash doc link above, for your convenience again here:
[http://gnucash.org/docs/v2.4/C/gnucash-help/print-check.html](http://gnucash.org/docs/v2.4/C/gnucash-help/print-check.html)

gnucash is going to solve the alignment problem(s). I tried a latex method but don't know latex, it's going to be faster and easier just to follow that tutorial above and use gnucash.

 At the current time, the gnucash package installs a gnucash which crashes on load. That's an easy google to fix, certainly temporary.

The check itself I have learned to print using FreeCheck, newest version on github now under new maintainer, Caleb:
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]FreeCheck is written by:
[/TD]
                                [TD="class: blob-code blob-code-inner js-file-line"] 
[/TD]
                                [TD="class: blob-code blob-code-inner js-file-line"]	Eric Sandeen <sandeen-freecheck@sandeen.net>
[/TD]
                                [TD="class: blob-code blob-code-inner js-file-line"]	James Klicman <james@klicman.org>[/TD]
                                [TD="class: blob-code blob-code-inner js-file-line"]	Caleb Maclennana <caleb@alerque.com>[/TD]
[/TR]
[/TABLE]
[https://github.com/alerque/freecheck](https://github.com/alerque/freecheck)
[http://www.home.unix-ag.org/simon/penguin/](http://www.home.unix-ag.org/simon/penguin/)
Older, original project here:
[http://www.sandeen.net/freecheck](http://www.sandeen.net/freecheck) # Eric Sandeen original author.

Just putting the GnuMICR font in my ~/.fonts was not enough. I also put it into the /usr/share dirs for ps and ghostscript.

 Here's my ~/.freecheck.cfg profile to use Office Depot "P 8000" Personal Wallet check blanks:

[CheckBlank ODP8000]
# Office Depot P 8000 Personal Wallet Check Refills
# CheckHeight == (PageHeight - CheckVerOffset) / ChecksPerPage
#             % calculated in points avoid rounding error
#             == 11 inch 2.5 inch sub 3 div
#             == 204
CheckHeight            = 210
CheckWidth             = 5.90 inch
CheckHorOffset         = 2.50 inch
CheckVerOffset         = 2.50 inch
ChecksPerPage          = 3
LeftMargin             = 0.125 inch
RightMargin            = 0.25 inch
TopMargin              = 0.38 inch

So a command line looks like this:
```

 freecheck --account me --checkstyle Normal --checktype ODP8000 | ps2pdf - me.pdf # to pdf file
 freecheck --account me --checkstyle Normal --checktype ODP8000  1400 | lpr           # through ghostscript--you may have to install freecheck's GnuMICR font to gs and ps

```

I am on my way to a couple of banks to try checks today, without magnetic toner for GnuMICR, at clerk windows and atm's. I also am trying 600 dpi inkjet, not laser! Canon scanner/printer.

Very important: I editted Sandeen's penguin logo to add my website. Penguin just keeps pooping money into "PAY TO THE ORDER OF", as if.

---

### Post by bobdodds2 on 2016-06-01
If gnucash is crashing on open:

```

#!/bin/bash

sudo apt-get purge gnucash
sudo apt-get autoremove

# ubuntu's alt to getdeb, 
sudo add-apt-repository ppa:micha/libaqbanking

sudo apt-get update
sudo apt-get install gnucash

```

---

