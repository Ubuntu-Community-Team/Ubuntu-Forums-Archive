---
title: "samsung ml2010"
date: 2006-07-30
forum: General Help
---

### Post by shanepardue on 2006-07-30
i now have the driver installed from samsung's website and the printer is being recognized correctly. however, when i print something, the job stops before the printer even starts printing. i found this info on google...how would i go along with what he is advising?

"I just got
another problem when trying to print a test page. CUPS was unable to find
/usr/libexec/cups/filter/rastertosamsungspl. I found that the driver installed
them in /usr/lib/cups/filter/ so I just created those symlinks: 

MindLess filter # pwd
/usr/libexec/cups/filter
MindLess filter # ls -l rastertosamsung*
lrwxrwxrwx 1 root root 39 jui 11 13:06 rastertosamsungpcl ->
/usr/lib/cups/filter/rastertosamsungpcl
lrwxrwxrwx 1 root root 39 jui 11 13:06 rastertosamsungspl ->
/usr/lib/cups/filter/rastertosamsungspl
lrwxrwxrwx 1 root root 40 jui 11 13:06 rastertosamsungsplc ->
/usr/lib/cups/filter/rastertosamsungsplc"

---

### Post by shanepardue on 2006-07-30
now i'm able to print, but the margins don't exist. i've checked the page i'm printing off and they're set correctly.

---

### Post by shanepardue on 2006-07-30
this is the solution..i tried many options and installing the printer this way is the only way to get this printer working.

[http://ubuntuforums.org/showpost.php?p=1244456&postcount=18](http://ubuntuforums.org/showpost.php?p=1244456&postcount=18)

---

### Post by Sabrage on 2007-05-10
Argh! I just bought this printer because it was supposed to be easy to install in Ubuntu. It's recognized correctly as ML-2010 but it's not printing anything, not even the test page is working. ](*,)

---

### Post by Whiffle on 2007-05-10
Hmmm.  I had zero problems installing this printer under feisty.  I opened up kcontrol (using KDE)> perhiphrials > printers, and added it as a USB printer, and I've been using it ever since.  

I've used the way that shanepardue did under slackware, and that should work as well.

---

### Post by Sabrage on 2007-05-10
Here's a weird thing: The printer is recognized correctly, and it's set to default. But the driver is set to Manufacturer:"Alps Md-1000" Driver:"ppmtomd" which are the two first options and when I change it to manufacturer "Samsung" with either driver "ML-2010" or driver "Samsung ML-2010" it just automatically changes back to "Alps MD-1000" and "ppmtomd" by the next time I check properties.... So if I'm not able to even choose the right driver then no wonder I can't print anything....

Is there a *gasp* file I can edit or something to make it use the driver I want?

---

### Post by Sabrage on 2007-05-13
I now have three strategies to get my printer working:

1) Install the missing filter:

[IMG]http://img82.imageshack.us/img82/4974/screenshotsamsungml2010kz5.png[/IMG]

This seems easy. I found this file on the CD-rom I got with the printer, but I don't know where to copy it. Anybody know?

2) Run the install script on the CD. There is an installscript on the CD (setup.sh), but you must be logged in as root to run it, but I don't event think I *have* a root account. So how can I run the setup script?

3) Install KDE. Whiffle got it working perfectly with KDE, so this could be an option. Will it mess up all my settings if I install KDE?

Thanks in advance for any help!

---

### Post by Sabrage on 2007-05-14
Sorry for bumping, but I'm at my wits' end! 

Just tried executing setup.sh from the CD, using the command ./sudo setup.sh in the terminal, but was told I did not have the needed permission. This I don'tunderstand because I thought I got all the permissions I needed with sudo?

Tried logging in as root to run the script from the CD, was then told the username or password was incorrect. (I don't think my root user is enabled because none of the options for root in "administration>users and groups" are checked. 

I installed the pdd file for ML-2010 from the CD, and got another driver to choose from. In addition to "ML_2010" I got "Samsung ML-2010". None of them works. The print job  is paused and I get the error in the post above, saying filter ppm2spl is not available.

[-o<

---

### Post by Sabrage on 2007-05-15
I downloaded the driver from the [_samsung website _]("http://www.samsung.com/support/productsupport/download/FileView.aspx?cttfileid=425024&type=Printer&typecode=300500&subtype=Laser+Printer&subtypecode=300501&cmssubtypecode=&model=ML-2010&filetype=DR&language=") but when I click on it I get this error from archive manager:

[[IMG]http://img466.imageshack.us/img466/2429/screenshoterrorsj0.png[/IMG]](http://imageshack.us)

:confused: 

Also tried copying the file ppm2spl2 (which I hoped was the filter it says it can't find, I found it on the CD that came with the printer) to /usr/share/cups/model/custom but no luck. I just don't get it...:confused:

---

### Post by Sabrage on 2007-05-28
Yes!! Finally!!

Don't really know why it suddenly started working, but today when I installed the new printer using the ML-4500 and gdi like briguy said in  [_this thread_]("http://ubuntuforums.org/showthread.php?t=65111"), everything was OK.  I also installed KDE and the driver from the Samsung homepage, but I'm not using KDE or that driver now. So thank you briguy and Whiffle and everyone!!

---

