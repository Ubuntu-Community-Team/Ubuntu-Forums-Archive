---
title: "Foxit Reader users and user suggestions for alternates"
date: 2020-02-09
forum: General Help
---

### Post by dustyt on 2020-02-09
Guys, I am really trying hard to get away from Windows 10, even with my work.

I tested several distros via live usb and installed Foxit Reader to test drive to see how the distros did for doing my work. I didn't run into any issues until post hard install... which I admit there was a time lapse there. So Foxit Reader may have updated during that time for the worst which would explain my issue. I checked my installed version and checked for updates as well. It is up to date and on version 2.4.4.0911

I have been using Foxit products for a long time. Probably 6 years now. What they offer is pretty critical to the office productivity portion of my work. So I will be very specific about my needs and my issue.

I was using Foxit Phantom on windows until about a month ago. My work pc crashed and I could find no way to move the software to my new PC. So I tried just the Foxit Reader and found it does everything I need really. 

I need to be able to open multiple PDF's in tabs in the same program. At first this was not working. Each was opening a new instance of the program. And I kept getting not responding messages from it until finally I locked up and had to hard boot. Now this function seems to work.

I also need to be able to highlight PDF text, which is also working fine. And I need to be able to save those changes which seems to be working fine as well.

Lastly, I need to be able to select text in the PDF and paste it elsewhere. This sorta works. What I mean is, I can copy and paste text elsewhere. But each time I go to do it again, I paste the first text in again. I have found if I copy twice I am able to get the new text selection to the clipboard to paste elsewhere. It should just work copy/paste but it does not and it is driving me insane. copy copy again/paste

Those of you that use Foxit reader, could you check your version and check the copy/paste functionality by copying from PDF and pasting a few different lines of text from a few different lines or pages to a text file or Libre Writer? 

Please post if it works correctly or not and Foxit Reader version.


Also if anyone else knows of a PDF program where I can open multiple pdf in tabs, advance through pages by clicking a next page arrow or pressing an arrow key, copy text and paste elsewhere, highlight text and save changes, please let me know. 

This is pretty basic functionality. I am playing with Evince Document Viewer now, but I can't seem to open multiple in tabs, so...

Seems like a small thing. But I need to be able to do my work in a Linux Distro if I want to stay out of Windows.

---

### Post by Quarkrad on 2020-02-10
I think you will find Qpdfview will satisfy your needs - it is also in the repositories.  If you haven't got Synaptic install it via **sudo apt-get install synaptic** and once it is installed (in addition other things it searches the repositories and allow you to install programs) search for qpdview and install it.  Any problems get back.

---

### Post by rbmorse on 2020-02-10
If you don't mind a pay to play application take a look at Master PDF Editor.  I think the license fee is about $40 a seat.

---

### Post by TheFu on 2020-02-10
There are multiple ways to copy/paste in X11.  I prefer the select/paste method, which works with almost all programs.
Just select the text you want w/ the left mouse button, then use the middle mouse button to paste into any text-input location. That can be a terminal, textedit webpage, or editor.

I've been using **atril**.

Not all PDF flles have text. Some are just images, so selecting any text isn't possible.  But you can run those through OCR tools and get text.  You can also use **pdftotext** to take the nicer PDF files with text underlying into text files.  As for tabs, my WM makes fining the window easier than using tabs.  I dislike programs with tabs greatly. That's why we have different workspaces with WMs.

---

### Post by dustyt on 2020-02-10
Thanks, I forgot about middle click. It has been a while... shame on me, but I am trying to return.

I never thought about this though because copy/paste works fine in everything else, so I was blaming Foxit solely for the issue. So I will try the other ways and see if that makes a difference.

It is still likely I may try another. I swear Foxit takes about a minute to load

---

### Post by dustyt on 2020-02-10
I am back to the issue of Foxit (and also Qpdfview) opening everything in a new program window. I have to open them from a browser (firefox) and they aren't loading in tabs. Each is a new separate window.

Yesterday Foxit was opening them in tabs.

What am I missing here???? A setting somewhere?

---

### Post by dustyt on 2020-02-10
I rebooted and Foxit reader started opening in tabs in the same window again. No idea why it quit.

Qpdfview... well it will open in tabs off the hard drive but not out of the browser? Opening from a browser it opens in new instance windows every time?

Both are freakishly slow to open rather opening a pdf or just opening the software. 30 seconds to a minute! Worse than in windows, not better. First time I have ever experienced anything similar be slower in Linux than windows. Something ain't right.

---

### Post by TheFu on 2020-02-10
snap packages?

---

### Post by dustyt on 2020-02-10
I uninstalled Qpdfview. Never could get it to open multiple pdf files into tabs in the same window. And the copy text proceedure was way too much. Select copy to clipboard, draw a box around the text. Really?

Thanks for the suggestions for Master PDF Editor. That is a step in the right direction. It like Foxit will open several in tabs in the same window. 

Like Foxit I am also finding it has the same copy text problem. I have to do it twice after the first time. Copy Copy with mouse or Control C twice. Else I paste the same text again. I have tested the copy function way more than I want to and have found if I move on what is really going on is it only copies every other time. For example if I copy A paste, copy B paste, copy C, paste, copy D paste, copy E paste, the result is A A C C E E and so on. I dont get why both have this issue while the others do not. Weird.

Like Foxit it also takes 30 seconds or more to open the software or open a pdf. That's crazy. The delay was long enough to begin with that it makes you think it is not working, lol.a

Atril and Evince both open and open files quickly and don't have the copy issue but neither supports tabs, which is a shame.

---

### Post by TheFu on 2020-02-10
Clipboards have screwed up the X11 select/paste methods.  If you don't use a DE, then that issue goes away.  DEs are optional, not mandatory. The GUI you choose is completely up to you on Linux.  Don't feel like the big 10 GUIs are the only choices.  With a lighter GUI, we usually have more control.

---

### Post by Holger_Gehrke on 2020-02-11
Might be a stupid idea, but how about using the pdf functionality of your web browser ? Both of the major browser can display pdf, tabs are the standard behaviour and at least on Firefox cut and paste seems to work.

Holger

---

### Post by rbmorse on 2020-02-12
> **dustyt said:**
> 

Like Foxit it also takes 30 seconds or more to open the software or open a pdf. That's crazy. The delay was long enough to begin with that it makes you think it is not working, lol.a



That's odd.  It opens quickly for me.  Sometimes it takes a bit to unpack a really large .pdf file, but little ones open quickly. 

Try starting it from a terminal and see if it complains about a missing module or library.

---

### Post by dustyt on 2020-02-12
OK thank you rbmorse,

I have that issue opening just the software or opening a pdf either one. Same issue with Foxit and Master PDF. Atril and Evince open right up. I will start them from terminal and see.

---

### Post by dustyt on 2020-02-12
> **rbmorse said:**
> That's odd.  It opens quickly for me.  Sometimes it takes a bit to unpack a really large .pdf file, but little ones open quickly. 

Try starting it from a terminal and see if it complains about a missing module or library.

Not that I can see.

After pushing enter to open Foxit Reader from terminal, the little box blinks probably 20 seconds, then stops blinking for probably 10 seconds. Then it starts running. I don't see anything in the trial about missing modules or libraries.

---

### Post by rbmorse on 2020-02-12
From the description, it sounds like exactly the same thing I had here with both Master PDF Editor and VueScan,  except in my case, when I started the applications from the terminal I received an error message about a missing module.  

From my notes it was:

libcanberra-gtk3-module

and it's in repository.  You'll have to restart the machine after installing the module.  


If that doesn't resolve the long start time issue you can remove the file, so it might be worth a try.   Don't forget the restart part. It's necessary.

---

### Post by dustyt on 2020-02-12
> **rbmorse said:**
> From the description, it sounds like exactly the same thing I had here with both Master PDF Editor and VueScan,  except in my case, when I started the applications from the terminal I received an error message about a missing module.  

From my notes it was:

libcanberra-gtk3-module

and it's in repository.  You'll have to restart the machine after installing the module.  


If that doesn't resolve the long start time issue you can remove the file, so it might be worth a try.   Don't forget the restart part. It's necessary.

Dang I thought you had it because I had a message like that from trying to get some python stuff going. Miniconda I think. I thought maybe that was it, but seems I already fixed that. But I think I will still uninstall and reinstall because I don't know which I installed first. But anyways, I went to install it and this was the result.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcanberra-gtk3-module is already the newest version (0.30-7ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

---

### Post by rbmorse on 2020-02-12
Ah, nuts.  I thought I was on to something there.  

I can tell you that on my machine (Bionic 4.04.3) MasterPDF Editor opens instantly when I click on the icon and most documents load expeditiously.  Maybe there's a hint in the application logs or maybe dmesg.

---

### Post by dustyt on 2020-02-18
What about Okular?

What is the word on installing this particular reader being that it is associated to KDE, although I am not running a KDE environment right now?

I know I can install it. I just haven't ran Linux in a long time. I know way back some would say not to do this and because of the KDE dependencies it brings along with it. Back then I had a couple Gnome boxes and a KDE box (Kubuntu) I would boot to play around in the KDE environment and use KDE software. But I also realize things change over the years and this may be considered a non-issue now.

---

### Post by dustyt on 2020-02-28
I tried Okular, it was a waste of time. I found that it could not open any PDF edited by any other reader or editor. I also could not use the save as function.

With some more guidance I purged qt5-gtk2-platformtheme and that allowed Master PDF Editor to open really fast. This didn't help Foxit Reader at all though?

Unfortuneatly I still have the copy/paste issue with Master PDF Reader though. After the first copy, I have to copy everything twice in order for it to copy. 

I am somewhat tempted to try it on another distro to see if that persists. Or try it on an older version of Ubuntu. IDK.

What I do know is, it is the little nagging things like this, you know basic operations not working correctly that hinder Linux from where it should be.

---

### Post by mastablasta on 2020-02-28
> **dustyt said:**
> I tried Okular, it was a waste of time. I found that it could not open any PDF edited by any other reader or editor. 


that's not true.

> 
I also could not use the save as function.


Why not? Function is supported.
[https://docs.kde.org/stable5/en/kdegraphics/okular/okular.pdf](https://docs.kde.org/stable5/en/kdegraphics/okular/okular.pdf)

> 
What I do know is, it is the little nagging things like this, you know basic operations not working correctly that hinder Linux from where it should be.
there are many little nagging things but oddly they hit only some users.

also, i am not sure what kind of manual labour you are into, but with linux (and at work) i learned about alternatives and to do the same task in a different way. so for example if you are searching any copying a specific text from file data - a computer might be able to pull it out faster in a different way. it depends really what you are trying to do. but i've seen many times people doing things manually, wasting time, because they didn't know about a better solution.

now back to options.
would zathura, which offers a tabbed tool work?: [https://pwmt.org/projects/zathura/](https://pwmt.org/projects/zathura/)
in Okular tabs work
another option is to set the pdfs to open in chromium, chrome or firefox

now as for slowness - the speed of opening the files depends primarily on the read speed of disk drive and CPU. with modern CPU in the PC, the bottleneck is usually the disk drive. old HDD in laptop is worst, newer SATA HDD is better, and even better option is SSD and ofcourse the best currently is nvme. when working with plenty tabs in one app it also pays off to have plenty of RAM. especially if you keep opening and closing the same apps. i would go with at least 8 Gb these days, 16 Gb is even better.

BTW i have about 5 tabs open on Adobe reader in windows 10. and it get's slow as i add more stuff. i only have 4 GB ram. Okular on my old single core PC at home loads way faster than Adobe does on win 10 on a modern i3 CPU.

---

### Post by monkeybrain20122 on 2020-02-28
qpdfview >> Foxit. In fact much much better. It is a also very fast. But the version in the repo is very old and buggy, need to install from the ppa [https://launchpad.net/~adamreichold/+archive/ubuntu/qpdfview-dailydeb](https://launchpad.net/~adamreichold/+archive/ubuntu/qpdfview-dailydeb)

---

