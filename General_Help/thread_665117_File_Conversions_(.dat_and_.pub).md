---
title: "File Conversions (.dat and .pub)"
date: 2008-01-11
forum: General Help
---

### Post by rykel on 2008-01-11
Hi,

**.dat**
In Windows, I use a program called SUPER from eRightSoft to convert .dat (ie. VCD) files to .mpg ones.

Do you know how I can do the same in Ubuntu Gutsy?

I tried running SUPER in WINE, but the GUI was all messed up.

**.pub**
Is there a way to read and/or edit .pub (ie. Microsoft Publisher) files in Ubuntu Gutsy?

Thanks for the advice!

---

### Post by rykel on 2008-01-12
Hi,

I found that **VCDGear** does the job of converting .dat to .mpg very well and fast too - faster than SUPER on Windows.

Simply go to **[http://www.vcdgear.com](http://www.vcdgear.com)**, download the Linux tar.gz file to your Home, untar (unzip) it by right-clicking it and "Extract To..." and then running the program from its folder in Terminal. A sample usage is given below:

[INDENT]**~/vcdgear$ ./vcdgear -dat2mpg ~/movie.dat ~/movie.mpg**[/INDENT]

If you know of any GUI for vcdgear please let me know.

Now to dealing with the pesky **.pub** files... any ideas yet?

---

### Post by isparkes on 2008-02-21
Thanks for that! Great bit of info.

I have used this with success converting .cue/.bin files to .mpg. It didn't work if I extracted the .dat file out if the .bin file.

I did:

ian@ian-desktop:~/Desktop/vcdgear$ ./vcdgear -cue2mpg d1.cue dis2.mpg

This picked up the right block size (2352) from the cue file, and gave a good quality output.

---

