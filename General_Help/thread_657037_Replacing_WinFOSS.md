---
title: "Replacing WinFOSS"
date: 2008-01-03
forum: General Help
---

### Post by Henrik on 2008-01-03
I wrote a [proposal on ubuntu-devel]("https://lists.ubuntu.com/archives/ubuntu-devel/2007-December/024846.html") recently to remove the Windows software collection from the Live CDs. The Live CD browser was also intended to launch Wubi from the CD so we need to find an alternate way of doing that if we remove the WinFOSS browser (it also displays some documentation, like the migration guide which we should still provide). 

My preferred option would be to launch Wubi directly from the CD and add an option to that interface to launch the documentation/into-material in a browser.


Is this feasible?

---

### Post by tuxcantfly on 2008-01-04
> **Henrik said:**
> I wrote a [proposal on ubuntu-devel]("https://lists.ubuntu.com/archives/ubuntu-devel/2007-December/024846.html") recently to remove the Windows software collection from the Live CDs. The Live CD browser was also intended to launch Wubi from the CD so we need to find an alternate way of doing that if we remove the WinFOSS browser (it also displays some documentation, like the migration guide which we should still provide). 

My preferred option would be to launch Wubi directly from the CD and add an option to that interface to launch the documentation/into-material in a browser.


Is this feasible?

Certainly sounds feasible, though on another note, wouldn't it also make sense to remove K-Meleon and just rely on an embedded IE frame within the small NSIS app for browsing the help documentation, while simply launching the .exe files from the small NSIS app directly (since the mini-help documentation is already html, and renders fine on IE, thereby using the embedded IE frame approaches eliminates the need to rewrite the current HTML interface, while still allowing for launching the .exe files directly from the small NSIS app, outside the IE frame)? That would free up a few megabytes of space as well (not to mention that it would speed up the launch process, since a small NSIS app with an embedded IE frame launches faster than the modified K-Meleon loads from the CD).

Also, perhaps to act as a replacement for the WinFOSS software, there could also be links in the menu launched by the autorun with links to the various FOSS software that was removed.

So, as a basic mockup, this is what I'd envision:

(user inserts Ubuntu CD, autorun.inf launches a small standalone .exe app written using NSIS, which displays the following) 

===
Welcome to Ubuntu! Select one of the tasks below:

1. Help, About Ubuntu (Browses existing html help guide using an embedded IE frame within the small NSIS app)

2. Install Ubuntu using Wubi (this option launches wubi.exe)

3. Patch bootloader to boot from CD and reboot (this option installs the GRLDR patches to Ubuntu, provided by wubi-cdboot.exe)

4. Browse Ubuntu documentation (Browses html documentation on CD via an embedded IE frame)

5. Browse available free/open-source software (Uses embedded IE frame to display some remote portal page with links to downloads for Firefox, Thunderbird, Openoffice.org, Abiword, and the like)

---

### Post by Henrik on 2008-01-04
Yes, the intention was also to remove the K-meleon browser. Sorry if that wasn't clear. Using the IE frame is interesting, but if we are simply linking to HTML-based info/docs we could just as well link to the users default browser. I agree that we should add links to some of the Windows-based applications (project pages) that will now be removed. 

I would suggest altering your mockup to:

(user inserts Ubuntu CD, autorun.inf launches wubi.exe, which displays the following)

===

The standard Wubi screen as shown [here]("http://wubi-installer.org/images/wubi.png") 

Plus:

A link or button: "Ubuntu introduction and documentation" which opens the user's web browser with [this page]("http://people.ubuntu.com/%7Ehenrik/images/about-ubuntu.png"). 

That page will in turn link to the migration guide and to an overview page open source for Windows.


===

That to me seems like the simplest solution, using a single .exe and removing all the K-meleon and FOSS installers, freeing up the most space. 

Displaying [www.mozilla.com/firefox/](www.mozilla.com/firefox/) etc. in the IE frame seems to me to have a few problems a) It will look more cramped than the user's normal browser (unless we make that window very big) b) the user can not easily bookmark those sites and return to them later c) the person may be using an alternative browser for a reason so we don't want to push IE technology.

---

### Post by tuxcantfly on 2008-01-04
> **Henrik said:**
> Yes, the intention was also to remove the K-meleon browser. Sorry if that wasn't clear. Using the IE frame is interesting, but if we are simply linking to HTML-based info/docs we could just as well link to the users default browser. I agree that we should add links to some of the Windows-based applications (project pages) that will now be removed. 

I would suggest altering your mockup to:

(user inserts Ubuntu CD, autorun.inf launches wubi.exe, which displays the following)

===

The standard Wubi screen as shown [here]("http://wubi-installer.org/images/wubi.png") 

Plus:

A link or button: "Ubuntu introduction and documentation" which opens the user's web browser with [this page]("http://people.ubuntu.com/%7Ehenrik/images/about-ubuntu.png"). 

That page will in turn link to the migration guide and to an overview page open source for Windows.


===

That to me seems like the simplest solution, using a single .exe and removing all the K-meleon and FOSS installers, freeing up the most space. 

Displaying [www.mozilla.com/firefox/](www.mozilla.com/firefox/) etc. in the IE frame seems to me to have a few problems a) It will look more cramped than the user's normal browser (unless we make that window very big) b) the user can not easily bookmark those sites and return to them later c) the person may be using an alternative browser for a reason so we don't want to push IE technology.

Yes, that certainly sounds better, but I don't quite think wubi.exe should be auto-launched by autorun.inf by default; rather, the NSIS standalone .exe app displays a small menu that informs the user that they can either reboot to proceed with the standard installation, or use Wubi (if the user clicks there then wubi.exe is launched), and below those come the various links to the help, documentation, and FOSS software portals (which will be displayed externally in the default web browser).

I think it would be unwise to launch wubi.exe by default, because many users prefer the liveCD installation approach, which is just a reboot away. Just launching Wubi automatically will cause many new users to not even realize that they can reboot into liveCD mode and do a standard installation from there just as easily. Having an intermediate menu that shows them that they have the option of using either Wubi or the standard liveCD install doesn't present an extra hassle to those who would be using Wubi anyhow (just an extra click on the Wubi entry), while it would be helpful to those who want to do a standard installation.

Besides, given that the default behavior for Wubi installations is a loopmounted install that chainloads off the Windows bootloader, which is clearly more problematic in the long run compared to the standard installation approach (performance overhead, more prone to filesystem corruption, etc), it would probably be better to have more people installing using the standard approach, and restricting the usage of Wubi to just those who cannot use the standard approach. Therefore, having the autorun display the options available, from which Wubi can be launched, rather than automatically launching Wubi, will help to minimize the number of users on a loopmounted install to only those who really need and want it.

---

### Post by ago on 2008-01-04
Henrik,

If you wish I can easily add an NSIS page to wubi or modify the existing one or create a separate nsis app. 

It is perfectly possible to use wubi-cdboot as default wubi installation option whenever a ubuntu CD is detected, this  will change the bootloader (to prevent bios issues) and guarantee a full installation to a dedicated partition (the bootloader changes can be removed on the next windows boot). It would also be easy to add an option to simply reboot. One thing to add anyway is the checksum of the files within the CD (note to self).   

An (x)html page would also be a good option.

Shall you choose the wubi route, I would appreciate if you could send a few mockups on how to lay-out the wubi pages.

---

### Post by Henrik on 2008-01-10
I like the idea of a separate NSIS app so we can keep wubi as it is. [Here is a mockup]("http://people.ubuntu.com/%7Ehenrik/images/wubi-mockup.png") of a possible layout. ([SVG version]("http://people.ubuntu.com/%7Ehenrik/images/wubi-mockup.svg"))

---

### Post by ago on 2008-01-10
.

---

### Post by ago on 2008-01-10
Henrik, sounds good.

I would add a couple of lines under each option

> 
**Ubuntu Demo and Full Installation**
You can try Ubuntu without installing anything by simply rebooting your machine leaving the CD in the tray. If you like what you see, you will have the option to perform a full installation from within the demo itself. If the demo did not start after you rebooted your machine, click here (wubi-cdboot).

**Install Ubuntu inside Windows**
This installation can easily be uninstalled and does not require dedicated harddisk resources, but performance and robustness are not on par with a full installation and suspend/hibernation are disabled. 

**Learn more about Ubuntu-Linux**
(launch default browser opening pages on CD)

**Free and open source applications for Windows**
(launch default browser opening pages on CD with external links)



PS: it is not possible to change partitions when the ISO is on the partition itself. This does not affect loopinstallations, but it may result in partman/ubiquity failing when installing to a dedicated partition
PS2: I can put that together in a few hours if you wish.

---

### Post by ago on 2008-01-10
Henrik have started a launchpad project to submit code ([https://launchpad.net/umenu](https://launchpad.net/umenu))
and a wiki page [https://wiki.ubuntu.com/umenu](https://wiki.ubuntu.com/umenu) for proposals

This should simplify the process. Feel free to start a blueprint if you feel it's appropriate.

---

### Post by ago on 2008-01-11
What about using HTA ([http://msdn2.microsoft.com/en-us/library/ms536471.aspx](http://msdn2.microsoft.com/en-us/library/ms536471.aspx))???
Should be supported on all windows versions (comes with IE5+) and would allow us to use all usual dhtml weaponry + execute commands. This is only intended to be used as a CD menu launcher of course, document/internet browsing should be displayed via the default browser (see example below).

Here is an example app. Simply save as "umenu.hta" and doubleclick on it from windows. If you like the concept it is well possible to expand on it and make a brandable/localizable app... and even make it look good...

```

<HTML>
<HEAD>
    <TITLE>Ubuntu CD Menu</TITLE>
    <!-- for HTA docs see:
    http://msdn2.microsoft.com/en-us/library/ms536471.aspx
    -->
    <HTA:APPLICATION
        ID="umenu"
        APPLICATIONNAME="Ubuntu CD Menu"
        BORDER="normal"
        BORDERSTYLE="normal"
        INNERBORDER="no"
        SCROLL="no"
        CAPTION="yes"
        ICON="icon.ico"
        SHOWINTASKBAR="yes"
        SINGLEINSTANCE="yes"
        SYSMENU="no"
        WINDOWSTATE="normal"
        CONTEXTMENU="no"
        NAVIGABLE="no"
        SELECTION="no"
    />
    <!--
    <LINK REL="stylesheet" HREF="umenu.css" TYPE="text/css" />
    -->
    <STYLE TYPE="text/css">
        body {
            font-family: Arial;
            text-align: left;
            margin: 0;
        }
        .action {
            text-decoration: none;
            color: #618322;
            font-weight: 500;
            font-size: larger;
        }
        p {
            text-align: justify;
        }
    </STYLE>
</HEAD>
<BODY>
    <DIV ID="logo">
    </DIV>
    <DIV ID="menu">
        <DIV ID="choicelist">
            <DIV CLASS="choice">
            <A CLASS="action" HREF="#" ID="cmdReboot">Ubuntu Demo and Full Installation</A>
            <P>You can try Ubuntu without installing anything by simply rebooting your machine leaving the CD in the tray. If you like what you see, you will have the option to perform a full installation from within the demo itself. If the demo did not start after you rebooted your machine, <a ID="cmdWubiCdBoot" HREF="#">click here</a></P>
            </DIV>
            <DIV CLASS="choice">
            <A CLASS="action" HREF="#" ID="cmdWubi">Install Ubuntu Inside Windows</A>
            <p>You can now install and uninstall Ubuntu without modifying your harddisk setup, but robustness and performance are not on par with a full installation and suspend/hibernation are disabled.</P>
            </DIV>
            <DIV CLASS="choice">
            <A CLASS="action" HREF="http://www.ubuntu.com/products/whatisubuntu/desktopedition">Learn more about Ubuntu-Linux</A>
            <P>Ubuntu is a free, Linux-based operating system, it comes with a full set of applications including an office suite, drawing software, a web browser and much more.</P>
            </DIV>
            <DIV CLASS="choice">
            <A CLASS="action" HREF="http://www.opensourcewindows.org/">Free and Open Source Software for Windows</A>
            <P>Some of the free and open source applications available in Ubuntu can also be installed within Windows</P>
            </DIV>
            <DIV CLASS="choice">
            <A CLASS="action" HREF="#" ID="cmdClose">Close</A>
            <P>Quit ubuntu menu, no changes will be made.</P>
            </DIV>
        </DIV>
        <DIV ID="choiceinfo">
        </DIV>
    </DIV>

    <SCRIPT FOR="cmdReboot" EVENT="onclick" LANGUAGE="VBScript">
        msgbox "Rebooting now... (kidding)"
    </SCRIPT>

    <SCRIPT FOR="cmdWubi" EVENT="onclick" LANGUAGE="VBScript">
        msgbox "Launching Wubi"
    </SCRIPT>

    <SCRIPT FOR="cmdWubiCdBoot" EVENT="onclick" LANGUAGE="VBScript">
        msgbox "Launching Wubi-CdBoot"
    </SCRIPT>

    <SCRIPT FOR="cmdClose" EVENT="onclick" LANGUAGE="VBScript">
        window.close
    </SCRIPT>

    <SCRIPT LANGUAGE="VBScript">
        Call InitWindow

        Sub InitWindow
            Const HEIGHT = 600
            Const WIDTH = 600
            window.resizeTo HEIGHT,WIDTH
            window.moveTo (screen.width - HEIGHT) / 2, (screen.height - WIDTH) / 2
        End Sub
    </SCRIPT>
</BODY>
</HTML>


```

---

