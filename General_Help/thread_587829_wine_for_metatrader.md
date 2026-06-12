---
title: "wine for metatrader?"
date: 2007-10-23
forum: General Help
---

### Post by indosupremacy on 2007-10-23
does anybody know how to use metatrader in ubuntu?
it seem that wine cant do that...any suggest?
thank u

---

### Post by pininy on 2007-11-16
> **indosupremacy said:**
> does anybody know how to use metatrader in ubuntu?
it seem that wine cant do that...any suggest?
thank u


I found a thread that might be useful to you, follow it and you will be able to have it running

here's the [URL]("http://forums.fxservice.com/index.php?showtopic=499&pid=5488&st=0&#entry5488")


also I have attached my metatrader on my gusty!

---

### Post by rjs2006 on 2008-01-13
follow instructions for how to add the mfc42.dll to you wine configuration. After that copy all our windows fonts to your wine install.

Doing the above solved my problems and Metatrader is running great on Ubuntu for me.

---

### Post by rjs2006 on 2008-01-13
screen shot attached.

---

### Post by AgentZ86 on 2008-03-14
Hi all

From Ubuntu 7.10

I sort of followed an instruction on the web, and from the url, but basically I just installed wine from the applications/add/remove menu item.

Then, copied the windows fonts from my windows drive, to my /.wine/drive_c/windows/font  I did this manually by using the clickety method, simply browse to your windows partition, and copy all the files in the WINDOWS/fonts folder, then  from the applications/wine/  and select BROWSE/C:DRIVE, Then browse to the windows/fonts folder, and past those fonts in there. by right clicking and select paste.

Then I went to my WINDOWS/Temp folder and copied all the mfc/MFC .dll files and then pasted them to applications/wine/ selected BROWSE/C:DRIVE and then navigated to the windows/temp folder and just right clicked and pasted those mfc.dll files here.

Then downloaded the mt4 from: [http://forextrade.ru/downloads/mt4setup.exe](http://forextrade.ru/downloads/mt4setup.exe)

And it installed and sounds worked perfectly no other configuration needed.

And I"m using the wine in the ubuntu repository which is 0.9.46 version. So I'll update it from those repositories as they become available but no need for the moment, as it's working great just like this.

I hope this helps.

---

### Post by Louis Cypher on 2008-07-14
I have Metatrader installed and working under 8.04.  The only issue I have is that the BackTestng does not work perfectly.  If I select Visaul Mode it works.  But when I just select Use Date I don't get any chart data.  I have a copy of MT4 running under VirtualBox.  That's where I copied the DLL's from.  Thanks.

---

