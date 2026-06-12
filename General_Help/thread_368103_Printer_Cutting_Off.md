---
title: "Printer Cutting Off"
date: 2007-02-22
forum: General Help
---

### Post by Miniberger on 2007-02-22
Everything I print in Ubuntu that goes to the bottom of the page gets cut off by my printer, as if it thinks the paper is larger than it is. I have my printer set to letter sized paper, and all other settings are normal.

In Open Office Writer, for example, the last line of text is cut off. My margins are set at 1'', but also appear smaller than normal at the top (doesn't cut off, but text is very near top of page). In print preview, the page appears normal, as I want it to print, but doesn't come out that way.

My printer is an HP Photosmart 7350, and prints fine in MS Word in Windows.

Any ideas?

---

### Post by elf@whoever.com on 2007-03-06
I had a simular situation. I have a HP lj1000 and everything but OpenOffice prints just fine. OpenOffice under the printer settings, is assuming that I have A4 paper for some wierd reason.  The net result is I end up with scewed or chopped off printing. Nothing I do makes it think otherwise. The printer is set to Letter size under the gnome printer panel I guess you would call it.

I figured out a work around for the problem, as well as later on a permenant solution:
The work around is you can manually go to File, Printer Settings, change to the proper paper size. But this will only last for that one file that you have open and it will revert back to A4 when you reopen the document.

The permenant fix was to use firefox, or whatever browser you want, and enter the address for the cups manager web interface:  [http://localhost:631/](http://localhost:631/)

Then click on Manage Printers, followed by Set Printer Options. Set the correct options here and Set them to save the setup. Now when I open any document thats Letter size, it prints correctly with no further intervention.

I have NO clue how I have had no other printing problems of that sort, except with OpenOffice. :lolflag: Been printing just fine for over a year now.
Guess ubuntu guessed what I wanted and gave it to me :)

---

### Post by laidback on 2007-03-06
Check printer settings in System>Adminstration>Printing then double click your active printer and select Printer>Properties. Set the paper size as required + other params if wanted.
Also set the paper size within the application, i.e. OOo Writer. (check page configuration as well)
Now try again, no guarantees.

I have mine working OK but took some time, really annoying. Came to the conclusion that my problems were from inconsistences between these settings.

---

### Post by Miniberger on 2007-03-09
Ok, so I changed my overall printer setting to letter in Gnome printer options, then did it for the individual OO document, with default margins. This fixed the problem at the bottom of the page, with the text lining up properly, but the first line of text was just below the top of the page with almost no margin, despite OO showing a 1 in. margin. 

The page looks as I want it in OO print preview.

I also tried using CUPS through FF which did exactly the same thing.

I changed all of the paper types to letter everywhere, but its Is there just one more setting that I'm missing? 

Thanks for all of the help.

---

### Post by laidback on 2007-03-10
What does test print come out like? (Printer>Properties)
Have you got the correct driver loaded?

---

### Post by Miniberger on 2007-03-10
Now that I have all of my print settings lined up in letter format, I have got it to work.

OpenOffice Writer just needed some formatting changes to its margins and now it is all working correctly. I stopped using CUPS as it doesn't seem necessary, I just adjusted my printer settings.

Thanks for all of your help!

---

### Post by jubu on 2007-03-22
That little CUPS web server config tip just saved my butt on a paper I have due tomorrow!!:guitar: 

I have an Epson Photo Stylus R300, and I had the mysterious margin issue where the printing seemed shifted down an inch, cutting off the bottom. I set the default paper size to Letter in the printer properties, and even changed the /etc/papersize file to say "letter" instead of "a4".  Neither worked - but when I went to http:localhost:631, I saw that the paper size was still set to a4. I changed it there, and when the browser prompted me for my username and password, I just used my regular login info. Presto - everything works now. Thanks sooo much for the tip.

I wonder why the settings I changed in gnome didn't show up in CUPS when I used the web server. Is the gnome settings app setting a different CUPS?

---

### Post by elf@whoever.com on 2007-03-22
> **jubu said:**
> That little CUPS web server config tip just saved my butt on a paper I have due tomorrow!!:guitar: 

I have an Epson Photo Stylus R300, and I had the mysterious margin issue where the printing seemed shifted down an inch, cutting off the bottom. I set the default paper size to Letter in the printer properties, and even changed the /etc/papersize file to say "letter" instead of "a4".  Neither worked - but when I went to http:localhost:631, I saw that the paper size was still set to a4. I changed it there, and when the browser prompted me for my username and password, I just used my regular login info. Presto - everything works now. Thanks sooo much for the tip.

I wonder why the settings I changed in gnome didn't show up in CUPS when I used the web server. Is the gnome settings app setting a different CUPS?

Glad it helped you out. :p Thats basically the kind of deadline I was working under when I found the solution. :lolflag: 

I have no clue why its that way. Its not that way for everyone. Might have to do with printer installation linkages to cups.  Oh well, after I fixed it the first time, I never had to fix it again. Both settings are the same when I change it from the gnome panel now.

I went and did some searching and there are several other people having similar problems. Search on cups openoffice margins pulls up 3 articles focused on this. Any broader and you have to sift through it all. The good news is this does not seem to be a problem related to any one specific brand or type of printer.  It is most noticed with OpenOffice.org it seems. Probably because unless you set it in printer settings in OOo it just uses the defaults for the printer. Since gnome panel and cups are not handshaking well some people get this odd situation?!

I guess it might be worth seeing if there has been a "bug" report on this and if not submit one. :)

---

### Post by FidalgoMike on 2007-03-24
Greetings all,

Have been beating my head against the wall on this issue myself. ](*,) I'm wondering if the maintainers can do something along the lines of:  1) adding cupsys to group shadow so the localhost:631 cups config page will work properly; and 2) in the US, "automagically" make letter the default papersize. On 2, I'm thinking along the lines of if a US time zone is selected, then letter is the default, else a4? I've never seen a4 paper used here.

Thanx,
Mike

---

