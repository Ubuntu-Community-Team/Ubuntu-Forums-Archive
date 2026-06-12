---
title: "Help with maxview program for viewing .max files"
date: 2013-05-09
forum: General Help
---

### Post by benawhile on 2013-05-09
I have some old .max files that were created by paperport. I found a program called maxview [URL="http://sourceforge.net/projects/maxview/"]http://sourceforge.net/projects/maxview/
[/URL]that claims it can read them and convert them to .pdf. They are just image files. I don't know about 3D stuff.
I downloaded the maxview program and ended up with a debian icon on my  desktop that looks like a cardboard box with a red squiggle, and titled  maxview_0.7-1_i386.deb. I haven't sussed those debian icons out yet.  When I clicked on it it asked me if I wanted to open it with Ubuntu  software centre so I said Yes, and the software centre says it has been  installed, but how do I run it? I can't see it under Ubuntu "applications" and  when I click on a .max file it doesn't present me with "maxview" in  the list of options.

I did post a similar question to this elswhere, with teh main intention of informing the OP about maxview, but it was at the end of a thread and hasn't received any answers.

I have Ubuntu 12.04 XP Dual Boot. Which has been working  perfectly from the word go, which was last September. And a twin core  Athlone AMD processor. Does that mean I should opt for AMD 64 and not  i386 when downloading the maxview debian installation file?                                                                                                                                                                                                                            [[IMG]http://ubuntuforums.org/clear.gif[/IMG] Edit Post]("http://ubuntuforums.org/editpost.php?p=12638261&do=editpost")                                                                          [[IMG]http://ubuntuforums.org/clear.gif[/IMG] Quick Reply]("http://ubuntuforums.org/newreply.php?do=newreply&p=12638261&noquote=1")                                                                                   [[IMG]http://ubuntuforums.org/clear.gif[/IMG] Adv Reply]("http://ubuntuforums.org/newreply.php?p=12638261&noquote=1")                                                                                       [[IMG]http://ubuntuforums.org/clear.gif[/IMG]  Reply With Quote]("http://ubuntuforums.org/newreply.php?do=newreply&p=12638261")                                                                           [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/multiquote_40b.png[/IMG] ]("http://ubuntuforums.org/newreply.php?do=newreply&p=12638261")                                                                                                                                                                                                                                                                                                                                                                                                       
     
                                              
                        [+ Reply to Thread]("http://ubuntuforums.org/newreply.php?p=12638261&noquote=1")

---

### Post by Cheesemill on 2013-05-09
Try running the program from a terminal to see if you get any errors...
```
maxview
```

> **benawhile said:**
> Does that mean I should opt for AMD 64 and not   i386 when downloading the maxview debian installation file?
That depends on which version of Ubuntu you have installed. If you are running 64-bit then use the amd64 deb file, if you are running 32-bit then you should use the i386 version. You can see which version of Ubuntu you are running by going to System Settings > Details.

---

### Post by benawhile on 2013-05-10
Thanks, interesting result:

Ran in terminal and got this:

[I]ben@BENCOMPUTERUBUNTU:~$ maxview
maxview - An electronic filing cabinet: scan, print, stack, arrange

(C) 2009 Simon Glass, [EMAIL="chch-kiwi@users.sourceforge.net"]chch-kiwi@users.sourceforge.net[/EMAIL], v0.7

Usage:  maxview <opts>  <dir/file>

   -p|--pdf        convert given file to .pdf
   -m|--max        convert given file to .max
   -j|--jpeg       convert given file to .jpg
   -v|--verbose    be verbose
   -h|--help       display this usage information
   -d|--debug <n>  set debug level (0-3)
   -f|--force      force overwriting of existing file
   -r|--relocate   move a processed file into a 'xxx.old' subdirectory
   -i|--info       display full info about a file
      --index <f>  build/update an index file f for the given directory

If none of -p, -m, -j are specified, maxview opens in desktop mode, displaying
thumbails of the given directory

[/I]But it didn't actually run the program

Then I accidentally copied the whole thing in to a new terminal, and something happenend, tweaked around and found that by copying just the top two lines :
[I]maxview
maxview - An electronic filing cabinet: scan, print, stack, arrange

[/I]I got this:[I]ben@BENCOMPUTERUBUNTU:~$ maxview
maxview - An electronic filing cabinet: scan, print, stack, arrange

(C) 2009 Simon Glass, [EMAIL="chch-kiwi@users.sourceforge.net"]chch-kiwi@users.sourceforge.net[/EMAIL], v0.7

Usage:  maxview <opts>  <dir/file>

   -p|--pdf        convert given file to .pdf
   -m|--max        convert given file to .max
   -j|--jpeg       convert given file to .jpg
   -v|--verbose    be verbose
   -h|--help       display this usage information
   -d|--debug <n>  set debug level (0-3)
   -f|--force      force overwriting of existing file
   -r|--relocate   move a processed file into a 'xxx.old' subdirectory
   -i|--info       display full info about a file
      --index <f>  build/update an index file f for the given directory

If none of -p, -m, -j are specified, maxview opens in desktop mode, displaying
thumbails of the given directory
ben@BENCOMPUTERUBUNTU:~$ maxview - An electronic filing cabinet: scan, print, stack, arrange
QLayout: Attempting to add QLayout "" to Pagewidget "", which already has a layout
QLayout: Attempting to add QLayout "" to Pagewidget "", which already has a layout
"/" 
Dirview::selectionChanged 1 
"//" 
new Desk "//" 
dir not found
couldn't write maxdesk.ini
ben@BENCOMPUTERUBUNTU:~$ 

[/I]And **a maxview window opened up**, at first I couldn't make head or tail of it*, *I have attached a screenshot of it.

Then playing around with the window I found I was able to navigate to the folder where my scansoft/paperport documents were, and **actually display them as they used to display in paperport!** Except that the program didn't display them smoothly, the thumbnails for a file would keep changing from one image to the image of a different file when I did things with them, although hopefully so far the display on "page view" seems to be accurate. I** found how to do what I wanted, convert the .max files to .pdf and save them to a different folder,** but the only way was to select from desktop view, duplicate as .pdf, select .pdf and print to (location). If I tried anything from page view the programme closed/crashed.

So something is working but it needs cleaning up. I still don't know if the debian file on my desktop has been used.

What should I be typing in to terminal to run properly? I only found this "terminal>copy>paste> terminal" method by accident.
Do I need the debian file?
How could I stabilise the thumbnail images on desktop view?
How can I stop the program from closing from page view?

---

### Post by imon.glass on 2013-12-14
Hi,

This has actually moved to github here, and renamed to paperman.

[https://github.com/sglass68/paperman](https://github.com/sglass68/paperman)

The latest version can remember folders that you add, so you don't need any arguments when running it.

Regards,
Simon

---

