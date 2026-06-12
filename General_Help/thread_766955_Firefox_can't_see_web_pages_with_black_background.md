---
title: "Firefox can't see web pages with black background"
date: 2008-04-25
forum: General Help
---

### Post by clarezoe on 2008-04-25
Hi, I'm using Ubuntu 8.04 LTS with the firefox 3 Beta 5. 
I have a very weird problem with browsing the webpages that have black or dark color background.

For example, the page [http://mycroft.mozdev.org/deepdocs/quickstart.html ]("http://mycroft.mozdev.org/deepdocs/quickstart.html")
And the picture in the attachment is what I saw in my browser.

Anyone have the problem? Google seems not have any good solution of my problem.

Thanks!

---

### Post by bingoUV on 2008-04-25
I hate to break it to you but the page does not have a dark background.      You can try the follwing :  1. Run firefox in safe mode ```
 firefox -safe-mode 
``` This will disable extensions and themes so you will know if it is a problem with some of your extensions or not.  2. Download firefox from mozilla's server directly and run it. If it gives the same behaviour, either file a bug or post the debugging information here so that someone on this forum can file a bug.

---

### Post by clarezoe on 2008-04-25
thanks bingoUV, now I used the save mode and disabled all the extensions, it acts still the same. Then but firefox 2 works fine and then I removed firefox 3 and downloaded firefox 3 beta5 from mozilla's server directly as you said, and it works fine too. Do you think I can confirm that it's a bug of firefox 3 beta 5 in ubuntu distribution? Or do you need more information from me to track the problem?

That page IS black in the browser, and there're some other pages behave the same before.

---

### Post by clarezoe on 2008-04-25
Now I'm using the firefox downloaded directly from the Mozilla, it's fine.
But another thing I have to say is that, it also happens in my Liferea (version 1.4.14), it behaves the same in the feed [http://feeds.feedburner.com/googlechinablog/hESp](http://feeds.feedburner.com/googlechinablog/hESp)

I have no clue why this happens.

Thanks in advance.

---

### Post by bingoUV on 2008-04-26
It should be enough to file a bug on Ubuntu. Mozilla's build of firefox is fine so no need to file a bug on mozilla. The URL and screenshots of safe mode should be enough to get the developers working.  In my browser, both opera and firefox 3 beta 5, I do not see any black background. Locale problem? See the attached image.

---

### Post by clarezoe on 2008-04-26
I've posted a bug, hope it will be solved soon.
Thanks bingoUV, I don't know if the locale can make any effect of that.:confused:

---

### Post by clarezoe on 2008-06-13
just updated firefox to the latest version, still the same, so disappointed.

---

### Post by max63 on 2008-06-14
I've the same probleme...

---

### Post by clarezoe on 2008-06-14
> **max63 said:**
> I've the same probleme...

mas63, I've filed a bug here [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/222757]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/222757"), could you go and confirm it?

---

### Post by pencilcheck on 2008-07-10
I had that problem too bump!!
I also post a thread here in ubuntuforums but no one knows the solution to that.

But strangely, I don't have that synptom on that page. but other pages...

---

### Post by mscitex on 2009-10-23
3.0.14 is given me same problem
when i went to this site..([http://www.syfy.com/rewind/](http://www.syfy.com/rewind/)) all i saw was black
see screen shot...

---

### Post by mscitex on 2009-10-24
I also had no video or flash and could not see pages with black background
I fixed the problem by removing 2 packages and installing 3

by using "synaptic package manager"

**I removed this package**.
"swfdec-gnome"
Tools to play SWF files (Macromedia Flash) on GNOME
This package contains programs to integrate Flash functionality into the
GNOME desktop. It's main application is swfdec-player, a stand-alone viewer
for Flash files. It also contains swfdec-thumbnailer, a program that
provides screenshots for files to display in the Nautilu

**I removed this package**.
swfdec-Mozilla
Mozilla plugin for SWF files (Macromedia Flash)

A GTK+ and swfdec based Mozilla plugin for SWF files,
commonly known as Macromedia Flash animations

**I installed this package**.
adobe-flashplugin

Adobe Flash Player plugin version 10
This package will download the Flash Player from Adobe. It is a
Netscape/Mozilla type plugin. Any browser based on Netscape or Mozilla can use
the Flash plugin. This package officially supports the following browsers:

**I installed this package**.
flashplug-ininstaller

then i just went to Adobe and downloaded  (Adobe Flash Player)
Adobe Flash Player version 10.0.32.18 Linux

heres the link

[http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

then i selected (.deb for ubuntu)

the i restarted Firefox the everything was working as far as i can tell

   -=Mike Scitex=-
 [email]flapipe@yahoo.com[/email]

---

