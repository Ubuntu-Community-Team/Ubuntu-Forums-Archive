---
title: "No icons no double click on nothing :("
date: 2007-01-11
forum: General Help
---

### Post by rem on 2007-01-11
Hello,

Today, I wanted to try the Bluefish editor unstable version and I downloaded it as a .rpm from their site. I aliened it and generated a .deb package. When I double clicked it, it failed to install because of some kind of conflict with the other dev version I previously installed from CVS. I saw there aren't any broken packages and I thought that everything is ok, I abandoned it for another time.

After a while I noticed that the icons for every document, audio, video, archives, etc ... files are gone and can't double click them anymore. Ex: before, when I was double clicking an .avi file, Totem was opened. Now, nothing but this error message :( 

```

Couldn't display "~/file.ext".

```

Otherwise, everything is OK with my Ubuntu Dapper, I'm using it with great success on everything I need! Very happy indeed... 

Thank you a million. Hope you guys know a way to sort this weird thing out...

Best,

Rem.

---

### Post by taurus on 2007-01-11
Have you tried to reboot?  Also, can you open those files (videos with gmplayer, xine, vlc, or even totem) from a terminal?

---

### Post by rem on 2007-01-11
> **taurus said:**
> Have you tried to reboot?  Also, can you open those files (videos with gmplayer, xine, vlc, or even totem) from a terminal?

yes, i did rebooted and nothing happened... i noticed: when i want to unpack some archives, it's not even recognized as an archive. i have to open it by choosing "open with" from the context menu... if i'm opening mplayer or totem, open office or gedit, I can select a file or a media and then open it but can't open it if i'm double clicking on it... somehow all my files turned into some strange unknown files for my Linux with no icons and no double click to open :( 

also, can open any file from terminal ex: gedit myfile.htm or mplayer mymovie.avi


thanks!

---

### Post by taurus on 2007-01-11
Right click on the files and look into Properties.  Make sure you include the right app to open for the file.

---

### Post by rem on 2007-01-11
I know that ... I wouldn't insist with this matter no more. Thank you. I'll have to assign apps and icons to all the files all over again even though some of them are not working (OOffice odts) and this whole thing kinda sucks! Don't know what to do, I'll dig some more...

---

### Post by rem on 2007-03-02
> **rem said:**
> I know that ... I wouldn't insist with this matter no more. Thank you. I'll have to assign apps and icons to all the files all over again even though some of them are not working (OOffice odts) and this whole thing kinda sucks! Don't know what to do, I'll dig some more...


I finally got it ... It was a Gnome MIME problem.
~/.local/share/mime/aliases file had a bunch of bogus mime properties. i emptied that out and now it's working ...

---

