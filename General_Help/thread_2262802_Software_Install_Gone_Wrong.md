---
title: "Software Install Gone Wrong"
date: 2015-01-27
forum: General Help
---

### Post by Alex Eagle on 2015-01-27
I installed a program from a disc a while back and it went perfectly well.

However!... Lol. Those words that hang in the air so... :-P I messed something up by removing an icon of the software from somewhere or something and then when trying to open the program, it was obvious that it wasn't installed.

I tried to put the install disc in, so as to reinstall, but the Wizard thought that it was installed already. It therefore only gave me the option to open the application.

I looked in />usr>share>applications and removed it from there. I also searched all files withtin "/" (computer) and deleted what I could without fear of messing up kernal or goodness knows what else. After doing all of that I tried the install disc again. The same thing happened. Somehow the disc thinks it's still installed. Whether that's because the disc stores info about which computers it installs onto or whether there's something on my computer that's telling it it's installed I don't know. 

When I said > I looked in />usr>share>applications and removed it from there.  I also searched all files withtin "/" (computer) and deleted what I  could without fear of messing up kernal or goodness knows what else., I'm of the opinion that it's incredibly unlikely that this program is contained in the kernal. But you never know... XD I didn't want to harm the computer so much so that I'd have to fresh-install ubuntu, so I was being extra cautious.

P.S: I'm using WINE for this application. It's Windows only. There is no Linux version.

P.P.S: While I was typing that "P.S:" I accidentally typed "Linuxz". That got me thinking. I've seen "Linuz" written sometimes before. As far as I can see, it's not a typo. So what's the difference between Linux and Linuz? If indeed "Linuz" isn't a typo.

:-) Thanks

---

### Post by kc1di on 2015-01-27
What's the Program,  It may have created a hidden config file in your home Directory which it reads. 
Go to you home directory and click on view and show hidden files. 
see if there is anything there.

---

### Post by Penguin360 on 2015-01-27
If the software was installed via Wine, then it shouldn't be listed under /usr/share/applications, instead it should be under Wine environment. Go to Program Files under Wine to see if the software is there.

---

### Post by Holger_Gehrke on 2015-01-27
> **Alex Eagle said:**
> 
P.S: I'm using WINE for this application. It's Windows only. There is no Linux version.


And there's the problem. Wine has it's own deinstaller. Windows programs installed in wine are in the user's directory in a hidden directory, usually somewhere in '~/.wine/drive_c/Program\ Files/'. They are completely separate from Linux, there should not have been anything related to it anywhere else, except a .desktop file in '~/.local/share/applications' (or wherever your version of Ubuntu stores them).

> **Alex Eagle said:**
> 
P.P.S: While I was typing that "P.S:" I accidentally typed "Linuxz". That got me thinking. I've seen "Linuz" written sometimes before. As far as I can see, it's not a typo. So what's the difference between Linux and Linuz? If indeed "Linuz" isn't a typo.


You've probably seen that in the '/boot' directory. The kernel files are named 'vmlinuz-x.y.z-nn-whatever'. The z instead of an x is probably meant to tell us that it's a compressed image.

---

### Post by Alex Eagle on 2015-01-28
Thanks. And you @Penguin360. 

Will check and then update this post with what I find.

**UPDATE:** Can anybody give me an exact path? I'm having trouble finding the Wine directory. :-/

---

