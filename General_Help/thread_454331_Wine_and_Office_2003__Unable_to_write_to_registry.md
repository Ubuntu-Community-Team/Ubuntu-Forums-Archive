---
title: "Wine and Office 2003:  Unable to write to registry"
date: 2007-05-25
forum: General Help
---

### Post by thepossiblehuman on 2007-05-25
Hi all,

I've been playing around with Ubuntu a lot a lately, and have been testing it to see how well I could integrate it into our business.  Two absolute musts are to be able to run Internet Explorer for Explorer-written corporate web applications (Mozilla works most of the time, but "most of the time" isn't viable in this case) and of course Office 2003 mainly for Outlook/Exchange support and advanced Excel work.  

I installed wine through synaptic package manager, but when I go to install Office 2003, it fails when it gets to the writing to the registry part.  I will then be able to see the excutables on my machine and even run them for a split second, but immediately upon openning I get a "Excel not installed for this user.  Please run set-up again" message, then it closes.  This makes perfect sense since it is looking for and not finding the registry entries.

I'm a complete noob when it comes to working with wine.  Is this a common problem that there is a common fix for.  Does nybody know of any good resources on the web about wine that I can get some pointers for?  Thanks.

---

### Post by wieman01 on 2007-05-25
Well, I got to work MS Office using Wine... that's the bad news. The good news is that there is remedy if you want to take a shortcut and spend 40 US$ or so on CrossOver Office which builds on Wine. I have been using it for a few months and man, I tell you, it makes (Linux) life a lot simpler:

[http://www.codeweavers.com/]("http://www.codeweavers.com/")

The program is worth every single dollar and has saved me a considerable amount of time. MS Office XP works just fine, had no trouble installing and running it.

---

### Post by Medieval_Creations on 2007-05-25
Here is the home page for ie4linux.  It installs IE to run in linux.
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

I don't think office 2003 works in Wine yet.  Here's a link to Wine HQ.
[http://appdb.winehq.org/appview.php?iAppId=31](http://appdb.winehq.org/appview.php?iAppId=31)

---

### Post by cookies on 2007-05-25
I have gotten Office 2003 to work in Wine. Just ignore the error, it has dumped all you need in ~/.wine.

Now, go to ~/.wine/drive_c/Program Files/Microsoft Office/OFFICE11 and try to open Word. If it says you have not installed it, run the installer from the CD again, and select Repair and Repair All

Now, you have to set some DLL's, so open Winecfg, and select Applications > Add Application and add PowerPoint, Word, and Excel.

Now, select Word, go to  Libraries

Add the riched20.dll and set it to Native. Do this for all of the Office Apps.

Next, for the Default Settings, download and install wininet.dll:
[http://www.dll-files.com/dllindex/dll-files.shtml?wininet](http://www.dll-files.com/dllindex/dll-files.shtml?wininet)

Put it in
~/.wine/drive_c/windows/system32

There is already one there, but overwrite it. 

Now for Default Settings, select wininet.dll in Libraries and set it to Native

Open Word again, and fill in the name and stuff it asks, now, for Product Registration, you have to call and follow the procedure, because Activation over the Internet doesn't work.

Hope it works for you.

---

