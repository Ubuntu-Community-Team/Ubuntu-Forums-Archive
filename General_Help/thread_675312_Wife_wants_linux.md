---
title: "Wife wants linux"
date: 2008-01-22
forum: General Help
---

### Post by BobLand on 2008-01-22
Convinced her to switch to OpenOffice on XP.  She loves it and wont use MS anything anymore.  Now she wants to bite the bullet and get off XP.  Since Gutsy seems to be pretty stable, I'm willing to put it on her machine.

However, she must have a QuickBooks clone.  Can anyone suggest one?  Importing data is not too important but reliability is.

I was reluctant to put her on feisty because of the troubles I was having with it but they have all gone away with gutsy.

Thanks,
bobland

---

### Post by nemilar on 2008-01-22
Your options are probably one of:

[http://kmymoney2.sourceforge.net/index-home.html]("http://kmymoney2.sourceforge.net/index-home.html")
[http://www.gnucash.org/]("http://www.gnucash.org/")

Or for something even more robust:
[http://www.sql-ledger.org/cgi-bin/nav.pl?page=about.html&title=About]("http://www.sql-ledger.org/cgi-bin/nav.pl?page=about.html&title=About")

However, many people say that the lack of a Quickbooks-clone is one Linux's pitfalls, so I'd try them out and see if they do what you need, before you commit yourself to the switch.

---

### Post by Tanjer1588 on 2008-01-22
If you have the space for it just use dual boot for now. Theres a lot of things we need clones for on Linux but there are just some things we have to have windows for. So if you have the space on your hard drive just stay with a dual boot and have the best of both worlds.

---

### Post by cdaringe on 2008-01-22
what version of quickbooks does she use?
I checked the wine website and it seems people were still having a little bit of trouble getting it to run on their linux boxes.  but there have been a few updates i believe since they tried...so its worth giving it an install via wine and seeing what happens.
what a suprise that she loved OO significantly more than MSOffice!  man, im not even sure if im there yet. maybe someday...

---

### Post by wolfen69 on 2008-01-22
the good thing about gnucash is you can import your .qif backup files from quickbooks.

---

### Post by bodhi.zazen on 2008-01-22
Another option is to run quickbooks in VMWare or Virtualbox. You can migrate to an alternate if you find one.

---

### Post by rosegarden78 on 2008-01-22
1) install wine from repositories.
2) if windows is NTFS format you need to use FUSE or ntfs-3g to mount it.  That way you don't have to copy the files twice on the same computer.

By the way you're dual booting right?  No need to throw away a decent operating system.

3) If the Windows is in FAT32 it should be mounted automatically on Desktop or /media folder or /mnt folder.

Stay with me.  

4) Navigate to your Windows drive with file manager Nautilus or Konqueror.
5) Go to Program Files / Common File on Windows
6) Send this folder as a link to your Wine directory. /home/user/.wine/windows/Program\ Files/

That should do it!  I run Windows software on Ubuntu this way.  If you don't send a symbolic link to Common Files WINE won't know where to look to load your Windows drivers.  Now you can create a launcher on your desktop.

wine /media/sda1/Program\ Files/Path\ to\ Application/YourApplication.exe just don't forget to delimit spaces in filenames with a backslash

---

### Post by BobLand on 2008-01-22
Wife HATES quickbooks.  She has to use it to maintain items for 2 different organizations.  In all cases, she can change to a different program.  QB came as legacy.

I'll look into the other suggestions.

Thanks,
bobland

---

### Post by p_quarles on 2008-01-22
> **wolfen69 said:**
> the good thing about gnucash is you can import your .qif backup files from quickbooks.
Another good thing is that it's available for Windows. The OP can easily give it a test drive without finalizing the switch. And I agree: it's an all aorund solid bookkeeping app.

---

