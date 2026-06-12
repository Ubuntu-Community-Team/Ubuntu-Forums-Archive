---
title: "How do I install Microsoft Money using Wine?"
date: 2007-01-06
forum: General Help
---

### Post by glendavee on 2007-01-06
I have a dual boot system with several Microsoft programs installed in the XP drive. I have Edgy installed on the second hard drive. I have successfully installed Wine (I think)
Question - how do I use Money (or any other windows program) in Edgy. Do I need to reinstall the software in Edgy using Wine, or can I use Wine to open the program already in the Windows partition?
I have tried to install in Edgy, but the installation wizard tells me that installation was interrupted, try again later.
Using winefile in a terminal, I can see the windows version in the wine c:\ drive.
Anyone out there got any suggestions?

---

### Post by Stemp on 2007-01-06
[Wine HQ]("http://appdb.winehq.org/appview.php?iAppId=79")

The new versions of MS Money doesn't seems to work well :(

---

### Post by BiggoCharley on 2007-01-13
According to the WineHQ website app database MS Money doesn't work well under Edgy but is rated "gold" under dapper.  That being said however, I have not been able to successfully install money (2004) in dapper. When the install is complete (I think) there is a prompt to restart the system but restarting desn't seem to have any effect. and if you look at the wine /c_drive/program files the msmoney folder is there but it is empty.

---

### Post by pawsey on 2008-01-18
[COLOR="Red"]I installed msmoney 4 using this procedure:[/COLOR]

RE: MS Money 2004 won't run
by John Rydberg on Saturday November 3rd 2007, 22:30
1 - Install ies4linux using default parameters. [www.tatanka.com.br/ies4linux/page/Installation](www.tatanka.com.br/ies4linux/page/Installation)

Note: Verify that IE6 works correctly before continuing by logging into an SSL website of your choice. The IE about screen will say that there is "-bit" encryption but the "lock" icon in the lower right says 128-bit encryption when you hover over it.

2 - Create a script to launch winefile from within the ies4linux default installation path:

#!/usr/bin/env bash
export WINEPREFIX="$HOME/.ies4linux/ie6"
winefile

3 - Put Money 2004 CD in cdrom drive.

4 - Launch "Wine File" using script above.

5 - Double click on setup.exe found on the CD within "Wine File".

Everything should just work. The setup runs and does not try to re-install IE6. When it finishes it puts an icon on the desktop that launches money with no complaints.

My Install Details: Ubuntu-7.10 ies4linux-2.0.5 wine-0.9.46 cabextract-1.2

[COLOR="Red"]I deviated from the above in that I obtained ies4 from:
 
[http://ubuntuforums.org/attachment.php?attachmentid=53346&d=1197785907](http://ubuntuforums.org/attachment.php?attachmentid=53346&d=1197785907)

I didn't create the batch file, simply typed the commands into terminal.

Finally make sure that the line:

export WINEPREFIX="$HOME/.ies4linux/ie6"

Matches your correct directory path.

Hope this helps.[/COLOR]

---

### Post by glendavee on 2008-01-24
Thanks for that. I actually installed Money using Crossover - it worked well and has been running now for several months.

---

### Post by yellerKat on 2008-05-12
Wow Thanks for that - got MsMoney 2001 running!

---

### Post by mb76 on 2008-06-29
I've installed Money 2005 no problems, but now when I open the program it says it needs to download an update, however it never gets past the preparing to download part of updating.
I'm new to ubuntu and so far I like what I've seen, but as I've got 4 years worth of Money data I don't really want to start from scratch :(

Anyone got any ideas?

---

### Post by iheartubuntu on 2008-07-09
I was excited when I came across your tutorial, but it didnt work for me. I installed ies4linux and it works great. When I run the script, nothing happens. Ive got cabextract installed as well.

After using the script, I get a prompt like ">" with winefile listed so I press enter and get nothing. Am I doing something wrong?

winefile works fine without the script, but I guess thats not what we want here. I wonder if my problem is I had tried to previously install MS money 04 unsuccessfully.



> **pawsey said:**
> [COLOR="Red"]I installed msmoney 4 using this procedure:[/COLOR]

RE: MS Money 2004 won't run
by John Rydberg on Saturday November 3rd 2007, 22:30
1 - Install ies4linux using default parameters. [www.tatanka.com.br/ies4linux/page/Installation](www.tatanka.com.br/ies4linux/page/Installation)

Note: Verify that IE6 works correctly before continuing by logging into an SSL website of your choice. The IE about screen will say that there is "-bit" encryption but the "lock" icon in the lower right says 128-bit encryption when you hover over it.

2 - Create a script to launch winefile from within the ies4linux default installation path:

#!/usr/bin/env bash
export WINEPREFIX="$HOME/.ies4linux/ie6"
winefile

3 - Put Money 2004 CD in cdrom drive.

4 - Launch "Wine File" using script above.

5 - Double click on setup.exe found on the CD within "Wine File".

Everything should just work. The setup runs and does not try to re-install IE6. When it finishes it puts an icon on the desktop that launches money with no complaints.

My Install Details: Ubuntu-7.10 ies4linux-2.0.5 wine-0.9.46 cabextract-1.2

[COLOR="Red"]I deviated from the above in that I obtained ies4 from:
 
[http://ubuntuforums.org/attachment.php?attachmentid=53346&d=1197785907](http://ubuntuforums.org/attachment.php?attachmentid=53346&d=1197785907)

I didn't create the batch file, simply typed the commands into terminal.

Finally make sure that the line:

export WINEPREFIX="$HOME/.ies4linux/ie6"

Matches your correct directory path.

Hope this helps.[/COLOR]

#!/usr/bin/env bash
export WINEPREFIX="$HOME/dave/.ies4linux/ie6
winefile

---

