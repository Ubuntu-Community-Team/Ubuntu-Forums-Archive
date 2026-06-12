---
title: "Firefox and Wine"
date: 2007-07-06
forum: General Help
---

### Post by AlanR8 on 2007-07-06
Evening all

Here's the thing. Running Kubuntu and have Crossover Linux 6.1.0 installed. I've noticed that FF will lockup on some pages, particularly when a video is on screen. BUT, this last day I've noticed on the lock up the Process table shows wineserver and winewrapper.exe is running despite the fact they have Not been consciously invoked.

According to about:plugins in Mozilla:

> CrossOver - npwmsdrm.dll

    File name: npcxoffice-086a7ac3-bdbb-46b0-8a9f-ea303ae87a29.linux.npwmsdrm.dll.so
    Unable to load the Windows plugin library (last attempt Fri Jul 6 21:33:29 2007 ).

MIME Type 	Description 	Suffixes 	Enabled
unknown/mime-type 	Do not open 	none 	Yes
CrossOver - NPOFFICE.DLL

    File name: npcxoffice-76cffda7-2f47-4aef-a92b-f4ed4d6706ec.linux.NPOFFICE.DLL.so
    Unable to load the Windows plugin library (last attempt Fri Jul 6 21:33:29 2007 ).

MIME Type 	Description 	Suffixes 	Enabled
unknown/mime-type 	Do not open 	none 	Yes
CrossOver - npqtplugin4.dll

    File name: npcxoffice-76cffda7-2f47-4aef-a92b-f4ed4d6706ec.linux.npqtplugin4.dll.so
    Unable to load the Windows plugin library (last attempt Fri Jul 6 21:33:29 2007 ).

MIME Type 	Description 	Suffixes 	Enabled
unknown/mime-type 	Do not open 	none 	Yes
CrossOver - npqtplugin5.dll

    File name: npcxoffice-76cffda7-2f47-4aef-a92b-f4ed4d6706ec.linux.npqtplugin5.dll.so
    Unable to load the Windows plugin library (last attempt Fri Jul 6 21:33:29 2007 ).

MIME Type 	Description 	Suffixes 	Enabled
unknown/mime-type 	Do not open 	none 	Yes
CrossOver - npqtplugin6.dll

    File name: npcxoffice-76cffda7-2f47-4aef-a92b-f4ed4d6706ec.linux.npqtplugin6.dll.so
    Unable to load the Windows plugin library (last attempt Fri Jul 6 21:33:29 2007 ).

MIME Type 	Description 	Suffixes 	Enabled
unknown/mime-type 	Do not open 	none 	Yes
CrossOver - npqtplugin7.dll

    File name: npcxoffice-76cffda7-2f47-4aef-a92b-f4ed4d6706ec.linux.npqtplugin7.dll.so
    Unable to load the Windows plugin library (last attempt Fri Jul 6 21:33:29 2007 ).

MIME Type 	Description 	Suffixes 	Enabled
unknown/mime-type 	Do not open 	none 	Yes
CrossOver - npqtplugin2.dll

    File name: npcxoffice-76cffda7-2f47-4aef-a92b-f4ed4d6706ec.linux.npqtplugin2.dll.so
    Unable to load the Windows plugin library (last attempt Fri Jul 6 21:33:29 2007 ).

MIME Type 	Description 	Suffixes 	Enabled
unknown/mime-type 	Do not open 	none 	Yes
CrossOver - npqtplugin3.dll

    File name: npcxoffice-76cffda7-2f47-4aef-a92b-f4ed4d6706ec.linux.npqtplugin3.dll.so
    Unable to load the Windows plugin library (last attempt Fri Jul 6 21:33:29 2007 ).

MIME Type 	Description 	Suffixes 	Enabled
unknown/mime-type 	Do not open 	none 	Yes

Any ideas what's going on? I'm NOT asking Wine/Crosover Linux to start up. BTW, I do not have Wine installed, just Crossover Linux.

Any help, as always, MUCH appreciated.

---

### Post by cookies on 2007-07-06
CrossOver must be trying to play the video because you installed QuickTime/MS Media Player, et cetera.

---

### Post by AlanR8 on 2007-07-06
You might think that 'cos I didn't say what I had installed under Wine/Crossover Linux!

All I have under the above is Office 2003. NO other apps at all.

---

### Post by p_quarles on 2007-07-06
I'm just taking a wild guess, but there are some apps which will stealthily use Wine to install themselves. Picasa, for instance. Do you maybe have anything like that?

---

