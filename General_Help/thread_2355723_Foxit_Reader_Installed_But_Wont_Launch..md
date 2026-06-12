---
title: "Foxit Reader Installed But Wont Launch."
date: 2017-03-15
forum: General Help
---

### Post by Nylo on 2017-03-15
Ive installed Foxit Reader per instructions at, [Sourcedigit]("http://sourcedigit.com/20670-how-to-install-foxit-reader-in-ubuntu-using-terminal/").  My problem is I cannot get it to launch.  By default It installed its self in my OPT folder, but mentioned to abort if I wanted it in root...  Is this my issue?

---

### Post by #&amp;thj^% on 2017-03-15
> **Nylo said:**
> Ive installed Foxit Reader per instructions at, [Sourcedigit]("http://sourcedigit.com/20670-how-to-install-foxit-reader-in-ubuntu-using-terminal/").  My problem is I cannot get it to launch.  By default It installed its self in my OPT folder, but mentioned to abort if I wanted it in root...  Is this my issue?

Run as Root is for system wide installation. I just installed the default non-root install as you are implying you did also.
See Screenshots.                           To be clear I used this command to do my install:
```
./FoxitReader.*.run

```
And not the system-wide way Via:
```
sudo ./FoxitReader.*.run
```
There is a uninstaller you can use to try again...uninstall and re-install...located>> "/home/yourusername/opt/foxitsoftware/foxitreader".

---

### Post by Nylo on 2017-03-20
I did exactly what you said per your instructions.  Uninstalled/reinstalled, but I cannot get the "ConnectedPDF" window.

---

### Post by #&amp;thj^% on 2017-03-20
> **Nylo said:**
> I did exactly what you said per your instructions.  Uninstalled/reinstalled, but I cannot get the "ConnectedPDF" window.

You can also use <Edit> and <Preferences> to see that option....if I understand you clearly, that you now have it installed.
BTW there is newer version from their site, so I uninstalled the Older Version and went with newer.
I used a different method this time to install with.
So if interested Go to this Page for Foxit Downloads:[https://www.foxitsoftware.com/products/pdf-reader/](https://www.foxitsoftware.com/products/pdf-reader/)
I choose to download to my Downloads Directory...you can make another choice or location if you want.
Then I navigated to my Downloads Folder and right clicked on the "FoxitReader2.3.1.2182_Server_x64_enu_Setup.run.tar.gz" and used the Extract here:
Then I opened a terminal and ran:
```
cd Downloads
```
Followed by:
```
./'FoxitReader.enu.setup.2.3.1.2182(r242182).x64.run'

```
Just to note here: I also did not see the "ConnectedPDF" window" This go around.
So just to remind Edit and Preferences will show the same options as the "ConnectedPDF" window" did.

---

### Post by Nylo on 2017-03-22
Downloaded "FoxitReader.enu.setup.2.1.0805(r225434).x86.run," uninstalled, followed your instructions and still have the same result.  The last window I get is foxit2.png.  When I click finish it disappears.  I then go to menu, Office, Foxit and click... And nothing happens, nothing to edit.

Downloading newer version.  Ill give that a shot.

---

### Post by #&amp;thj^% on 2017-03-22
Very sorry to hear this::o
Lets see if we can find out why.
Open Terminal and run:
```
'/home/yourusernamehere/opt/foxitsoftware/foxitreader/FoxitReader.desktop'

```
Replace "yourusernamehere" with your user name.
Paste back the errors please.

---

### Post by Nylo on 2017-03-23
Command not found, but FoxitReader.desktop is there.

I found something thats different.  "/home/***/.local/share/Foxit Software" has only one file.  "Config.XML."  But in another Linux laptop running Foxit that same path has, "cacheData (folder), Foxit Reader (folder), RMS (folder), and two error logs.

---

### Post by #&amp;thj^% on 2017-03-23
> **Nylo said:**
> Command not found, but FoxitReader.desktop is there.

That would be the one to drag to the terminal and drop in there. (Clarity "FoxitReader.desktop")
It will be a rather large out put, So if you would use code tags to wrap the return in.:D
So this a lubuntu install then?

---

### Post by dragonfly41 on 2017-03-23
I'll chip in because I have Foxit installed.
I don't understand why there is reference to this location ..
```
[COLOR=#000000][FONT=Ubuntu Mono]'/home/yourusernamehere/opt/foxitsoftware/foxitreader/FoxitReader.desktop'[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
In fact my installation is in
[/FONT][/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]'/opt/foxitsoftware/foxitreader/FoxitReader.desktop'[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
I also have
```
 ~/.local/share/Foxit Software
```

.. containing folders
cacheData
Foxit Reader
RMS

and some log files.[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2017-03-23
> **dragonfly41 said:**
> I'll chip in because I have Foxit installed.
I don't understand why there is reference to this location ..
```
[COLOR=#000000][FONT=Ubuntu Mono]'/home/yourusernamehere/opt/foxitsoftware/foxitreader/FoxitReader.desktop'[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
In fact my installation is in
[/FONT][/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]'/opt/foxitsoftware/foxitreader/FoxitReader.desktop'[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
I also have
```
 ~/.local/share/Foxit Software
```
[/FONT][/COLOR]

We are trying to find out why OP's is segfaulting
BTW:
```
~$ '/opt/foxitsoftware/foxitreader/FoxitReader.desktop'
bash: /opt/foxitsoftware/foxitreader/FoxitReader.desktop: No such file or directory

```
Mine on Unity:
```
$ '/home/me/opt/foxitsoftware/foxitreader/FoxitReader.desktop' 

```
Where "me" is my user. 
Curious, Yes.

---

### Post by dragonfly41 on 2017-03-23
> [COLOR=#000000]We are trying to find out why OP's is segfaulting[/COLOR][COLOR=#000000]
[/COLOR]I didn't realise from reading above that this is a segfault troubleshooting problem ..
I can remember posting some approach I found to pin down segfaults ..

Read post #2 here ... [https://ubuntuforums.org/showthread.php?t=2350423&highlight=segmentation+fault](https://ubuntuforums.org/showthread.php?t=2350423&highlight=segmentation+fault)

---

### Post by Nylo on 2017-03-23
Yes, Lubuntu.

No matter what I drop in it will not open.

---

### Post by mc4man on 2017-03-23
You can't run a .desktop file in a terminal as previously posted, nothing will happen.
Assuming the install placed a copy of FoxitReader.desktop in an applications folder in typical path then you can run as such
(- here the install placed a copy in ~/.local/share/applications
```

gtk-launch FoxitReader
```

---

### Post by #&amp;thj^% on 2017-03-24
> **Nylo said:**
> Yes, Lubuntu.

No matter what I drop in it will not open.
This makes it very hard to see why this happens. With no errors to see.:confused:
Looking now at dragonfly41 link for any clues we can use here.

> **mc4man said:**
> You can't run a .desktop file in a terminal as previously posted, nothing will happen.
Assuming the install placed a copy of FoxitReader.desktop in an applications folder in typical path then you can run as such
(- here the install placed a copy in ~/.local/share/applications
```

gtk-launch FoxitReader
```
Sometimes the simple things just slide right by ](*,)...LOL
By the way I can run the .desktop file from my terminal as shown in the screenshot in my pervious post. [IMG]https://ubuntuforums.org/images/smilies/confused.gif[/IMG]
Thanks mc4man this works very well here {gtk-launch FoxitReader}, and the best way to run it...now if it only works for Nylo.

---

### Post by dragonfly41 on 2017-03-24
I wonder if this might be a clue ... which I did not spot on first reading ..


post#4   FoxitReader.enu.setup.2.3.1.2182(r242182).x64.run
post#5   FoxitReader.enu.setup.2.1.0805(r225434).x86.run


This looks to me that OP has installed 32bit version, not 64bit version of Foxit, on Ubuntu 16.04.


```

http://sourcedigit.com/20670-how-to-install-foxit-reader-in-ubuntu-using-terminal/


32 Bit Ubuntu Systems
wget http://cdn01.foxitsoftware.com/pub/foxit/reader/desktop/linux/2.x/2.1/en_us/FoxitReader2.1.0805_Server_[COLOR=#ff0000]**x86**[/COLOR]_enu_Setup.run.tar.gz


64 Bit Ubuntu Systems
wget http://cdn01.foxitsoftware.com/pub/foxit/reader/desktop/linux/2.x/2.1/en_us/FoxitReader2.1.0805_Server_[COLOR=#ff0000]**x64**[/COLOR]_enu_Setup.run.tar.gz

```

---

### Post by #&amp;thj^% on 2017-03-24
> **dragonfly41 said:**
> I wonder if this might be a clue ... which I did not spot on first reading ..


post#4   FoxitReader.enu.setup.2.3.1.2182(r242182).x64.run
post#5   FoxitReader.enu.setup.2.1.0805(r225434).x86.run


This looks to me that OP has installed 32bit version, not 64bit version of Foxit, on Ubuntu 16.04.


```

http://sourcedigit.com/20670-how-to-install-foxit-reader-in-ubuntu-using-terminal/


32 Bit Ubuntu Systems
wget http://cdn01.foxitsoftware.com/pub/foxit/reader/desktop/linux/2.x/2.1/en_us/FoxitReader2.1.0805_Server_[COLOR=#ff0000]**x86**[/COLOR]_enu_Setup.run.tar.gz


64 Bit Ubuntu Systems
wget http://cdn01.foxitsoftware.com/pub/foxit/reader/desktop/linux/2.x/2.1/en_us/FoxitReader2.1.0805_Server_[COLOR=#ff0000]**x64**[/COLOR]_enu_Setup.run.tar.gz

```

+1 Good Spot! :)

---

### Post by Nylo on 2017-03-30
Sorry for not replying sooner.  Ive been out of town.

Yes, I am running 32bit on Lubuntu 16.04 LTS.

Im running two machines (one 32bit the other 64bit) with Lubuntu 16.04 LTS and Foxit works fine.  Im thinking it might be an issue with my third laptop.

---

### Post by ferryfernando on 2017-05-23
get same issue if I installed on /opt folder (system-wide). Cant launch the program form dash.
But application can running if I open from file directory

---

