---
title: "OOo fully functional in recovery mode but not in normal mode"
date: 2007-07-21
forum: General Help
---

### Post by jhattu on 2007-07-21
I have a problem with OpenOffice. I installed Ubuntu 7.04 and the OpenOffice that was packed with it on the same cd. Now I noticed that my OOo Calc is missing one command: MROUND. I really need that command for some calculation that I do. If I try to use the command, I get an error message. In addition, the command does not even appear on the list of usable commands. However, if I boot into recovery mode, the function works very well! 

As a linux newbie I might have done something (i.e. remove a package, etc.) bad for my computer. Still, the missing of MROUND is the only thing I have noticed to be wrong with my computer or OOo. I believe I should have all the packages needed by openoffice. The installed packages with the name openoffice on them are: > openclipart-openoffice.org                 0.18+dfsg-4
 openoffice.org                             2.2.0-1ubuntu4
 openoffice.org-base                        2.2.0-1ubuntu4
 openoffice.org-calc                        2.2.0-1ubuntu4
 openoffice.org-common                      2.2.0-1ubuntu4
 openoffice.org-core                        2.2.0-1ubuntu4
 openoffice.org-dev                         2.2.0-1ubuntu4
 openoffice.org-draw                        2.2.0-1ubuntu4
 openoffice.org-evolution                   2.2.0-1ubuntu4
 openoffice.org-filter-binfilter            2.2.0-1ubuntu4
 openoffice.org-filter-mobiledev            2.2.0-1ubuntu4
 openoffice.org-gnome                       2.2.0-1ubuntu4
 openoffice.org-gtk                         2.2.0-1ubuntu4
 openoffice.org-help-en-us                  2.2.0-0ubuntu2
 openoffice.org-hyphenation                 0.2           
 openoffice.org-impress                     2.2.0-1ubuntu4
 openoffice.org-java-common                 2.2.0-1ubuntu4
 openoffice.org-l10n-common                 2.2.0-0ubuntu2
 openoffice.org-l10n-en-gb                  2.2.0-0ubuntu2
 openoffice.org-l10n-en-za                  2.2.0-0ubuntu2
 openoffice.org-l10n-fi                     2.2.0-0ubuntu2
 openoffice.org-math                        2.2.0-1ubuntu4
 openoffice.org-style-andromeda             2.2.0-1ubuntu4
 openoffice.org-style-crystal               2.2.0-1ubuntu4
 openoffice.org-style-default               2.2.0-1ubuntu4
 openoffice.org-style-hicontrast            2.2.0-1ubuntu4
 openoffice.org-style-human                 2.2.0-1ubuntu4
 openoffice.org-style-industrial            2.2.0-1ubuntu4
 openoffice.org-style-tango                 2.2.0-1ubuntu4
 openoffice.org-thesaurus-en-us             2.0.4~rc1-3ubuntu1
 openoffice.org-voikko                      1.1-4build3
 openoffice.org-writer                      2.2.0-1ubuntu4

The list above was generated with the command dpkg -l | grep openoffice. Ofcourse there could be other libraries that OOo uses but are not named as "openoffice something". 

**So, my question is: if MROUND works in recovery mode, how could I make it work in normal mode too?** It looks like my computer eventually has all the libraries, but the normal mode somehow corrupts something so that this MROUND command (and who knows if there are other commands too) does not work.

---

### Post by prince_niceguy on 2007-07-21
start open office from command line in a terminal. this should show you the errors if any. I am no expert but looking at the error console some one would be able to help...:-)

---

### Post by jhattu on 2007-07-21
By starting from the command line I don't get any error messages.

I made a new discovery. If I boot from Ubuntu 7.04 live cd, the command MROUND in OOo works perfectly. I also used VirtualBox to create a new virtual hard disk and I installed Ubuntu to it (from the same cd). After hard drive installation, MROUND does not work any more. So this could be a bug in Ubuntu and not in my computer only?


So I am using OOo that came "out of the box" together with Feisty. Could someone confirm this bug? So, if you are using same configuration could you verify that MROUND works or not? For example if you write in Calc the followind:

=MROUND(7; 2)

do you get a result or just an error message? Thanks!

---

### Post by prince_niceguy on 2007-07-21
try reinstalling office. if that does not help then file a bug in launch pad. as open office work on my laptop in 7.04 so might be some issue with the configuration of ubuntu on your comp.

---

