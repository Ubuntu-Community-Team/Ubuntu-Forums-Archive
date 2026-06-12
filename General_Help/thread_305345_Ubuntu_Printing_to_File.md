---
title: "Ubuntu Printing to File"
date: 2006-11-23
forum: General Help
---

### Post by rhofmeyr on 2006-11-23
Hi all,

I'm trying to print documents from the command line. I don't have any printers installed and hence no default printer. I do however, when I go to print on a document, have a generic postscript printer...

How do I access this printer from the command line? It isn't listed under Adminstration -> Printing. Also what would I use to force it to print to file from the command line?

Any help would be greatly appreciated.

Thank you,
Robert

---

### Post by rhofmeyr on 2006-11-23
Can no Linux guru shed any light on this?

---

### Post by geoff1941 on 2006-12-16
Hi everybody,
I have a similar problem as rhofmeyr I can print ok from gnome ,firefox or evolution. In my case I print to my local printer which is a HP PSC 2110. However, if I try to print from the command line using lpr or from emacs my local printer is not found?   emacs shows spooling done but the printer is not activated. Looking on (Edgy 6.10) system, adminisration, printing my local printer is shown ready. I notice when I press the print icon in  evolution it shows a window with the following Create a PDF document, Generic Postscript, PSC-2110 ready. The Generic Postscript is highlighted , also shows the lpr command in another box. I have to click the PSC-2110 to highlight it before I print? It seems that the system highlights Generic Postscript as default which does not regcognise my local printer. I have looked through my Official Ubuntu  Book and a PracticlaI Guide to Linux but I am not able to find a solution! I would appreciate any pointer on how to proceed. Thanks to anyone who replies

---

### Post by greenwhale on 2007-09-06
Hi,

geoff1941's problem might be that the wrong lpr-tools are installed. emacs and other programs do not print nativly to cups but use lpr. There are two packages that provide these commands: 'lpr' for bsd-style lpd (alternative to cups) and 'cupsys-bsd'.

'cupsys-bsd' is needed to print from commandline to cups.

---

### Post by geraldm on 2007-09-06
rhofmeyr:
Does "generic postscript printer" mean winprinter?
What make, model printer?

---

### Post by bogolisk on 2007-09-06
to see the configured printer(s):
```
sudo cat /etc/cups/printers.conf
```

If there was a
```

<DefaultPrinter Foo-Bar-1234>

```
Then Foo-Bar-1234 is the default printer, otherwise there's no default printer.

to see status of the printers:
```

lpstat -a

```

It's is *highly recommended* to install the cups-pdf package. If you print to that printer, it will create a PDF file in the **~/PDF/** directory.


hope it helps

---

