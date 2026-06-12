---
title: "Print to Windows printer"
date: 2005-10-31
forum: General Help
---

### Post by soulcoughy on 2005-10-31
My situation:

I have an inkjet that's unsupported in linux (lexmark x5250).  I have a windows machine I can hook it up to and share via samba.  Is there any way I can convince the linux box to print to the windows box?  Is there some sort of program that can run on the windows box and translate the postscript put out by linux to the printer?  I'm not too familiar with the workings of such things....Is it possible?

Thanks

-Brian

---

### Post by eternal0void on 2005-11-01
[QUOTE=soulcoughy]My situation:

I have an inkjet that's unsupported in linux (lexmark x5250).  I have a windows machine I can hook it up to and share via samba.  Is there any way I can convince the linux box to print to the windows box?  Is there some sort of program that can run on the windows box and translate the postscript put out by linux to the printer?  I'm not too familiar with the workings of such things....Is it possible?

Thanks

-Brian[/QUOTE]
You may have to obtain a Linux-compatible printer for this to work, but I found this [link ](http://www.faqs.org/docs/Linux-mini/Debian-and-Windows-Shared-Printing.html#printing_to_windows) to a site which covers setting up various things including printing on Debian systems.  Since Ubuntu is based on Debian it probably will work for you.

The problem with Lexmark is that they usually use some form of software processing for anything printed to them.  This requires that you have drivers installed on the remote machine for the Lexmark printer on the Windows machine.  No drivers--actually more like "additional printer software"--equals no access to the printer.  Lexmark is much-avoided by Linux users for this reason.  

I've been told that HP is a much better choice for finding a Linux-compatible printer.  

Personally I chickened out and went to a thrift store, where I purchased a very old but working Canon BJ-200ex, and installed it via CUPS directly to my Linux computer.  Since the Canon BJ-200ex requires no special OS-specific drivers to run, I can share it out to Windows PCs on my network as well.  Sadly, Canon hasn't learned anything from Lexmark and also produces low-end printers which are incompatible with Linux for the same reasons that Lexmark printers are incompatible with Linux.

I long for the old days in which there was a "compatibility mode" on some printers.  This was usually to provide support for older DOS applications which couldn't be upgraded to use the current drivers for the new printer.  For example, about seven years ago I had a color HP printer which had a B&W compatibility mode with older DOS applications.  Such a compatibility mode would make it possible to print directly to the printer instead of having to go through layers of printer software.

---

