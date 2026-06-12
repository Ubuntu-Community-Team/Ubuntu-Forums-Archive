---
title: "Calendar Applet,  Can it be replaced or have settings changed?"
date: 2015-08-29
forum: General Help
---

### Post by oldefoxx on 2015-08-29
I have the Classic Deskrop installed and am running with Metacity as my way of seeing the desktop.  It's fine, and though I did once stumble on how to change some of the colors, I don't remember how.  Be nice to be reminded again.

But the main point of this post is, the calendar applet is small, black, with white and two shades of gray against a background of black.  The shade of gray to mark the current day is almost indistinguishable from the black of the background, and it is usually the current day that I am interested in determining.  Finding it is something of a challenge.

So can I change this somehow?  Use a bit of color, make it larger, whatever?  Searching for calendar, I find mention of installing evolution or california, which are two email programs to replace thunderbird.  That's not what I want to do, as I've lots of message filters already worked out on thunderbird.  It doesn't seem to offer a calendar feature as the others do, but I let my wife handle the appointments issue, and I just need to know the current date, day, or time, which an applet can handle.

Actually, in checking this out further to make sure I hadn't miss anything, I went under Applications > System Tools > Preferences > Appearance > All Settings > Time and Date.  I found I can check boxes to add the day of week and date, even week of year to the toolbar.  I've done that, and we will see if that is enough for me going forward.  But I would still like to know if the applet can be replaced or not.

And speaking of the top toolbar, I've found that you can drag a desktop link to it, and launch an application from there with just one click.  What I don't know how to do is remove a link from there if you want it gone later.  I found that you can hold down the right mouse key and access the link's Properties, so I guess you could modify a link to point to a different application, and in this way just redefine and reuse an existing link, but as far as removing it, I don't see any way to do that.  I have a few links up there now, for opening a terminal, opening gedit, opening firefox and/or slimjet, opening thunderbird, and opening the purebasic IDE.

Anyway, there are a few questions here that I hope someone can answer, and information from my end on what you can do, assuming you replace Dash with the Classic view of the gnome desktop.  For details on how to do that, I refer you to [http://www.howtogeek.com/189912/how-to-install-the-gnome-classic-desktop-in-ubuntu-14.04/]("http://www.howtogeek.com/189912/how-to-install-the-gnome-classic-desktop-in-ubuntu-14.04/")

---

### Post by oldefoxx on 2015-08-29
Speaking of a helpful tip, I learned this one ages ago when working with links on Windows' Desktops.  I just tried this with the desktop links on Ubuntu, and it does the same thing.

Say that there are only an handful of web sites that you go to on a regular bases.  You van set up custom desktop links on the desktop to that that vrowser of your choice and go directly to that website.  It's simple:  Create (by right-button choice or dragging) a link to that browser to the desktop.  Then with the right mouse button, click on the link and go under Properties.  On the line titled "Command", you may see the path, but you will certainly see the browser name, followed " U%".  I don't know what the " U%" represents or does, but it's always there. 

Say you wanted to have a link that always took you to these forums, so after the " U%" you simply add " ubuntuforums.org".  Now you can also rename the link to something like "Ubuntu" or "Ubuntu Forums", and save it.  Then double click on it with the left mouse button and see of you go there.  Do it right, and it should happen.  Then you can do it all again to create more specialty links to go to other sites. My brother-in-law loved it, because he could just click on a link and go where he wanted to go, rather like having a chauffeur drive you about.  It was quicker getting there this way as well, especially if you had the browser set up to automatically log you in once you got there.  He never did mess with the idea of restoring the last session after he got there, but that is also an option with some browsers.

---

### Post by oldefoxx on 2015-08-29
I didn't realise it before. but you can adjust the brightness settings of the screen under Ubuntu.  It's under Preferences > Brightness & Lock.  You can't really drag the slide back and forth to adjust brightness, but you can click the mouse on the slide bar where you want to position it, and the effect on the screen is immediate.  I cut mine down to roughly 80%, because white was glaringly white.  Much better now.

Administration settings effect everybody on this machine.  Preferences only effect the current user.  For instance, with the right software added, you can choose which view you have of the desktop (adding this feature was covered in the 1st post).  Other users can pick a different view.  Under Preferences > Main Menu, you can decide what shows up under Applications.  If something does not show up there, it can still be called using a terminal and typing in its name on the command line.

What's of some interest is that you cannot pick and choose what shows up under Places.  USB devices appear here when they are attached, and then mounted automatically when you click on them, but you find the internal drives/partitions are all under Computer.  In Linux, everything related to folders and files is considered just a part of a single file system.  In ubuntu, these are individually accessed via the /media folder, where it gets mounted under a user account.   It's different from DOS and Windows, where each device is treated independently and given a drive letter.  You can deal with the individual devices under Linux with the appropriate software, such as using gparted to handle disk drives and partitions, or Brassero for handling DVD and CD disks,

Printers and scanners are unique, in that the software with them is generally of two types:  Applications or simply drivers.  Application software has to be used with a specific operating system,  Drivers have to meet the driver specifications for a specific system as well.  Applications meet their own criteria for features.  Drivers need to meet certain performance criteria expected by higher level software,  For Linux, printers must be able to work with CUPS.  For scanners, drivers are part of custom libraries, providing API support for SANE or XSANE.  Windows provides TWAIN support, which is by far the bigger part of the software market.  There have been efforts to port an adaption of TWAIN over to Linux, but the problem is, it all has to be carried down to the hardware level, so why bother?  Vendors either write code specific to SANE for the small Linux market, of you look for a different solution.

The most common solution then is to shop for a scanner or 3-in-1 that includes the necessary Linux software.  Rather than range all over the scanner and 3-in-1 market in search of one, that information has been collected into lists of what works, does not work, or is still untested as to  in whether it works with Linux or not.  Searcj for SANE scanners or something similar.  There is even a HOW-TO on testing your present scanner under Linux.

A different solution is to see if someone else has found an answer by a web search, or to install a VM Manager like Virtualbox and install a Windows client under that.  You use the Windows client to try and use TWAIN with the attached scanner.  In earlier times, scanners were designed to attach and be used with bidirectional parallel ports.  That technology has been dropped in favor of using USB now.  Virtualbox, with its Extended Features package installed, allows you to configure specific devices for pass-through to the client, and supports both USB 2,0 anf 3,0.  Technically, it should work.  And with the ability to share folders and files between host and client, you can effectively have it both ways.  But this solution is a bit of an inconvenience, and may be most suitable for those that already own a scanner that does not have Linux support.

---

### Post by ajgreeny on 2015-08-29
I have edited your tag for this thread from Lubuntu to Ubuntu to avoid confusion.

---

### Post by oldefoxx on 2015-09-04
Thanks/  I missed that

---

