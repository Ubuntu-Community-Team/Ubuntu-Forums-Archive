---
title: "Struggling with the switch to Ubuntu"
date: 2016-06-05
forum: General Help
---

### Post by Paul_Patton on 2016-06-05
Hi-
My question is a general one.  I have my desktop machine set up as a dual boot with Windows 7 and Ubuntu.  For a long time I've wanted to switch over to Ubuntu as my primary operating system, but a series of problems have prevented it.  I'm a fairly computer literate person, but have no formal training in computer science.  What do I need to learn in order to be proficient enough to confidently rely on Ubuntu Linux as my primary OS?  What are the main resources available to me to do so?  I live in Toronto, Canada, but have so far been unable to locate a local Ubuntu users group.

My single biggest problem is with installing the software I need in Ubuntu.  Software that is available through Ubuntu's 'Software' feature installs automatically, but the rest doesn't.  There are two software packages I need to install, but can't be installed through 'Software'.  One is VPN software so that I can access my university's library content.  The other is f.lux, which I need because I have sleep problems without screen dimming software.  I have some familiarity with Unix commands, and have found instructions for installing software via the command line on-line.  When I follow such instructions, I inevitably run into a snag, spend a couple of hours trying to troubleshoot, fail, and go back to Windows in defeat.  I also tried installing MATLAB under Ubuntu Linux, with similarly frustrating results.  I tried setting up to run Windows 7 in Ubuntu as a virtual machine.  I successfully installed VirtualBox software, but when I did I lost my ability to use WiFi in Ubuntu, and this problem went away only when I uninstalled VirtualBox.  

Overall, my main needs are as follows:

1. Office and bibliographic database software.  I have found Libreoffice  to be fine for my office needs, but have had some problems with using  Mendeley in place of EndNote for my bibliography.

2. The ability to open and do OCR on .pdf files and to upload them to my  ipad to read.  Goodreader doesn't have a version of Goodreader USB that  lets me upload from Linux to my iPad, so I apparently need to run  Windows as a virtual machine for this.

3. The ability to install and run VPN software so that I can access  library contents from my Unix environment.  In general, I need to be  able to effectively install and uninstall software without hours of  troubleshooting and frustration. This is my biggest single Ubuntu  Achilles heel, and perhaps the biggest thing that has prevented me from  adopting Ubuntu as my primary OS.

4. The ability to install and run MATLAB within a Ubuntu environment.   Because of the limited funding of my employer for running this on my  home machine, it needs to be a 'bootleg' version.  This is easy to do in  Windows 7, but has so far defeated me in Ubuntu, despite the  instructions provided to me with the needed MATLAB version.

5. The ability to run Windows 7 as a virtual machine within Ubuntu  Linux.  I succeeded in installing Virtual Box, but it caused my Wifi  connection to fail.  I have not been able to solve this problem except  by uninstalling Virtual Box.  I need this to be able to run Windows  applications when I need them from within Ubuntu.

My question is not a specific one about how to solve these particular problems.  It is a general one.  What do I need to learn in order to become proficient with Ubuntu given these five classes of needs?   Where do I learn it?  I'm a busy graduate student.  Given the number of problems I've encountered so far with Ubuntu is it really reasonable for me or anybody without a computer science degree to aspire to use it as their primary operating system with reasonable expenditure of effort?  Thanks.
-Paul Patton

---

### Post by HermanAB on 2016-06-05
Well, consider how many years you spent figuring out how to use Windows, then get a big mug of hot chocolate and try again...

Regarding your VPN connection: Without any technical information on what kind of VPN it is, you can forget about it.  There are too many different VPNs and too many variations on the theme and too many ways to do authentication, to have any hope of getting it to work through trial and terror.

For OCR, there are multiple options in the repositories.

So your best bet is to install Virtualbox properly (which is as simple as apt get virtualbox) and make a Windows XP or 7 VM for special software that you cannot get to work with Linux.

---

### Post by ventrical on 2016-06-05
Hi,

 I am member of Ubuntu Development Cycle testing. We have created a wiki which you will find below in my tag that might be helpful. Also I am providing a link which helps with common sudo commands in terminal. You may or may not find it helpful. It is a little bit of reading.

[http://ubuntuforums.org/showthread.php?t=1970289](http://ubuntuforums.org/showthread.php?t=1970289)

regards..

---

### Post by dragonfly41 on 2016-06-05
I'll add some suggestions ..


[case #1] LibreOffice, zotero standalone or Firefox zotero add-on for citations (substitute for Mendeley).
Also explore pandoc for managing document flow [http://pandoc.org/README.html](http://pandoc.org/README.html)
Note that the Ubuntu version of pandoc in Software Centre lags behind the latest release so you may find it useful to build a later version of pandoc (I have version 1.17.1).   Explore using markdown editor for writing your reports (to be converted by pandoc into any format you choose - including maths). Explore Atom editor with Markdown Preview Plus package added (to preview markdown content).

[case #2] Install Tesseract OCR and OCRFeeder.

[case #3] VPN .. I pass on answering that question.

[case #4] Read here ... [http://askubuntu.com/questions/509902/how-to-install-matlab-on-ubuntu-14-04](http://askubuntu.com/questions/509902/how-to-install-matlab-on-ubuntu-14-04)
and install Matlab via MathWorks account.

[case #5] Continue trying to install VirtualBox.

[later edit]

Adding this link on F.lux ... [http://askubuntu.com/questions/493507/flux-for-ubuntu-14-04-possible](http://askubuntu.com/questions/493507/flux-for-ubuntu-14-04-possible)

---

### Post by Paul_Patton on 2016-06-11
Thanks for the very helpful responses.

---

### Post by Bucky Ball on 2016-06-11
1. [Zotero]("https://www.zotero.org/"). Don't bother with anything else in Ubuntu for academic, or any other kind, of referencing, IMHO.

I have used it for the past six or seven years during which time I've done a BA, then honours and am now doing a masters. I couldn't recommend it more highly for academic citations and bibliographies in Ubuntu. It installs as an add-on to Firefox or there is a stand-alone version. 

There is also a plugin which links it to Libreoffice and puts Zotero icons right there in the taskbar so you can insert citations directly from the Zotero database and Zotero looks after it (including changing things around when you move or delete citations, etc.) 

As for 5., best to post a new thread. Best to keep to one question per support thread, actually, to improve your chances of help, so you might consider that if you have problems with any of the other things that need more help than suggestions or risk this thread getting v. confusing! :)

Good luck.

---

