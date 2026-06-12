---
title: "How to fix your slow printer (printing)"
date: 2015-02-07
forum: General Help
---

### Post by poe503 on 2015-02-07
Ever since I upgraded from Ubuntu 8.04, I have been plagued with slow printing/spool crashing on my old parallel port HP printer.  I had searched and could not find a fix.  Upgrading to 14.04 increased the crashing of print jobs.

I fixed the problem simply by removing HPLIP all together.  HPLIP is intended for network printers not older printers.  The writeup for HPLIP says it supports parallel printers.  It does so poorly.  

HPLIP comes already installed in the Ubuntu package.  When you set up your printer you are given the option of either setting the printer up by using HPLIP or as a parallel port printer.  Neither option worked well for me.  Slow printing and crashing occurred using either option.

The Fix  -  First I removed the printer from the System Settings printer utility.  I then went to the Software Center and first looked up the list of installed programs.  HPLIP was not listed.  I used the search window and searched for HPLIP and, sure enough, there it was, listed as installed.  I uninstalled it. 

I reinstalled the printer.  Now there was no choice.  It just set up the printer. 

Now I can print without a hitch, just as it was in 8.04.

Hope this fixes your printing blues.

---

