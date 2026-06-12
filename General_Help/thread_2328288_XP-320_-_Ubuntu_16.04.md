---
title: "XP-320 - Ubuntu 16.04"
date: 2016-06-19
forum: General Help
---

### Post by oldefoxx on 2016-06-19
I am also trying to get a multi-function unit working under Ubuntu 16.04 LTS.  I refer to it as a "unit" or "device", while most people refer to it as a "printer", as that is its primary function.  The other function is scanner, and when you combine both actions together, you get a copier.

When I went shopping, I went for lowest cost.  That is usually a toss-up between Epson and Brother.  There was a recent sale where a Canon printer was cheaper (half price), but I could not take advantage of it.  My searches led me to Epson Expression XP-330 and EpsonExpression XP-320. and the difference in price was $5.  To me, the XP-320 was the better buy, as it uses 4 cartridges, not 2 as the XP-330 does (a tri-color cartridge printer becomes more expensve as you have to replace or refill the whole cartridge of 3 colors when one runs out.  Yellow runs out first, as it has to mix with cyan and/or magenta to make your reds, greens, blues, purples, and other colors, plus it has to double-shoot itself for strong yellows).

I bought the printer knowing from some research that Epson printers can work with Linux, and there were at least 2 approaches for getting this done.  But I did not get into the details involved at the time.  Now I need those details, and it is a hard search to find them.

First, I don't see the Epson XP-320 on my PC, and I am not aware of where it should show up.  Under Places/Computer (I am using Metacity interface), I see these new devices:

Epson Storage
Generic-Compact Flash
Generic-MS/MS-Pro
Generic-SD/MMC
Generic-SD/XD-Picture

Only the first indicates Epson, but it is unknown.  The other four are also unknown, but might relate instead to a smarkcard slot or the USB-attached webcam.

Checking with Epson on-line support, they do not provide drivers for Linux and act like they never will.  They were no help at all except to suggest an old SCSI link that is meaningless.  

Now the reality is, Microsoft is blowing it big time, its code is insecure and is way out of date, and with Linux on the top end and Google's Android at the low end, there is no real future for costly PC or mobile software.  Microsoft is dying on the vine, but old mindsets can't get that picture straight in their head.  In fact, for many people, PCs are overkill now, they prefer their mobile devices for day to day things, and the PCs and laptops dryrot someplace in the home or garage until they sell them or give them away.

In reality, you only need one good operating system that gives you what you want or need.  If you want to play Window's games, you either add wine or crossover or another emulator to Linux, or you install Oracle VM Virtualbox and add some 32-bit or 64-bit version of Windows as a client.  Or you use multi-boot options or just stick with Windows despite it being so bad at its core.

Believe me, I've tangled with Windows for over a decade as a trained and working professional, and know how vulnerable it is.  But even I was unprepared for the rapidity in which a new Win7 install's safequards were bypassed in under an hour, behind a secured router as well.

I had Microsoft's own tech support in my laptop remotely and watched him work, and it was so bad he told me he had to pass the matter on to a crisis management team to see if they could clean it up, and that would only cost me $247 for one year of checkups and cleanups, always after the fact.  No way man, I went back to Ubuntu 16.04 LTS which is very secure, very powerful, up to date, and always free.

On the surface, the Win7 experience looked fine.  Underneath, it was a different story.  Available protection software was added as I went along, and only reported 24 Registry issues, which were fixed.  Then another 15 were detected, and I would have to subscribe for a year to get those resolved.

That is when I let MS's tech support in remotely for only a marked-down price of $19.95.  He knew exactly where and how to look too, so it must be an ongoing problem.  But what got him, and me, was a hacker was into the laptop at the same tme watching him work.  He could see that, but could not stop it.  That is when he said he was going to have to turn it over to crisis management.  To me, Windows is dead already.  I'm out of that game, though with Oracle VM Virtualbox running protection and Linux as a host to blind the world to my use of Windows in a virtual sandbox, it might still be viable as a cradle is to a baby.

Enough of that.  If I have to, I will add Oracle VM Virtualbox, install Win7 as a client, add Epson XP-320 drivers, and pass files between the two OSes.  So I can make the printer a go that way, but i don't want to have to go to that extreme.

So can someone help me here?  I had a Canon IP-6000D, IP-4000, and IP-4300 printers that all worked well under an old version of Ubuntu (8.04), and promises made that I found that Ubuntu 11.04 supported then current versions of Epson, but how about the present?  I can refer to Unity/Dash in a hearbeat for an interface (natural Ubuntu) or switch to Compiz (all choices if you install gnome-session-flashback), so don't let the interface throw you if you don't know metacity.

Epson is a new challenge for me, and I have no idea how to tackle it.  It's been around longer than XP-330, and I see XP-330 being tackled and resolved.  Makers of printers and such tend to reuse established code and processes rather than invent new ones, which sort of makes a family.   But it is a software family, not a hardware one like using the same ink cartridges, so is only an issue on setup.  The references I found in passing were for Linux in general, not specific to Ubuntu or 16.04 LTS.  The more specific the info given, the more certain the outcome.  But any information is better than none.  Can you help me out here?

---

### Post by vasa1 on 2016-06-19
Split off from [Printers fully supported by ubuntu 14.04]("http://ubuntuforums.org/showthread.php?t=2324937")

---

### Post by howefield on 2016-06-19
Post moved to own thread, not much point in posting for support in a thread marked solved and which relates to a different printer and version of Ubuntu.

---

### Post by howefield on 2016-06-19
> **oldefoxx said:**
> Checking with Epson on-line support, they do not provide drivers for Linux and act like they never will.  They were no help at all except to suggest an old SCSI link that is meaningless. 

Have you tried searching for drivers on the Epson website ?

[https://www.epson.com/cgi-bin/Store/support/supDetail.jsp?oid=253768&infoType=Downloads&platform=OSF_O_LINUX](https://www.epson.com/cgi-bin/Store/support/supDetail.jsp?oid=253768&infoType=Downloads&platform=OSF_O_LINUX)

They appear to be all there.

---

### Post by oldefoxx on 2016-07-01
Okay, some progress and corrections to make:

This PC is runnung 14.04 LTS, ,ot 16.04 LTS.  I reverted io 14.04 LTS on this PC months ago when I was cross-checking how each version handled hard drives.  I never reverted back.  Now with 16.04 LTS much further along, I will be changing over.  But I have some HDD cleanup to attempt first.

The XP-320 printer is attached and working, sort of.  I can't find a way to access it directly from the interface, but I can print a test page from where I add printer.  And Google was able to detect it and add it as a printer under the Cloud.  So via Google, I can now print documents to it.  But under LibreOffice, I cannot specify a printer or access it directly.  I need something to pull these pieces together.  That is suppose to be cups I believe.  But I have no details on configuring cups to recognize a new printer.  I found reference in one post that spoke briefly of stopping and starting the cups daemon, so that makes it a background service that you don't have to call directly.

I've not tackled the scanner part yet.  Scanners generally meet the T.W.A.I.N. specification, but for Linux, you usually look to iscan or xsane, which are free.  Being free means less interrest in tackling someone else's problems, and only those that got through the process on their own are likely to get involved.

If you are willing to pay, there is vuescan, where profit for effort makes a better driver.  I don't know what the cost are, and that puts the cups solution on onto someone else.    So I will stay this course for awhile.

A problem encountered is old threads, old posts, and the fact that much once available or applicable has since been made obsolete.  Links go dead, and packages get moved or dropped altogether.  You may have to go back to the source code and start over.  Or get a complete packages with no outside dependencies.

AFAIK, search engine results are not offered up on a time bases.  That is, the most recent postings are not placed first in sort order.  Not in the order of being found and indexed, but when the file referenced was last modified.  The more recent the modification, the more current the results, we would hope.

Google will let you search contents (or something) based on a Julean Format.  This is a date format that begins with 1900.  The date 0000101 would be the first day of January, 1900.    The date 1150703 would be  2000 + 15 for the year, the 7th month (July), and the 3rd day of the month, or 03/07/10`5 according to American tradition.  For easier sorting, much of the world follows the yyyy/mm/dd format.  Julian reduces this to cyymmdd, where "c" is the century.  There are algorythms in Fortran and other languages for converting Gregorian dates to Julian and vice versa.  It's just straight math, so should be easy to convert the code to a different language.  Or work out your own steps.

Years become leap years when, y representing yyyy, is divisible by 4 evenly but no divisible evenly by 100, unless it is divisinle as well by 400.  ly represents a leap year.  Thus,

    ly = MOD(Y,400) = 0 OR MOD(y,100) != 0 AND MOD(Y,4) = 0

If you don't have MOD(), you can do it with INT():

    ly = (INT(y/400)*400 = y) OR (INT(y/100)*100 <> y) AND (INT(y/4)*4 = y)

Actually, every 2,000 years, the variances in the earth's orbit around the sun as found in some research I did, indicate the formula should be extended to exclude all multiples of 2000 from being leap years.  But 2,000 has been celebrated as one, so other corrections will be required in the future.

We won't be around that long anyway.

I was planning a way to include 2 digit year abbreviations as well.  Thid would limit dates from going back as far, but would allow for droppind the century altogether.  Thr trick is to recognize that people look further back than they look forward, and tack on the century closest to where their interest lies.In dealing with the centuries 18, 19, 20, and 21, and today's date, we would rule out 18 and 21 quickly.  If the current year is 2016, and they enter 98, it is more likely the year 1998 rather than 2098.  So 1900 + 98 is our best guess.  If they enter 1 or 01, that is less likely to be 1901 than it is to be 2001.  If we guess wrong, they just enter mor than 2 digits for the year.  Thus, we hav 2 digits represent years in a century as far back as the year 100.  To represent centuries before 1900, we just go negative.  -1830512 woild be 1900-100 or 18th century, + 83 is 1883, 5th month, 12th day, or May 12, 1883.

I may be wrong about how it is suppose to work, but I only have the principles down.  Until you write the approved algorithms into code and run a full range of dates can you be sure of the specifics. 

And until you use the feature in google, you won't have an idea what it is actuall searching for, which could be embedded test in the document or a date related to the document itself.

---

