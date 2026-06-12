---
title: "Convert .txt files to .pdb"
date: 2008-02-03
forum: General Help
---

### Post by Teasdale on 2008-02-03
I installed jpilot and it syncs with my Palm TX. But I need to read large files on the TX. The program I was using requires that files be converted to .pdb first, but the converter only works in Windows. I'm unable to install any new programs on my TX - when I tried to install CardTXT with jpilot, it killed jpilot. I had to uninstall and reinstall it.

So what I'm left with is finding a way to convert my .txt files to .pdb in Ubuntu (I still have the .pdb reader on my TX). I tried OpenOffice Word and there's no option there to save files as .pdb.


I did a search and found this thread:
[http://ubuntuforums.org/showthread.php?t=186542](http://ubuntuforums.org/showthread.php?t=186542)

One post says, 

----------------------------

You might want to look at pyrite publisher. It's flexible palmdoc creator that reads text, HTML and other formats. I've used it for years to transfer text to my handheld. I don't have a lot of experience converting material from HTML, so YMMV.

apt-get install pyrite-publisher
pyrpub file.txt
pilot-xfer -i file.pdb

done!

--------------------------------

I did this part:
sudo apt-get install pyrite-publisher

and it seems to have installed.

I tried 
sudo pyrpub file.txt
sudo pilot-xfer -i file.pdb

but it couldn't find those.

So I tried
sudo apt-get install pyrpub file.txt
sudo apt-get install pilot-xfer -i file.pdb

and that doesn't seem to work, either.

I also can't find the Pyrite Publisher program that was installed. When I type pyrite-publisher, it says "not found," and I don't see it listed in any of my programs.

---

### Post by gpilkay on 2008-02-03
OpenOffice can, it's just well hidden.  Go to save as, then, where it gives your format, scroll down or up till you get to Aportis Doc which is also Palm and .pdb.  Don't ask me why it's listed like that, though...

---

### Post by Teasdale on 2008-02-04
I've scrolled and I'm not seeing anything called Aportis in the "save as" options.

---

### Post by bmt on 2008-05-05
You may have already found it, but in case someone comes looking later ...

You need to install (with Synaptic/apt/whatever) the openoffice.org-filter-mobiledev package, too.

---

### Post by Bruce M. on 2008-05-18
> **Teasdale said:**
> I installed jpilot and it syncs with my Palm TX. But I need to read large files on the TX. The program I was using requires that files be converted to .pdb first, but the converter only works in Windows. I'm unable to install any new programs on my TX - when I tried to install CardTXT with jpilot, it killed jpilot. I had to uninstall and reinstall it.

WoW!  I've been using CardTXT for a long time now and jpilot works fine with it. Mind you I didn't "install" it with jpilot, that was during my other OS days.

Another program you might want to look at is a commercial program called [CardReader]("http://www.mobile-stream.com/index.html"). ( $11.95 )

With that it's like plugging in a USB Stick. You can copy everything on the SD card to your HD or copy stuff that "can't normally be synced" (like .TXT files) to the SD card.

It's another way of getting CardTXT back on your Palm.

Have a nice day.
Bruce

---

