---
title: "Unable to unzip .exe bios file"
date: 2007-10-25
forum: General Help
---

### Post by mandz on 2007-10-25
Hi All,

I'm following the  HOWTO: Flash BIOS, The Ubuntu Way. I'm fine with the whole process apart from I can't extract the necessary files from the D600_A16.EXE file. It unzip with the unzip command in terminal. I get this:

"End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive."

Is there any other way to extract the bios flash programme and rom file? I know Dell provides a method with SMBIOS or whatever its called but it doesn't work for me getSystemId gives no output for me.

The bios file I need to extract from can be found below:

[http://support.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=us&l=en&s=gen&~mode=popup&file=133834](http://support.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=us&l=en&s=gen&~mode=popup&file=133834)

I've looked at other related threads but cabextract doesn't work and wine just loads the exe file. So maybe its not extractable after all....

If anyone knows how to extract the files and would be kind enough to do so and send them to me that would be magic! Otherwise simple, plain advice would be great to :-)

Cheers.

Oh and I've got a Dell D600... any other info you need please let me know.

---

### Post by kellemes on 2007-10-25
You can't extract an .exe.. it's an Windows-executable.
Can you post a link to the **HOWTO: Flash BIOS, The Ubuntu Way**?
Maybe we can help you better if we can look at it.

---

### Post by mandz on 2007-10-25
Thanks.

[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

---

### Post by kellemes on 2007-10-25
Yes, I just found it myself..
I can't help you here actually.. just being honest. :popcorn:
The howto actually explains **Unzipping the .EXE** and I'm surprised at least..

Anyone else?

---

### Post by mandz on 2007-10-25
Yes pleeeease heeeeeeelp! I've only been spending all day on it. A chance for someone to make my day and do a Good Deed :-)

---

### Post by mandz on 2007-10-25
and thanks kellemes for trying :)

---

### Post by Fruhwirth on 2007-10-25
I'm getting the same error you are using the *unzip xxx.exe* command.

> End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of driver.exe or
        driver.exe.zip, and cannot find driver.exe.ZIP, period.

I hate how it's an error with attitude, spelling out the word "period" at the end for extra snotty emphasis.

Anyway, I'm following [**this HOWTO**]("http://ubuntuforums.org/showthread.php?t=563547") and feel like an idiot.  After 3 weeks and 15 pages of questions and comments on the HOWTO, no one has run into this "end-of-central-director signature" error.  I'm trying to open [**this file**]("http://www.ralinktech.com/ralink/Home/Support/Windows.html") found second-from-the-last on[ **this page**]("http://www.ralinktech.com/ralink/Home/Support/Windows.html").

Have all three items installed that are listed on[** this page.**]("http://packages.ubuntu.com/dapper/utils/unzip") 

I'm using Gutsy 64 if it matters.

---

### Post by kellemes on 2007-10-26
Thought about it a little..
Could it be it's just a compressed exe? Like a Zip.. or a Cab?
Maybe you should see if your system supports the extraction of Zip or Cab, and if not.. install the needed packages to get it..
Hope this helps.

---

### Post by Fruhwirth on 2007-10-26
kellemes, thanks for trying to help. Are you able to be a lot more specific?

> 
Could it be it's just a compressed exe? Like a Zip.. or a Cab?
How would I know this?  How can I find out whether this particular .exe file is "just a compressed exe" as you say?  And so what if it is? I don't know exactly how that info helps me. According to this [HOWTO]("http://ubuntuforums.org/showthread.php?t=563547") I'm following, there is a .inf, .cab and other files *inside* the .exe  that I desperately need.

> Maybe you should see if your system supports the extraction of Zip or Cab
How do I do that?  I have archive manager installed and it functions correctly with zip files.  Is that what you're talking about?

>  and if not.. install the needed packages to get it..
What are those needed packages? As i said before, I have all  three items installed that are listed on [this page]("http://packages.ubuntu.com/dapper/utils/unzip"), as well as archive manager and whatever dependencies are necessary to make that function correctly.

---

### Post by Fruhwirth on 2007-10-27
I tried to use Wine, which opened the file and began the install wizard as if I was in Windows. It threw an error after many machinations, which I guess one would expect. 

It placed a bunch of promising-looking files in the home/.wine/drive_c/Program Files/RALINK/Common directory but there is no .inf file, which is what I'm after!  

Anyone got a better place to look or know what I'm doing wrong?

Again, I need to crack open the exe and find the .inf, .cat, and .sys driver files for my wireless card per [this HOWTO]("http://ubuntuforums.org/showthread.php?t=564419").

---

### Post by kellemes on 2007-10-27
Well, I downloaded the exe myself and struggled with it without success. :(
It is not extractable it seems.. I tried just about a million ways.. :)
Are you sure it's the right file for the motherboard?

---

### Post by Fruhwirth on 2007-10-27
Thanks kellemes.  I'm about to give up on this whole thing, though doing so means giving up either on Gutsy with wireless, or giving up Gutsy and going back to dapper but at least having wireless.  Sad sad sad saturday.

---

### Post by kellemes on 2007-10-27
> **Fruhwirth said:**
> Thanks kellemes.  I'm about to give up on this whole thing, though doing so means giving up either on Gutsy with wireless, or giving up Gutsy and going back to dapper but at least having wireless.  Sad sad sad saturday.

Can you please give me the details of your wireless card?
Maybe I'm stupid but.. You're trying to unzip an exe that flashes BIOS.. shouldn't you get the wireless-driver instead?

---

### Post by Fruhwirth on 2007-10-27
The person who started this thread was trying to flash bios but was unable to unzip an exe file that a HOWTO told him he needed to do.

I also had a (different) HOWTO tell me to use the *unzip xxx.exe* command and it didn't work for me either. The original poster and I were getting idential errors (no signature file, or whatever) with different .exe files. 

But don't worry about it. I'm alread back on Dapper and my wireless is already working.  I wasted virtually every moment of free time for 9 days on Gutsy for something that takes only 1 hour in Dapper to configure and work.  And almost all of that hour is just downloading the updates!

I repeat: sad, sad, saturday. But, my issue is resolved, even if it took 16-month-old Dapper to do it.

---

### Post by kellemes on 2007-10-27
> **Fruhwirth said:**
> The person who started this thread was trying to flash bios but was unable to unzip an exe file that a HOWTO told him he needed to do.

I also had a (different) HOWTO tell me to use the *unzip xxx.exe* command and it didn't work for me either. The original poster and I were getting idential errors (no signature file, or whatever) with different .exe files. 

But don't worry about it. I'm alread back on Dapper and my wireless is already working.  I wasted virtually every moment of free time for 9 days on Gutsy for something that takes only 1 hour in Dapper to configure and work.  And almost all of that hour is just downloading the updates!

I repeat: sad, sad, saturday. But, my issue is resolved, even if it took 16-month-old Dapper to do it.

O yeah, was confused for a minute.. :confused:
Well, sorry I couldn't help..

---

