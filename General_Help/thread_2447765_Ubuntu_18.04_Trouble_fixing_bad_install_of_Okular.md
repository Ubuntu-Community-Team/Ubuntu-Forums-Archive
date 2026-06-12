---
title: "Ubuntu 18.04: Trouble fixing bad install of Okular"
date: 2020-07-25
forum: General Help
---

### Post by nought2 on 2020-07-25
Soon after getting my system up and running last year I tried out various document viewer alternatives. 
Using the Ubuntu Software Manager I found two versions of Okular and made a hash of things by trying to install both.

Okular 4.17.12.3-0ubuntu1 is an old version available via ubuntu-bionic-universe.
Okular 20.04 is the latest version available via Snap Store.

Only v4.17 was able to be used. 

A weird manifestation of the mess I created could be seen by right clicking a pdf file > properties > open with.
Initially the icon for v4.17 was listed about 10 times, which probably relates to the number of times I initially attempted to install it all those months ago when I knew much less about what I was doing than the little I know now.

Tonight I tried unsuccessfully to clean up the mess and install v20.04 via Snap. I used a couple of online tutorials for guidance.

Here's a list of the various methods I tried.

dpkg-query -l | grep okular
...this found an "okular" package and a dependency "libokular5core8"
I removed both with the method:
sudo dpkg --remove Okular
sudo dpkg --remove libokular5core8

This was followed up with:
sudo apt remove okular
sudo apt purge okular
sudo apt-get remove okular
sudo apt-get clean
sudo apt-get autoremove

After doing all of that I remembered to check the Ubuntu Software Manager. It still claimed both versions were installed so I used the Software Manager's remove button for each. Both were claimed to have been removed.

After this I tried to install v20.04 via Snap from terminal:
sudo snap install okular

The snap install process completed normally but a problem remains. When I hit Super > search "Okular" the result is two icons. One is a generic diamond logo depicting gears meshing, the other is the icon for Okular 4.17. When clicked neither launches Okular.

Help with properly fixing my stuff up would be appreciated.

---

### Post by TheFu on 2020-07-25
Don't use dpkg directly to modify anything.  Stay with APT tools which managed dependencies.  Only use dpkg to gather information.

I can't help with menu stuff. Sorry, I don't use menus.
I also avoid snaps. They don't work on some of my systems for technical reasons the snap team is well aware concerning.  If there is an Okular AppImage or flatpak, you can check those out. Can't guarantee those will work, since the packages may not include all the dependencies for your system. I've run into that with snaps too.

---

### Post by monkeybrain20122 on 2020-07-25
You don't use apt or dpkg to remove snap packages, your steps just removed the .deb version of okular  (apparently only partially, see below) which is not the one causing you problems (and as theFu said dpkg is a bad idea anyway, should use apt)

```
sudo snap remove okular
```

should remove the okular snap.

To get rid all snap stuffs (maybe that's what you should do, just to clean up the mess, you can reinstall snapd with apt after)

```
sudo apt purge snapd
```

This will remove everything related to snap except configuration files in your $HOME, which you'll have to clean up manually (sudo updatedb then use locate okular, locate snap etc)

Another issue is that you might have messed up the deb version of okular as well by trying to be too clever (using dpkg followed by apt, dpkg only removed parts of it but it left  bits still registered with apt so instead of removing it cleanly it left you with something broken and apt gets confused.. something like that)  In that case just reinstall okular and then uninstall it with apt (or keep it if you want). 

But you should get synaptic instead of messing with commands that you apparently don't understand.
```
sudo apt install synaptic
```

---

### Post by nought2 on 2020-07-26
Thank you TheFu and monkeybrain for your replies.

To be clear, my aim here is to install and use the most up to date version of Okular. That is v20.04 which is available from Snap Store.

monkeybrain reckons the problem is caused by snap. That doesn't totally agree with what I see. When the latest Okular version (20.04) is installed via Snap Store it seems to conflict with remnants of the old version (4:17.12.3) installed via Ubuntu Software Manager. After attempting to remove the old version using apt and then installing the newest version via snap, at the very least the icon linking to the old version remains on the system.

Today I tried conservative methods to install and remove v4:17.12.3 and then install v20.04 via snap.

sudo snap remove okular
...To make sure snap version was not installed to the system.

sudo apt install okular
...This installed Okular 4:17.12.3-0ubuntu1 from ubuntu bionic/universe. Was able to launch it and use it to view files.

sudo apt remove okular
...To uninstall Okular. Came with notice that many packages were automatically installed and are no longer required.
sudo apt autoremove 
...To remove these redundant packages.

sudo snap install okular
...This completed successfully, however Okular will not launch.
Screenshot below shows what I get after hitting Super > search "okular"
[[ATTACH=CONFIG]286547[/ATTACH]]("https://postimg.cc/CdrMyHSX")

Following monkeybrain's suggestion I had a look at:
sudo apt purge snapd
...which produced this warning:
The following packages will be REMOVED:
  gnome-software-plugin-snap* snapd*

Searching "gnome-software-plugin-snap" pulled up an Ask Ubuntu query in which the OP had created problems with his system after doing "purge snapd". Removing gnome-software-plugin-snap broke the Ubuntu Software Manager front page and he was unable to fix it (presumably with the snap plugin absent).
[https://askubuntu.com/questions/1240831/removing-gnome-software-snap-plugin-breaks-gnome-software-storefront-on-ubuntu-1](https://askubuntu.com/questions/1240831/removing-gnome-software-snap-plugin-breaks-gnome-software-storefront-on-ubuntu-1)

After reading that I aborted apt purge snapd. I would only try it after taking the precaution to image my system.

If I was to do apt purge snapd and remove both snapd and gnome-software-plugin-snap, would installing both again via apt restore the function of snap and the Ubuntu Software Manager?

I had a look at the man page for updatedb but it was beyond my comprehension. Ditto man locate. I would need guidance to use them effectively and safely.

Removing snapd from the system seems like a heavy handed approach. 
Is there a lighter way to find and weed out what is causing this problem?

In my $HOME I saw two text files within its subfolder .config:
okularpartrc (0 bytes)
okularrc (745 bytes)
Searching .config also found numerous other files with name format:
okular_<random-character-string>

Would it be safe to delete these files before attempting to install Okular again?

---

### Post by Dennis N on 2020-07-26
> To be clear, my aim here is to install and use the most up to date version of Okular. That is v20.04 which is available from Snap Store.
The latest Okular version at the moment is 1.10.3
If you want to use the latest in Ubuntu 18.04, other than a Snap, you can get it as a Flatpak. I use the Flatpak in Ubuntu 18.04 and it works fine.

---

### Post by nought2 on 2020-07-26
> **Dennis N said:**
> The latest Okular version at the moment is 1.10.3
If you want to use the latest in Ubuntu 18.04, other than a Snap, you can get it as a Flatpak. I use the Flatpak in Ubuntu 18.04 and it works fine.
Another universal package format, very interesting.

Found two useful step-by-step guides to install it to Ubuntu:
[https://www.omgubuntu.co.uk/2019/02/how-to-install-flatpak-on-ubuntu-flathub](https://www.omgubuntu.co.uk/2019/02/how-to-install-flatpak-on-ubuntu-flathub)
[https://www.atechtown.com/how-to-install-and-use-flatpak-ubuntu-18-04/](https://www.atechtown.com/how-to-install-and-use-flatpak-ubuntu-18-04/)

Using bits from each I installed a list of relevant items:
-Flatpak
-Flatpak PPA
-Flatpak software plugin
-Flathub Repo
...and then restarted the system.

I then did this:```

~$ flatpak search okular
Name       Description         Application ID    Version    Branch    Remotes
Okular     Document Viewer     org.kde.okular    1.10.3     stable    flathub
```
The outlined installation method from terminal in the second guide led me to do this:```

~$ sudo flatpak install flathub org.kde.okular
[sudo] password for zen: 
Looking for matches&#8230;
Required runtime for org.kde.okular/x86_64/stable (runtime/org.kde.Platform/x86_64/5.14) found in remote flathub
Do you want to install it? [Y/n]: y

org.kde.okular permissions:
    ipc                   network       cups       pulseaudio
    wayland               x11           dri        file access [1]
    dbus access [2]

    [1] host, xdg-config/kdeglobals:ro
    [2] com.canonical.AppMenu.Registrar


        ID                                   Branch Op Remote  Download
 1.     org.freedesktop.Platform.GL.default  19.08  i  flathub  < 89.1 MB
 2.     org.freedesktop.Platform.VAAPI.Intel 19.08  i  flathub   < 8.7 MB
 3.     org.freedesktop.Platform.openh264    2.0    i  flathub   < 1.5 MB
 4.     org.kde.KStyle.Adwaita               5.14   i  flathub   < 6.0 MB
 5.     org.kde.Platform.Locale              5.14   i  flathub < 337.3 MB (partial)
 6.     org.kde.Platform                     5.14   i  flathub < 363.0 MB
 7.     org.kde.okular.Locale                stable i  flathub   < 3.1 MB (partial)
 8.     org.kde.okular                       stable i  flathub  < 54.0 MB

Proceed with these changes to the system installation? [Y/n]:
```
For the time being I have not proceeded. 

All of that adds up to an enormous download for a single application. Easily 850MB.

Have I done this correctly?

Regarding Okular versions, there is variation in the numerical naming system. The old version installed via apt was labelled 4:17.12.3-0ubuntu1 in the Ubuntu Bionic Universe repository. When installed its Help > About page labelled it 1.3.3. I have no idea how the Gnome Snap system came up with version 20.04 for what the Ubuntu Software manager offers. The version of Okular available from Flatpak, 1.10.3, seems to be right up to date.

---

### Post by TheFu on 2020-07-26
> **nought2 said:**
>  
All of that adds up to an enormous download for a single application. Easily 850MB.
 

That is one of the issues with all snaps, flatpaks, appimages. There are many others which may or may not matter/impact you.

Okular is a Qt-based tool, as seen by the KDE sub-packages.
Gnome uses a competing GTK+ toolkit. 

These are competing, but it is fine to have both on a single system, running at the same time. All they waste is RAM, storage, startup time, and CPU.  In return, we get packages which are supposed to be 100% self-contained enough to run on any supported Linux distro.  It doesn't always work that way, but recent and currently supported distros really should work.

---

### Post by Dennis N on 2020-07-26
You should go to:

[https://flathub.org/home](https://flathub.org/home)

where there is a '**quick setup**' link. Be sure you did all the steps, including installing the **gnome-software-plugin-flatpak** so Ubuntu Software (in 18.04) can detect updates and inform you of them.

Your command for install is correct. Go ahead and install! Okular is a KDE package, and need some KDE resources (called platforms) not found in the default  Ubuntu with Gnome Desktop. Later, if you install another KDE package, the resources needeed will already have been installed. The apt version would also need additional resources, all installed as separate dependencies which are a mess to clean up. With Flatpak, should you decide to uninstall an application, you can neatly remove any platform that's no longer used.

Okular - not just for PDFs - I use it as my epub reader.

---

### Post by nought2 on 2020-07-27
Thank you TheFu and Dennis N. 

Having read a little more about Flatpak it seems sensible to start using software distributed through this channel. Its cross Linux platform availability cuts through the fragmented array of OS choices, and it's quite straightforward to use. Both of which for end users like me are very good things.

The entire download to install Okular via Flatpak wasn't quite as large as I expected. Instead of 850MB it was only 750MB, cough.

Okular launches and works a treat. Happiness. 

Dennis N confirmed what I had surmised about the KDE resources necessary for Okular, that is they will be used for other KDE-origin flatpaks that are installed. I will have to live with the hit to system resources all that extra software aboard will cost. Hopefully it will only amount to a modest inconvenience.

This workaround has elegantly sidestepped what would have been a tricky and intricate clean-up to get Okular working via Snap. That issue can now rest. Ripping out snapd by the roots would likely have caused all kinds of problems with other Snaps installed. Just too hard. Ultimately it will be resolved when at some point in future I start again with a clean install of the latest version of Ubuntu. 18.04 is working alright so no need for that yet. 

Out of interest I searched for other snaps installed:```

~$ snap list
Name                             Version                     Rev   Tracking       Publisher    Notes
canonical-livepatch              9.5.5                       95    latest/stable  canonical&#10003;   -
core                             16-2.45.2                   9665  latest/stable  canonical&#10003;   core
core18                           20200707                    1880  latest/stable  canonical&#10003;   base
gnome-3-28-1804                  3.28.0-17-gde3d74c.de3d74c  128   latest/stable  canonical&#10003;   -
gtk-common-themes                0.1-36-gc75f853             1506  latest/stable  canonical&#10003;   -
gtk2-common-themes               0.1                         13    latest/stable  canonical&#10003;   -
kde-frameworks-5-core18          5.61.0                      32    latest/stable  kde&#10003;         -
kde-frameworks-5-qt-5-14-core18  5.68.0                      4     latest/stable  kde&#10003;         -
onlyoffice-desktopeditors        5.5.1                       43    latest/stable  onlyoffice&#10003;  -
p7zip-desktop                    16.02.2                     220   latest/stable  ernytech     -
pdftk                            2.02-4                      9     latest/stable  smoser       -

```Not sure if this is the correct way to find out which Snaps were installed by me. The results are odd. I'm pretty sure p7zip was installed from terminal using apt. Why would this search find it?

Dennis N, some months ago in another thread you helped me use LibreOffice via AppImage. I noticed LO is offered at flathub.org. Do you think running LO from a Flatpak is preferable to running it from AppImage? For one Flatpak should enable automatic updates, wouldn't it?

---

### Post by Dennis N on 2020-07-27
I'm glad to hear you're giving Flatpak a try. I've been very satisfied with those I've installed. 

When I did recent fresh installs of Ubuntu 20.04 LTS, I opted for the 'minimal install' option and then utilized Flatpak versions for a number of applications. That way, I always have the latest stable versions of those. 

I suggest installing Flatseal (a Flatpak) to manage permissions. I found some Flatpaks are by default too restrictive on access to a separate data disk or external media. 

I do use the LibreOffice Flatpak regularly. I like it and prefer it. 

AppImage format didn't seem to have a lot of offerings - I have a few of them (Etcher and Krita come to mind) but generally moved on to Flatpak or Snap.  

Based on my own observations, Flatpak applications are automatically updating in Ubuntu 20.04, but not earlier Ubuntu releases. Probably due to a newer Gnome Software Flatpak plugin in 20.04. If a Flatpak doesn't automatically update, you will see a notification about any software updates.

I DO have some snaps, and won't criticize them. Some things are only found as a snap. For example, I have Firefox ESR as a snap (no Flatpak is available), and my atari800 emulator is a snap (better than the repository version). The LibreOffice snap is fine too.

---

### Post by TheFu on 2020-07-27
Check out **snap list --all**.

Canonical has decided that certain software only available via snap will have "APT transisional packages" which get installed as snaps to make things easier on users.  Whenever APT asks "Y/n" to continue, look at the list of things to be installed. It should be clear.

In theory, snaps should all "just work" in the same way that flatpaks and AppImages should.  Installed a FreeMind snap and an XMind snap yesterday. Both needed manual changes to run over remote X11.  I run almost everything over X11 remotely. It was the same change each time, so it really should be automated as part of the snap environment setup.  Remote Wayland users (are there any?), would be using XWayland, so they'd have similar issues.

---

### Post by nought2 on 2020-07-27
Mostly I've enjoyed success with Flatpak apps I've tried but there have been fizzers too.

--Okular looks to be great. 

--Bitwarden has been the best by far. Was recommended to use it last year by a friendly local Ubuntu and FOSS wizard for secure storage of login credentials. Wow, it is just amazing. Flatpak is great, but Bitwarden deftly covers every other access option: slew of desktop OSes; web access; full complement of browser extensions (Firefox one is very slick); IOS and Android apps. Spent hours yesterday copying login credentials piecemeal from dodgy, not-encrypted notes kept in my web-based email account into new BW acct via Flatpak. Super pleased with it, the Flatpak and the service.

--Tried LibreOffice Flatpak today. Using it is pretty much the same as with the AppImage version I had. However... Opened a couple of LO Calc files and had to run its spell check to Add to Dictionary many words, terms and abbreviations. The Flatpak version does not save all terms I have added. When I redo the spell check, even after saving and closing the sheet and Flatpak LO and then resuming, some squiggly red underlining obstinately remains when the process has completed. One sheet has about 6 workbooks and many cells in all have large blocks of text. Moving down the chain to spell check each workbook, when doing the later ones launching of the spell check tool is very slow, it is slow to work too. I didn't experience these issues with any AppImage version I used. Could they be caused by a problem with file permissions?

There is also the problem of differentiating installed LO 6.0.7.3 native to 18.04 LTS (which is never updated in Ubuntu repos) from Flatpak LO 6.4.5.2 when launching via Super > "type to search". There is only a slight difference in the artwork of their respective icons. Workable but a little inconvenient.

--Flatseal. Very lightweight app in terms of its download size. I would not be able to manage permissions with it confidently, those names were all new and strange to me.

--Scans to PDF. The biggest fizzer. Wanted to try it as an alternative to gscan2pdf which does a wonderful job of extending the working life of my ancient Epson scanner. While Scans to PDF launches it will do nothing else, just a blank framed screen window, no menu options, nothing. Maybe scanner is to too old for it to recognise. Scanner stays asleep after Scans to PDF is launched. Ah well, happy to still have gscan2pdf.

--Installed a couple one-job apps that relied on gnome resources, Obfuscate (simple image redacting tool, too simple) and CoBang (QR code scanner). Gnome resources had to be downloaded for them to work. Which I thought was strange because Ubuntu is a gnome project.

When doing all this trying out I copied installation commands from Flathub.org. I noticed none of them were prefixed with sudo. Installation proceeds unhindered without it. I thought this was inconsistent with the usual emphasis on security in Unix-type OSes.

I ran ~$ flatpak update. Easy to do. It pulled down a few small sized updates for Flatpak itself. Every Flatpak app was brand new, there was nothing to do with them.

I tried [~$ snap list --all]: ```

~$ snap list --all
Name                             Version                     Rev   Tracking       Publisher    Notes
canonical-livepatch              9.5.5                       95    latest/stable  canonical&#10003;   -
canonical-livepatch              9.5.2                       94    latest/stable  canonical&#10003;   disabled
core                             16-2.45.1                   9436  latest/stable  canonical&#10003;   core,disabled
core                             16-2.45.2                   9665  latest/stable  canonical&#10003;   core
core18                           20200427                    1754  latest/stable  canonical&#10003;   base,disabled
core18                           20200707                    1880  latest/stable  canonical&#10003;   base
gnome-3-28-1804                  3.28.0-17-gde3d74c.de3d74c  128   latest/stable  canonical&#10003;   -
gnome-3-28-1804                  3.28.0-16-g27c9498.27c9498  116   latest/stable  canonical&#10003;   disabled
gtk-common-themes                0.1-30-gd41a42a             1502  latest/stable  canonical&#10003;   disabled
gtk-common-themes                0.1-36-gc75f853             1506  latest/stable  canonical&#10003;   -
gtk2-common-themes               0.1                         9     latest/stable  canonical&#10003;   disabled
gtk2-common-themes               0.1                         13    latest/stable  canonical&#10003;   -
kde-frameworks-5-core18          5.61.0                      30    latest/stable  kde&#10003;         disabled
kde-frameworks-5-core18          5.61.0                      32    latest/stable  kde&#10003;         -
kde-frameworks-5-qt-5-14-core18  5.68.0                      4     latest/stable  kde&#10003;         -
onlyoffice-desktopeditors        5.4.1                       38    latest/stable  onlyoffice&#10003;  disabled
onlyoffice-desktopeditors        5.5.1                       43    latest/stable  onlyoffice&#10003;  -
p7zip-desktop                    16.02.2                     220   latest/stable  ernytech     -
pdftk                            2.02-4                      9     latest/stable  smoser       -

```Result differs from [~$ snap list] only by inclusion of disabled items.

I checked my /home/snap folder. It had sub-folders for:
p7zip-desktop
onlyoffice-desktopeditors
okular
canonical-livepatch

Searching Ubuntu Software manager I saw that I had long ago installed the p7zip-desktop Snap. Other elements of p7zip that work from terminal and context menu were installed via apt. Only my own unreliable memory to blame there.

---

### Post by Dennis N on 2020-07-28
*--Okular looks to be great.*
I agree. 

*--Tried LibreOffice Flatpak today.*
I'm familiar with the similar icons to regular L.O. I uninstall the regular L.O.  The one icon I put in the Ubuntu Dock is the main LibreOffice icon with the distinct grey border that allows access to all the L.O. programs with a right-click.  I haven't used L.O. Calc. I've been using Gnumeric since my Linux beginnings back in 2007 and have stuck with it. 

*--Flatseal*
Sooner or later, if you use additional Flatpak, you will run into one that is more restrictive on location access that you want. For example, Flatpak for Bluefish wouldn't open/save files on my separate data disk, making it unusable for me. Not the only way (you can also use a flatpak terminal command), but Flatseal makes it easy.

*--Scans to PDF*
not familiar with this. 

*--Gnome apps*
I think Flatpak and Snap cannot access software libraries outside of Flatpak's and Snap's specific resource bundles. It's part of the security features (sandboxing) of these things.  

*--Flatpak installs without admin privileges.*
Same here. Maybe works this way if current user had admin (sudoer) privileges? 
[https://github.com/flatpak/flatpak/issues/1669](https://github.com/flatpak/flatpak/issues/1669)
I need to check if Fedora does this too.

*--updates*
Updates are usually small as well - only the code portion that needs changing is downloaded.

---

### Post by nought2 on 2020-07-28
> **Dennis N said:**
> 
*--Flatpak installs without admin privileges.*
Same here. Maybe works this way if current user had admin (sudoer) privileges? 
[https://github.com/flatpak/flatpak/issues/1669](https://github.com/flatpak/flatpak/issues/1669)
I need to check if Fedora does this too.
The logic explained in that Github link for Flatpak's use of admin privileges in Ubuntu is remarkably nuanced.
Weird that Flatpak's architects/engineers have decided to allow it to operate on trust after a remote has been approved by a sudoer when in other instances system wide effects always require admin password to proceed. Even system updates on 18.04 LTS must be done as sudo. The architects/engineers like the sandbox they have made.

*--LibreOffice Flatpak slow.*
After submitting my previous post today I downloaded the latest LO AppImage. It had been awhile between updates. 
LO Calc dictionary in new AppImage needed to be updated with neologisms from my spreadsheet. So I got to test it too.
The exact same slowdown seen with the Flatpak version happened with the AppImage. This indicates that the issue isn't with Flatpak, it's me. The spreadsheet in question serves largely as a diary with very large volumes of text. LO Calc probably isn't intended to be used that way.

I was sparked to open this thread by a problem I had with accessing embedded links in a pdf file. It's been an adventure! My usual document viewers on Ubuntu could not access the pdf's embedded links. However the pdf viewer in Firefox could, ditto the free version of Foxit Reader. Regrettably the Okular Flatpak couldn't. The others tried were qpdfview and Document Viewer.

I receive newsletters a few times a year from the publisher of the pdf in question. They are important newsletters. Embedded links in newsletters published prior to the problematic one were accessible. Checking their respective file properties, older newsletters were created with Acrobat PDFMaker 19 for Word. The newest one was created with Acrobat PDFMaker 20 for Word.

This thread doesn't seem to be the right place to discuss how to deal with misbehaving pdf files. That's a different topic. I'm open to suggestion of a better place to ask questions about this issue either on these forums or elsewhere.

---

### Post by TheFu on 2020-07-28
PDF files are written to be compatible with an industry, lead by Adobe, PDF level.  Adobe has continuously added new features, so the PDF file version has continued to increase.  For a long time, most F/LOSS tools used the same library with support for PDF v1.6 files.  This means that any PDF creation tool that uses a newer version of the PDF standard cannot be accessed by those tools.  

To see the specific version of PDF standard that a file uses, use the "file" command.
```
$ file 2009-Resume.pdf 
2009-Resume.pdf: PDF document, version 1.4
```

```
$ file *pdf
Brother_mfc240C_user_guide.pdf:                 PDF document, version 1.5
E14401_ROG_STRIX_B450-F_GAMING_UM_WEB.pdf:      PDF document, version 1.7
m500 mu02_smart_attributes.pdf:                 PDF document, version 1.5
pc-engines-w85329-shipped.pdf:                  PDF document, version 1.3
The_Linux_Command_Line-William_Shotts_1364.pdf: PDF document, version 1.5
```
Evince opens all those files, including the v1.7 file.

Ghostscript claims support for rendering of PDF v2.0 stuff, but not all other parts.
[https://www.adobe.com/devnet/pdf/pdf_reference.html](https://www.adobe.com/devnet/pdf/pdf_reference.html)

---

### Post by nought2 on 2020-07-28
Evince, which I earlier named Document Viewer, does not access embedded links in the problematic PDF.

I renamed two files to permit particulars to be shared here.

20191219.pdf ==> able to access embedded links
20200724.pdf ==> cannot access embedded links
```
$ file *pdf
20191219.pdf: PDF document, version 1.4
20200724.pdf: PDF document, version 1.4

```"pdfinfo" command reveals document info for the respective files:```
$ pdfinfo 20191219.pdf
Title:          PPPP
Subject:        QQQQ
Author:         RRRR
Creator:        Acrobat PDFMaker 19 for Word
Producer:       Adobe PDF Library 19.21.90
CreationDate:   Wed Dec 18 18:14:47 2019 AEDT
ModDate:        Thu Dec 19 13:20:11 2019 AEDT
Tagged:         yes
UserProperties: no
Suspects:       no
Form:           AcroForm
JavaScript:     no
Pages:          11
Encrypted:      no
Page size:      595.32 x 841.92 pts (A4)
Page rot:       0
File size:      2404379 bytes
Optimized:      no
PDF version:    1.4

```
```
$ pdfinfo 20200724.pdf
Title:          SSSS
Subject:        TTTT
Author:         RRRR
Creator:        Acrobat PDFMaker 20 for Word
Producer:       Adobe PDF Library 20.9.95
CreationDate:   Tue Jun 23 12:09:43 2020 AEST
ModDate:        Tue Jun 23 12:09:46 2020 AEST
Tagged:         yes
UserProperties: no
Suspects:       no
Form:           none
Syntax Error: Invalid object stream
Internal Error: xref num 730 not found but needed, try to reconstruct<0a>
JavaScript:     no
Pages:          6
Encrypted:      no
Page size:      595.32 x 841.92 pts (A4)
Page rot:       0
File size:      443527 bytes
Optimized:      yes
PDF version:    1.4

```

While both good and bad files are the same PDF version (an old one) each has been made with different producer and creator.
pdfinfo shows a couple of errors in bad file's info. 
Any idea what the problem might be?

Modified archive shows PDF versions used since 2009 lack rhyme or reason:```

$ file *pdf
20090322.pdf:           PDF document, version 1.4
20090812.pdf:           PDF document, version 1.3
20090907.pdf:           PDF document, version 1.3
20100317.pdf:           PDF document, version 1.4
20100521.pdf:           PDF document, version 1.4
20110905.pdf:           PDF document, version 1.4
20140925.pdf:           PDF document, version 1.5
20141214.pdf:           PDF document, version 1.5
20150801.pdf:           PDF document, version 1.5
20150810.pdf:           PDF document, version 1.6
20151116.pdf:           PDF document, version 1.5
20160506.pdf:           PDF document, version 1.6
20160915.pdf:           PDF document, version 1.5
20161220.pdf:           PDF document, version 1.5
20170518.pdf:           PDF document, version 1.7
20170925.pdf:           PDF document, version 1.6
20171002.pdf:           PDF document, version 1.6
20171101.pdf:           PDF document, version 1.7
20171201.pdf:           PDF document, version 1.5
20171222.pdf:           PDF document, version 1.5
20180328.pdf:           PDF document, version 1.6
20180527.pdf:           PDF document, version 1.6
20180927.pdf:           PDF document, version 1.5
20181023.pdf:           PDF document, version 1.6
20181221.pdf:           PDF document, version 1.7
20190329.pdf:           PDF document, version 1.6
20190628.pdf:           PDF document, version 1.6
20191011.pdf:           PDF document, version 1.6
20191219.pdf:           PDF document, version 1.4
20200623.pdf:           PDF document, version 1.4
20200724.pdf:           PDF document, version 1.4

```All over the shop.

---

### Post by TheFu on 2020-07-28
My only guess is that v20 of  Acrobat PDFMaker is creating different types of links than v19 does.  There are changes in the PDF v2.0 standard, so you may have found a bug, since embedded linking has been part of the PDF standard since at least 1994 - of that I'm 100% positive.

Flatpak and snaps both run in constrained environments for security and Adobe PDF files have a long history of security failures - most adobe products have security failures.  Running any PDF viewer outside some sort of constrained environment is not something I would do, but that does explain why firefox works and the flatpak versions don't.  I don't know much about flatpak constraints besides that the local admin can relax those using a tool.  Have you tried that?  

I'm positive that with snaps, we can only enable capabilities, called "connections", that the snap package creator enabled, but that all snaps must be constrained to be distributed. There's no way to disable constraints in snaps.  The **snap connections <application-name> command** should show the available connections for any snap package.

---

### Post by nought2 on 2020-07-29
> **TheFu said:**
> My only guess is that v20 of  Acrobat PDFMaker is creating different types of links than v19 does.  There are changes in the PDF v2.0 standard, so you may have found a bug
Quite possible. 
Where could it be reported? 

Re Flatpaks and Snaps, this problem is not restricted to them.

Evince, qpdfview and Okular 1.3.3, all installed via apt, were unable to recognise embedded links in the bad file. Okular 1.10.3 Flatpak exhibits the same behaviour seen in installed apps. 

The apps I've tried on 18.04 where the links do work are: Firefox incorporated PDF viewer, Foxit Reader free, and Master PDF Editor. All of them are installed.

The issue manifests only with smaller scale open source offerings.

---

### Post by TheFu on 2020-07-29
```
Creator:        Acrobat PDFMaker 20 for Word
Producer:       Adobe PDF Library 20.9.95
...
Syntax Error: Invalid object stream
Internal Error: xref num 730 not found but needed, try to reconstruct<0a>
```

is where I'd start the hunt for bugs.  Just because some PDF software handles the files, that doesn't mean they are following the standard.  Or perhaps it does?  If all Acrobat PDFMaker 20 for Word documents with links cause  the above errors and that causes the different PDF programs problems, consistently, just pointing that out to each upstream project would be helpful.  They will want the smallest PDF file which shows the issue as an example.

Of course, it could be an issue in the pdfinfo tool.

If you open the files using one of the tools where it works, then save it to a slightly different PDF v1.x format, does that "fix" the problem?

---

### Post by nought2 on 2020-07-29
Bug reports submitted to:

-- gitlab.gnome.org/GNOME/evince/
-- bugs.kde.org/
-- bugs.launchpad.net/qpdfview

---

### Post by nought2 on 2020-07-29
> **TheFu said:**
> 
If you open the files using one of the tools where it works, then save it to a slightly different PDF v1.x format, does that "fix" the problem?I didn't know it was possible to change PDF version format.
I thought document viewers were read only. 

How is it done? Would PDF maker/creator software do it?

Bug report to GNOME Evince has already received a response:
[https://gitlab.gnome.org/GNOME/evince/-/issues/1464](https://gitlab.gnome.org/GNOME/evince/-/issues/1464)

He was able to reproduce problem with latest version of Evince.

Didn't realise how far behind 18.04 is already. It's installed Evince version is "ancient software" !

---

### Post by TheFu on 2020-07-29
> **nought2 said:**
>  
Didn't realise how far behind 18.04 is already. It's installed Evince version is "ancient software" !

That's common for a dev team to say.  In their minds, anything over 3 months ago is.

For me, stability is more important than "new."  Most systems here are still on 16.04, though I have (1) 20.04 VM where I see some of the pain for new software and the new OS issues.  For certain, 16.04 had lots of issues when it first came out. Either they were solved or I learned to get around them.

If "new" is more important to you, seek out a PPA with the newer version.

---

### Post by Dennis N on 2020-07-30
**&#8680;** nought2

I checked out the Okular Snap. It installed without any problem, but as you report, it had two icons in the overview search result. Both launched Okular. I found this was because there were two .desktop files for the program:

```
dmn@Sydney-VM:/var/lib/snapd/desktop/applications$ ls | grep okular
okular_okular.desktop 
okular_org.kde.okular.desktop

```
I renamed the the second (has the gear icon) as okular_org.kde.okular.hide and it no longer appears. I imagine it could reappear in an update, though. 

Okular suffers from this theming 'bug':

'Snaps don't honor the system theme'
[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1585332](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1585332)

The Okular snap works, but you have to put up with a peculiar file chooser in how you navigate to a file to open. I found no way to bookmark a folder to make this simpler.

Hopefully, improvements will come for any Okular Snap users.

---

### Post by nought2 on 2020-07-30
> **TheFu said:**
> That's common for a dev team to say.  In their minds, anything over 3 months ago is.

For me, stability is more important than "new."  Most systems here are still on 16.04, though I have (1) 20.04 VM where I see some of the pain for new software and the new OS issues.  For certain, 16.04 had lots of issues when it first came out. Either they were solved or I learned to get around them.

If "new" is more important to you, seek out a PPA with the newer version.
In May 2020 after getting wind of the imminent release of Ubuntu 18.04 LTS I had a crack at a system upgrade to a development release before the real-deal 20.04.1 was let loose. The upgrade thoroughly trashed my system. Not to worry, I had prepared by making a system image first. An important lasting benefit of the experience was learning how to stop upgrades getting pushed at my system from repositories. There will be no accidental upgrade nightmares.

Edit the configuration file:
> ```
/etc/update-manager/release-upgrades
```Here, you can check the line *Prompt=XXXX*, whereby:
    
[LIST]
[*]never &#8211; no upgrades will be offered. 
[*]normal &#8211; supported release that immediately succeeds the currently running release will be offered. 
[*]lts &#8211; LTS releases will be offered. 
[/LIST]
To use 20.04 LTS would require a fresh and clean install. On top of that I'd have to add and build all the bits and pieces that make my 18.04 system largely a pleasure to use. I've had 18.04 running for about a year. I've found it to be a very reliable and stable operating system. It is going alright, and I see from the steady stream of updates coming down the pipe that it is being continuously improved. There is no need for me to change it. I might consider doing that next year though, or even later.

My approach to installed software is different. LibreOffice, for example, undergoes constant development. The effort applied appears to be massive. The version installed to 18.04 was never upgraded via sudo apt update, sudo apt upgrade. Thanks to Dennis N I became aware of other upgrade channels for LO. First it was AppImage, and in this thread Flatpak. They take me where I want to be with LO, running ever improved and refined versions. 

For some tools I subscribe to PPAs. On example is gscan2pdf. My user experienced with it has at times been noticeably improved by versions installed via the developer's PPA.

This approach does not have me recklessly teetering over a bleeding edge or anything like that.

---

### Post by nought2 on 2020-07-30
> **Dennis N said:**
> I checked out the Okular Snap. It installed without any problem, but as you report, it had two icons in the overview search result. Both launched Okular. I found this was because there were two .desktop files for the program:

```
dmn@Sydney-VM:/var/lib/snapd/desktop/applications$ ls | grep okular
okular_okular.desktop 
okular_org.kde.okular.desktop

```
I tried running that command, got nothing, then realised I had removed the Okular Snap.
As mentioned earlier, I've given up on trying to get it working. Okular Flatpak will serve me nicely.
There is some solace in knowing some of the weirdness on my system was caused by a documented bug.

Reading through this thread again yesterday I realised I'd overlooked a change you'd made with handling the LO version installed from Ubuntu repos (6.0.7.3). Just uninstall it. Yesterday I looked up how to do that from terminal. 

Series of commands:```
~$ sudo apt-get remove --purge libreoffice*
~$ sudo apt clean
~$ sudo apt-get autoremove
```Now its gone.

There's no longer any confusion with stray icons for an LO version I didn't use getting pulled up by Super > search "libre"
LO Flatpak is working out well for me.

Should have realised there is PPA for LO that will install 'fresh' versions to 18.04:```
~$ sudo add-apt-repository ppa:libreoffice/ppa
```

---

### Post by Dennis N on 2020-07-31
> Should have realised there is PPA for LO that will install 'fresh' versions to 18.04
It's not surprising that there is one. But a PPA is only for Ubuntu, not other distros like Fedora, Arch Linux, or Manjaro. 
 
I do use the PPA for the **flatpak** application. It gives you the latest version, 1.8.1, while Ubuntu 20.04 offers version 1.6.3-1
The maintainer Alex Larsson is one of the Flatpak developers, so I trust this particular PPA. 

Otherwise, I don't use PPAs.  

There is at the moment a big difference in usability between the Snap and Flatpak versions of Okular - Flatpak has the edge on usability here. 
But, that's not always true. Snaps of LibreOffice, Inkscape, Gimp, and Firefox for example, I consider as good as the Flatpak versions.

---

### Post by nought2 on 2020-07-31
> **Dennis N said:**
> The maintainer Alex Larsson is one of the Flatpak developers, so I trust this particular PPA.It's delectably appropriate Flatpak was developed and named by someone with a Scandinavian name.

An irony in the name struck me when I was agog at the scale of the download needed to install Okular Flatpak. When shopping for things for your abode you might find yourself wandering around inside a cavernous Scandinavian homeware emporium. You select suitable bookshelves, desk, table, whatever, load the flatpacked cartons into your wagon to take home, then fiddle around with Allen keys for a few hours while assembling them. The items start small and finish big.

Flatpak software is not quite the same. After choosing a small item you take it home. When assembling the package its instructions tell you it needs a lot of other stuff that wasn't mentioned back at the megastore. To finish the job you wind up having to drag back a huge chunk of the cavernous emporium too and somehow stuff it into your house. The items start pretty big and get much much bigger!

Yeah, Flatpak is a great name.

Earlier in the thread you mentioned Firefox ESR. Until I built a new system last year it was FF ESR 52.9.0 that kept me remotely in touch with the internet while I doggedly slogged along with WinXP. Changes to FF extension design meant there would be no more extension updates for 52.9.0, which forced a timely end to that long serving venerable old box.

Ubuntu has markedly expanded my FF experience. It enables me to run multiple profiles concurrently. That's really useful. It might be possible to do it in Windows environment nowadays as well, but in XP it was fiddly to setup and I never got around to doing it. In Ubuntu it's as simple as running "firefox -p" (launches FF profile manager) from a new terminal instance and you're away.

Returning to Firefox  as a Snap, ESR or main release, is it possible to use multiple profiles with the Snap format?
Where is the profile folder located?

Curious to see how many PPAs I have subscribed to I ran:```
~$ apt-cache policy | grep http | grep ppa
 500 http://ppa.launchpad.net/unit193/encryption/ubuntu bionic/main i386 Packages
 500 http://ppa.launchpad.net/unit193/encryption/ubuntu bionic/main amd64 Packages
 500 http://ppa.launchpad.net/micahflee/ppa/ubuntu bionic/main i386 Packages
 500 http://ppa.launchpad.net/micahflee/ppa/ubuntu bionic/main amd64 Packages
 500 http://ppa.launchpad.net/jeffreyratcliffe/ppa/ubuntu bionic/main i386 Packages
 500 http://ppa.launchpad.net/jeffreyratcliffe/ppa/ubuntu bionic/main amd64 Packages
 500 http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu bionic/main i386 Packages
 500 http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu bionic/main amd64 Packages
 500 http://ppa.launchpad.net/adamreichold/qpdfview-dailydeb/ubuntu bionic/main i386 Packages
 500 http://ppa.launchpad.net/adamreichold/qpdfview-dailydeb/ubuntu bionic/main amd64 Packages

```Veracrypt, Onion Share, gscan2pdf, Flatpak, qpdfview.

That's not an excessive indulgence.
Risks to system security? With these I think it is minimal.

---

### Post by Dennis N on 2020-07-31
> Returning to Firefox as a Snap, ESR or main release, is it possible to use multiple profiles with the Snap format?

I've seen a notice when installing the Firefox Snap while the regular Firefox is still there. Essentially, it says the new install will have a new profile which allows them to coexist, and they do. I would think that extends to a different Snap version from a different Snap channel. 

For example, you could run Firefox Snap from latest/stable alongside the version from latest/beta.
On this computer, there is a regular Firefox + a Snap version, and there are two profiles in ~/.mozilla/firefox.

Current state of Firefox Snap:

```
channels:
  latest/stable:    79.0-1       2020-07-30 (398) 171MB -
  latest/candidate: 79.0-1       2020-07-27 (398) 171MB -
  latest/beta:      80.0b2-1     2020-07-31 (402) 171MB -
  latest/edge:      &#8593;                                   
  esr/stable:       68.11.0esr-1 2020-07-27 (400) 221MB -
  esr/candidate:    78.1.0esr-1  2020-07-27 (399) 170MB -
  esr/beta:         &#8593;                                   
  esr/edge:         &#8593;                                   

``` 

As to the PPAs, if I can get the same end result (latest version) I am going with the Flatpak.

I found this article yesterday - you might find it of interest:

[Flatpak: A Containerized Approach to Developing Linux Applications]("https://www.linux.com/news/flatpak-containerized-approach-developing-linux-applications/")

---

### Post by nought2 on 2020-08-03
> **Dennis N said:**
> I found this article yesterday - you might find it of interest:

[Flatpak: A Containerized Approach to Developing Linux Applications]("https://www.linux.com/news/flatpak-containerized-approach-developing-linux-applications/")
The Flatpak developers have certainly solved a lot of problems for app developers. It puts them in control of their product in so many ways. App release can be independent of distro release. That would be a huge obstacle for app developers. Small wonder there is only one Okular .deb package for Ubuntu 18.04, for example, or only only one .deb package of LibreOffice for 18.04. Too much work to go back and do all that testing again, especially when testing has to be done on apps for each annual distro release for several distros. 

Then there is Flatpak making multiple runtimes available in parallel. Dependencies can be provided by app or underlying distro. Flatpak devs have sorted out distribution. And it was designed from first principles for cross-distro compatibility. It all adds up to a compelling alternative for app developers. It looks set for the long haul.

I hadn't realised Canonical was behind Snap and that some elements of Snap are tied to Ubuntu. It will be interesting to see if its adoption increases once it has become truly decoupled from Ubuntu. The more cross-distro application distribution channels there are, the easier Linux in general becomes to use.

A day or two back I had another Flatpak update experience. Regrettably I neglected to copy the terminal display. Three packages were updated, the only one I recall was Bitwarden. Flatpak warned its update download was going to be <70MB. Only something like 5MB was actually downloaded. It was a similar story with the other two updates. Warning for them was in the order of <350M. Only about a tenth of that was downloaded for each. It's a very efficient system to allow update downloads to be so modestly sized.

> **Dennis N said:**
> I've seen a notice when installing the Firefox Snap while the regular  Firefox is still there. Essentially, it says the new install will have a  new profile which allows them to coexist, and they do. I would think  that extends to a different Snap version from a different Snap channel. 

For example, you could run Firefox Snap from latest/stable alongside the version from latest/beta.
On this computer, there is a regular Firefox + a Snap version, and there are two profiles in ~/.mozilla/firefox.
It's interesting that FF Snap has its profile stored in ~/.mozilla/firefox, same place as installed FF profiles are stored by default. 

It's useful that FF Snap can be run concurrently with installed FF. My query regarding FF ESR Snap was whether two or more of those profiles could be run concurrently via Snap as I do with installed FF via terminal. I imagine it would be tricky. I wonder if FF Snap's profile manager can be launched? That would be handy.

Prior to participating in this thread I hadn't realised different Snap channels were possible for a given application. Elsewhere I have seen that the desired channel can be selected via Ubuntu Software centre's GUI by clicking the green button in the "Details" section of an app's listing page. How can the desired channel be selected when a Snap is installed via terminal?

---

### Post by Dennis N on 2020-08-03
Disregard statements about the Firefox Snap profile location. Now I don't see any in ~/.mozilla/firefox, except for the default Firefox. After installing a Firefox Snap, it clearly doesn't use the existing one as things need to be configured again. 

More on parallel installs of the same snap application from two channels: This is a new possibility - learn about it here:
[Snappy Lets You Install Multiple Versions of the Same Snap App]("https://www.omgubuntu.co.uk/2019/06/snappy-now-lets-you-install-multiple-versions-of-the-same-snap-app")
According to the article, simultaneous use of two versions is not recommended. 

> How can the desired channel be selected when a Snap is installed via terminal? 
_Examples_
Install Firefox ESR:
```
snap install --channel=esr/stable firefox
```
Change Firefox to Firefox ESR using terminal commands (from my notes, with output):
```
snap switch --channel=esr/stable firefox
"firefox" switched to the "esr/stable" channel
snap refresh firefox
firefox (esr/stable) 68.9.0esr-1 from Mozilla&#10003; refreshed

```

---

### Post by nought2 on 2020-08-03
> **Dennis N said:**
> Disregard statements about the Firefox Snap profile location. Now I don't see any in ~/.mozilla/firefox, except for the default Firefox. After installing a Firefox Snap, it clearly doesn't use the existing one as things need to be configured again.It makes more sense for the profile to be kept within the same container as the FF Snap it belongs to.
> **Dennis N said:**
> More on parallel installs of the same snap application from two channels: This is a new possibility - learn about it here:
[Snappy Lets You Install Multiple Versions of the Same Snap App]("https://www.omgubuntu.co.uk/2019/06/snappy-now-lets-you-install-multiple-versions-of-the-same-snap-app")
According to the article, simultaneous use of two versions is not recommended.Thanks for this link. This is a useful feature, esp with FF where different profiles are often necessary for different roles. I hope the parallel-instances feature shifts from experimental to permanent.

Parallel-instances doesn't permit use of different iterations of the same Snap concurrently, that's OK. For FF Snap to have the potential to access different profiles by any other means is a close second.

For Firefox in MS Windows environments I have exclusively used the Portable Apps version for donkey's years. It's no-install, operates from a file, doesn't put its hooks into the system, can be removed cleanly & simply, which is similar to ambitions of AppImage, Flatpak, and Snap in Linux. I had multiple FF Port iterations each with a different profile. Years ago I learnt how to transfer profiles into FF Port copied from elsewhere. Still rely on this when I use Win10, can take FF profiles from Ubuntu with me.

I will have to play with Firefox Snap or Firefox ESR Snap sometime to see if I can locate where it stores the FF profile in Ubuntu. It would be useful to be able to save or substitute the profile of a FF Snap iteration.

Clues: [Profile Manager - Create, remove, or switch Firefox profiles]("https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles")
Same methods would surely reveal path to FF Snap profile.

Thank you for the "snap install" and "snap switch" examples.

After switching FF channels does the refreshed FF use the same profile as the original did for that Snap iteration? Or does it begin again with a vanilla profile?

---

### Post by Dennis N on 2020-08-04
_Profile for Snaps:_
Firefox Snap profile location:  ~/snap/firefox/common/.mozilla/firefox/

As I recall, after changing the tracking channel I did not need to re-do any settings, so same profile.

---

### Post by nought2 on 2020-08-04
Just attempted to install Firefox Snap. 

Installation process via terminal proceeded normally.```
~$ snap install --channel=latest/stable firefox
firefox 79.0-1 from Mozilla&#10003; installed
```
But on attempting to launch FF Snap it crashes with this munged report:
[ATTACH=CONFIG]286601[/ATTACH]

I've come full circle in this thread. If I want to use Snap packages something will need to be repaired.

After imaging the system I'll remove all Snap components and installed Snaps, purge snapd, then reinstall snapd and see if I can get Snaps to install and work.

---

### Post by Dennis N on 2020-08-04
That's not a helpful error message. I've not had any error messages with installing or running snaps, so can't offer any useful help in that regard. Your idea may be the quickest route in the end.

---

### Post by nought2 on 2020-08-05
My efforts were were unsuccessful.

Sequence of commands went like this:
```
~$ snap list  (to list installed snap packages)
~$ sudo snap remove <package> (all packages removed except "core 16-2.45.2", it cannot be removed)
~$ sudo snap purge snapd
~$ sudo apt autoremove
~$ rm -rf ~/snap  (remove /snap folder and its content from ~/home)

==> Restart system

~$ sudo apt install snapd
~$ sudo apt install gnome-software-plugin-snap  
~$ sudo apt update
~$ sudo apt upgrade

==> Restart system
```
At this point no Snaps were installed:```
~$ snap list
No snaps are installed yet. Try "snap install hello-world"
~$ sudo snap install hello-world
```
After installing "hello-world" the "snap list" command output included only "core 16-2.45.2" and the test snap "hello-world".

I installed pdftk Snap. It's a simple command line tool. As far as I could tell it worked normally.

Then I installed Okular Snap and Firefox Snap. Each installation was concluded with a long pause while this notice displayed:
"Automatically connecting eligible plugins and slots of snap "package_name" "
Snap output claimed both installed successfully but neither would launch. Launch attempts produced the errors below:```
~$ snap install okular
okular 20.04.0 from KDE&#10003; installed

~$ snap run okular
[error] cannot open locale definition file `en': No such file or directory
Qt: Session management error: None of the authentication protocols specified are supported
Icon theme "Adwaita" not found.
Fontconfig warning: FcPattern object width does not accept value [75 100)
Segmentation fault (core dumped)
``````
~$ snap run firefox
Gtk-Message: 15:08:14.204: Failed to load module "canberra-gtk-module"
Gtk-Message: 15:08:14.205: Failed to load module "canberra-gtk-module"
Sandbox: /tmp/.X11-unix/X1 is inaccessible (No such file or directory); can't isolate network namespace in content processes
Gtk-Message: 15:08:14.969: Failed to load module "canberra-gtk-module"
Gtk-Message: 15:08:14.970: Failed to load module "canberra-gtk-module"
ExceptionHandler::GenerateDump cloned child 4327
ExceptionHandler::SendContinueSignalToChild sent continue signal to child
ExceptionHandler::WaitForContinueSignal waiting for continue signal...
Exiting due to channel error.

~$ Gtk-Message: 15:08:15.149: Failed to load module "canberra-gtk-module"
Gtk-Message: 15:08:15.150: Failed to load module "canberra-gtk-module"

```Firefox launch attempt was accompanied by same munged crash report window posted yesterday.

Any clues on how to get Snap working properly?

Launch problems did not affect all installed Snaps. The GUI interfaces of p7zip-desktop and onlyoffice-desktopeditors lauched and functioned normally. No idea why they were spared from launch failure errors.

---

### Post by Dennis N on 2020-08-05
Here's my snap list from this computer (has Okular snap). Since yours 'sometimes works', compare your packages (other than applications) with mine. Install any you don't have one at a time and test again. This worked in another thread where one needed package was somehow not installed for that user. 

```
dmn@Sydney-VM:~$ snap list
Name                             Version                     Rev   Tracking         Publisher   Notes
atari800-jz                      3.1.0-0                     1     latest/stable    jz          -
chromium                         84.0.4147.105               1244  latest/stable    canonical&#10003;  -
core                             16-2.45.2                   9665  latest/stable    canonical&#10003;  core
core18                           20200707                    1880  latest/stable    canonical&#10003;  base
firefox                          79.0-1                      398   latest/stable    mozilla&#10003;    -
gnome-3-26-1604                  3.26.0.20200529             100   latest/stable/&#8230;  canonical&#10003;  -
gnome-3-28-1804                  3.28.0-17-gde3d74c.de3d74c  128   latest/stable    canonical&#10003;  -
gnome-3-34-1804                  0+git.3009fc7               36    latest/stable    canonical&#10003;  -
gnome-calculator                 3.36.0+git9.96b95fd2        748   latest/stable/&#8230;  canonical&#10003;  -
gnome-characters                 v3.34.0+git8.a46106b        550   latest/stable/&#8230;  canonical&#10003;  -
gnome-logs                       3.34.0                      100   latest/stable/&#8230;  canonical&#10003;  -
gnome-system-monitor             3.36.0-12-g35f88a56d7       148   latest/stable    canonical&#10003;  -
gtk-common-themes                0.1-36-gc75f853             1506  latest/stable    canonical&#10003;  -
kde-frameworks-5-qt-5-14-core18  5.68.0                      4     latest/stable    kde&#10003;        -
okular                           20.04.0                     98    latest/stable    kde&#10003;        -
qogir-themes                     2020-02-26-25-g660f92c      2     latest/stable    gantonayde  -
quadrapassel                     3.36.02+git2.7edd2a1        283   latest/stable    canonical&#10003;  -
snap-store                       3.31.1+git187.84b64e0b      415   latest/stable    canonical&#10003;  -


```

_Comments_:
Okular probably wouldn't need any of the 'gnome' items, but Firefox might. 
Also, 'gtk-common-themes' package should contain Adwaita theme that appears in one message.

One thing I haven't discovered about Snaps is how to determine if there are any unneeded resource packages here that could be removed. That's possible in Flatpak.

_Added comment_:
The Okular snap (rev 98) is ver. 1.10.0 with a date 23 Apr 2020 - somewhat older than the Flatpak.

---

### Post by nought2 on 2020-08-05
This was the snap list output before I performed the process of commands to remove all Snaps and snapd:```
~$ snap list
Name                             Version                     Rev   Tracking       Publisher    Notes
canonical-livepatch              9.5.5                       95    latest/stable  canonical&#10003;   -
core                             16-2.45.2                   9665  latest/stable  canonical&#10003;   core
core18                           20200707                    1880  latest/stable  canonical&#10003;   base
firefox                          79.0-1                      398   latest/stable  mozilla&#10003;     -
gnome-3-28-1804                  3.28.0-17-gde3d74c.de3d74c  128   latest/stable  canonical&#10003;   -
gnome-3-34-1804                  0+git.3009fc7               36    latest/stable  canonical&#10003;   -
gtk-common-themes                0.1-36-gc75f853             1506  latest/stable  canonical&#10003;   -
gtk2-common-themes               0.1                         13    latest/stable  canonical&#10003;   -
kde-frameworks-5-core18          5.61.0                      32    latest/stable  kde&#10003;         -
kde-frameworks-5-qt-5-14-core18  5.68.0                      4     latest/stable  kde&#10003;         -
onlyoffice-desktopeditors        5.5.1                       43    latest/stable  onlyoffice&#10003;  -
p7zip-desktop                    16.02.2                     220   latest/stable  ernytech     -
pdftk                            2.02-4                      9     latest/stable  smoser       -
```
After removing all Snaps and snapd I thought it would be best to install Snaps again from scratch so they could establish necessary relationships or connections with other elements of the OS as part of the install process, and for additional components to be downloaded and installed together with Snap. 

This was the output of snap list before additions were made tonight:
```
~$ snap list
Name                             Version          Rev   Tracking       Publisher   Notes
core                             16-2.45.2        9665  latest/stable  canonical&#10003;  core
core18                           20200707         1880  latest/stable  canonical&#10003;  base
firefox                          79.0-1           398   latest/stable  mozilla&#10003;    -
gnome-3-34-1804                  0+git.3009fc7    36    latest/stable  canonical&#10003;  -
gtk-common-themes                0.1-36-gc75f853  1506  latest/stable  canonical&#10003;  -
hello-world                      6.4              29    latest/stable  canonical&#10003;  -
kde-frameworks-5-qt-5-14-core18  5.68.0           4     latest/stable  kde&#10003;        -
okular                           20.04.0          98    latest/stable  kde&#10003;        -
pdftk                            2.02-4           9     latest/stable  smoser      -
```
gtk-common-themes is already installed but Okular Snap cannot find/use its Adwaita theme.

I installed additional Snap components. 
Here is the current output of snap list after making additions:```
~$ snap list
Name                             Version                     Rev   Tracking       Publisher   Notes
core                             16-2.45.2                   9665  latest/stable  canonical&#10003;  core
core18                           20200707                    1880  latest/stable  canonical&#10003;  base
firefox                          79.0-1                      398   latest/stable  mozilla&#10003;    -
gnome-3-26-1604                  3.26.0.20200529             100   latest/stable  canonical&#10003;  -
gnome-3-28-1804                  3.28.0-17-gde3d74c.de3d74c  128   latest/stable  canonical&#10003;  -
gnome-3-34-1804                  0+git.3009fc7               36    latest/stable  canonical&#10003;  -
gtk-common-themes                0.1-36-gc75f853             1506  latest/stable  canonical&#10003;  -
gtk2-common-themes               0.1                         13    latest/stable  canonical&#10003;  -
hello-world                      6.4                         29    latest/stable  canonical&#10003;  -
kde-frameworks-5                 5.47.0                      27    latest/stable  kde&#10003;        -
kde-frameworks-5-core18          5.61.0                      32    latest/stable  kde&#10003;        -
kde-frameworks-5-qt-5-14-core18  5.68.0                      4     latest/stable  kde&#10003;        -
okular                           20.04.0                     98    latest/stable  kde&#10003;        -
pdftk                            2.02-4                      9     latest/stable  smoser      -
snap-store                       3.31.1+git187.84b64e0b      415   latest/stable  canonical&#10003;  -

```For thoroughness I removed and reinstalled Okular Snap. When I attempted to run it I got the same error message in terminal. I did not remove and reinstall Firefox Snap; trying to run it from terminal produced same error message as before too.

_Response to additional comment_
I'm not fussed about having Okular Snap. Okular Flatpak already works well. Here I'm using Okular Snap to demonstrate the problem I'm having with Snap on my system.

Trial of snap-store did not produce a happy result. Characters were blocked out as in FF crash report. See screenshot:
[ATTACH=CONFIG]286616[/ATTACH]
Launch output from terminal:```
~$ snap run snap-store
14:25:45:0250 Gs  enabled plugins: odrs, rewrite-resource, snap, icons, key-colors, key-colors-metadata
14:25:45:0250 Gs  disabled plugins: appstream, desktop-categories, desktop-menu-path, dpkg, dummy, epiphany, fedora-pkgdb-collections, generic-updates, hardcoded-blacklist, hardcoded-featured, hardcoded-popular, modalias, os-release, provenance, provenance-license, repos, shell-extensions
14:25:51:0347 Gs  failed to create an app for */*/*/*/system/*
14:25:51:0348 Gs  updates-shell: failed to get updates: no plugin could handle get-updates
14:25:51:0348 Gs  failed to create an app for */*/*/*/system/*
14:25:51:0348 Gs  failed to get system app
14:25:51:0348 Gs  Only 0 apps for recent list, hiding
14:25:52:0750 Gs  hiding category graphics featured applications: found only 0 to show, need at least 9
14:25:52:0758 Gs  hiding category audio-video featured applications: found only 0 to show, need at least 9
14:25:53:0375 GLib g_variant_new_variant: assertion 'value != NULL' failed
14:25:53:0375 GLib g_variant_new_variant: assertion 'value != NULL' failed
14:25:53:0376 Gs  not GsPlugin error g-io-error-quark:35: Invalid string value converting to GVariant
14:25:53:0376 Gs  not handling error failed for action refine: Invalid string value converting to GVariant
14:25:53:0890 GsPluginSnap Failed to load snap icon: local snap has no icon
14:25:54:0928 GsPluginSnap Failed to load snap icon: local snap has no icon
14:25:55:0439 GsPluginSnap Failed to load snap icon: local snap has no icon

```

---

### Post by Dennis N on 2020-08-05
_Firefox: Exiting due to channel error:_
Bug - [https://bugzilla.mozilla.org/show_bug.cgi?id=1538435](https://bugzilla.mozilla.org/show_bug.cgi?id=1538435)
Some reports here are for Firefox snap version.

_Okular: Segmentation fault._
It crashed for some reason. We're clueless.

When starting from terminal, various messages (some labeled as errors) are not uncommon. If I run Firefox snap from terminal:

```
dmn@Sydney-VM:~$ snap run firefox
Gtk-Message: 08:38:15.286: Failed to load module "canberra-gtk-module"
Gtk-Message: 08:38:15.317: Failed to load module "canberra-gtk-module"
Sandbox: /tmp/.X11-unix/X0 is inaccessible (No such file or directory); can't isolate network namespace in content processes
Gtk-Message: 08:38:32.961: Failed to load module "canberra-gtk-module"
Gtk-Message: 08:38:32.962: Failed to load module "canberra-gtk-module"
Gtk-Message: 08:38:33.806: Failed to load module "canberra-gtk-module"
Gtk-Message: 08:38:33.808: Failed to load module "canberra-gtk-module"
Gtk-Message: 08:38:34.056: Failed to load module "canberra-gtk-module"
Gtk-Message: 08:38:34.057: Failed to load module "canberra-gtk-module"
extension-storage: migration complete
Gtk-Message: 08:38:36.033: Failed to load module "canberra-gtk-module"
Gtk-Message: 08:38:36.034: Failed to load module "canberra-gtk-module"
Gtk-Message: 08:38:36.505: Failed to load module "canberra-gtk-module"
Gtk-Message: 08:38:36.510: Failed to load module "canberra-gtk-module"


```After this Firefox is running normally.

Okular throws lots of messages too. I get 123 lines of FontConfig errors and warnings. Plus this Qt error that you have as well:
```
Qt: Session management error: None of the authentication protocols specified are supported
```
but this Okular snap still works normally.

System details:
```
dmn@Sydney-VM:~$ snap --version
snap    2.45.2
snapd   2.45.2
series  16
ubuntu  19.10
kernel  5.3.0-64-generic

```
I had to use 19.10 (it's a virtual machine) only because that's were I installed the Okular snap to test it.

---

### Post by nought2 on 2020-08-05
> **Dennis N said:**
> _Firefox: Exiting due to channel error:_
Bug - [https://bugzilla.mozilla.org/show_bug.cgi?id=1538435](https://bugzilla.mozilla.org/show_bug.cgi?id=1538435)
Some reports here are for Firefox snap version.
Majority of bug reports there are for development versions of FF. Strife with them is expected.

The Snap problems on my system are probably of a different nature and are likely to stem from the usage history of Snap. 

Exploring the problem in this thread has refreshed my memory of what I did to cause the malaise. At the time I first installed Snap packages I had no idea what they were and what their installation process entailed. Specifically, I didn't realise the size of the download required for self-contained Snap packages and how long it would take to pull them down from the cloud.

Early on I had installed a few Snaps successfully via the Ubuntu Software GUI. Some time later when installing Okular Snap nothing seemed to happen. In the background the package was downloading, but I didn't realise that, there was no indication in the GUI it was taking place. Impatient to see a result of my action I hit the install button numerous times. 

While at that time Okular Snap was installed it would not run. Okular installed via apt ran OK but was not latest version. Yada. We've already covered this ground. 

Occasionally when navigating around Ubuntu 18.04's GUI I would see evidence of the multiple Snap install attempts. IIRC, when selecting the default PDF viewer from a list there was ~10 appearances of Okular on top of each other. The number of appearances likely corresponded to the number of install requests/attempts I had made.

Snap packages installed prior to Okular Snap worked normally. When such apps were searched in the Ubuntu Software GUI their standard icon would appear. 

Today I reinstalled p7zip-desktop. It's a pretty lightweight app, only a GUI for a file compression utility. The installed package launches and appears to work. But its proper icon is missing from Ubuntu Software, instead the generic mauve diamond with gear motifs appears. Another manifestation of the perturbation of Snap on this system.

To remedy the problem, if it is possible, needs more than removing, purging, reinstalling various elements of Snap.

System info:```
~$ snap --version
snap    2.45.2
snapd   2.45.2
series  16
ubuntu  18.04
kernel  4.15.0-112-generic
```

---

### Post by Dennis N on 2020-08-06
Your experience with the initial install of snap reminds me of mine. Using (Gnome) Software, there was no feedback as to progress. Fortunately, I let it be for awhile instead of aborting. Now, I would rather install from the terminal, since it does show what is happening.

You can supply the icon for a snap. The atari800-jz snap didn't provide an icon. I copied the snap's .desktop file to ~/.local/share/applications and included an Icon= line. That worked. This also gives us a way to change the displayed name.

---

### Post by nought2 on 2020-08-06
> **Dennis N said:**
> Using (Gnome) Software, there was no feedback as to progress. ... Now, I would rather install from the terminal, since it does show what is happening.With 20/20 hindsight that is what I would certainly do. When feeling my way around in a new environment it was a case of traps for young players.

Searched for problems with Snap tonight. Along the way learnt that Canonical is pushing it hard, intends to rely on it to distribute frequently updated packages. Didn't realise Snaps are silently updated in the background without user's awareness, request or permission. Devs like this because all users have the most up to date package. Also security benefits. Some object because it seems a little underhanded. For Ubuntu the upshot is that Snap is to be an essential software distribution format and channel.

The searches pulled up a slightly different set of commands to remove snapd. I wound back the system with the image made two days ago and gave them a try.
```
sudo snap remove --purge <package1> <package2> <packageN>
sudo rm -rf /var/cache/snapd/
sudo apt autoremove --purge snapd gnome-software-plugin-snap
rm -fr ~/snap
```No joy. Reinstalled snapd. Tested by installing Snaps that had given me problems before; they still didn't work.

> You can supply the icon for a snap. The atari800-jz snap didn't provide an icon. I copied the snap's .desktop file to ~/.local/share/applications and included an Icon= line. That worked. This also gives us a way to change the displayed name.But for p7zip-desktop I would have to retrieve it somehow from a system image file.
Otherwise those are handy tricks to have up my sleeve.

---

### Post by Dennis N on 2020-08-07
> Didn't realise Snaps are silently updated in the background without user's awareness, request or permission.
Flatpak is doing this too. But not before Ubuntu 20.04. You get a notification about it (see attached). I'm not aware of any settings for the updating policy in either Snaps or Flatpak. But, I don't really mind the automatic updating, and Ubuntu itself does automatic security updates in the background.

---

### Post by nought2 on 2020-08-09
Through this thread I've come to realise Snap is an essential element of the contemporary Ubuntu experience, an experience partially denied to me. Having tried every means available to me to repair the system over the last 2w left me with few alternatives. I exercised my prerogative as sole authority of my computer to summon the football and whip out my biscuit. It was time for the nuclear option.

Scary, but not bone chilling like this:
[ATTACH=CONFIG]286656[/ATTACH]

I made a fresh and clean install of Ubuntu 18.04 LTS.

_Etcher_
Used it to flash ISO image to USB stick. There must be a lot happening behind its minimalist GUI. It made the job easy, no decisions to be made. Select ISO file, select target drive, done. Installed it to old system. Clicking on its *.AppImage file did not create a *.desktop launcher as far as I could tell. Ditto on new system. Made DIY launcher instead.

_Ubuntu OS install experience_
Was gobsmacked at how dazzlingly fast it was. It helps that boot  drive is NVMe. USB stick was ~10yo USB 3.0. Installation itself completed in about a minute, possibly less. Preparatory work took much longer: image entire boot drive; read Ubuntu installation notes of my commercial partition & boot manager; carefully select "Something Else" parameters in Ubuntu installer. Hit the go button and whammo. First time around Ubuntu had been installed from DVD media. Won't bother doing that again.

_Ubuntu 18.04.5 LTS installed_
Old system was 18.04.4 LTS. It was updated regularly. No idea why it was behind current point release.
Also downloaded ISO for 20.04.1 LTS. Have enough room on NVMe drive to try it too. Might do after I have finished slog of installing software and changing prefs for new 18.04.5.

_Snap test_
Installed Okular Snap via terminal. The pause before its first launch was an apprehensive few moments. Success. What a relief.

_p7zip-desktop Snap icon_
Copied its *.desktop file from /var/lib/snapd/desktop/applications to ~/.local/share/applications. Then had had to remind myself how to change file permissions and owner before I could do the rest. Had read all the relevant info months ago in The Linux Command Line by William Schotts. When it came to the crunch none of the salient info would come to me. Better return to TLCL for more reading and learning. 
Got there though. Happy that p7zip-desktop Snap now has working DIY icon and custom launcher name. 
Modified Okular Snap launcher too. Changed Name= line to distinguish it from Okular Flatpak. Changed file name of surplus generic Okular Snap launcher to hide icon.
[U]
Problematic pdf file bug report[/U]
Today received update from bugs.kde.org. 
It was a bug in Poppler, a pdf rendering library. One of its devs fielded the bug report.
[https://bugs.kde.org/show_bug.cgi?id=424779](https://bugs.kde.org/show_bug.cgi?id=424779)
Said it will be fixed in Poppler 20.09. 
Don't know when version with that bug fixed will make it to Linux repos. After updating new system Poppler version was 0.62.0. I was able to update it via PPA to 0.74.0. Tagged release points are up to 0.90.1 and 20.08. Those could take awhile to filter down.
[https://gitlab.freedesktop.org/poppler/poppler/-/tags](https://gitlab.freedesktop.org/poppler/poppler/-/tags)

---

