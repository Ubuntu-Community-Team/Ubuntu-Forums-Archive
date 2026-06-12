---
title: "Ubuntu Freezes VERY OFTEN"
date: 2007-04-29
forum: General Help
---

### Post by GSF1200S on 2007-04-29
This is new territory for me. Ubuntu is freezing on average every 15-20 minutes, and im starting to loose my cool. Any other problem I can work through, but freezing is just not cool...

It doesnt matter whether Beryl or Metacity is running, it still freezes. Its not will im doing any particular thing. Everything will be great, and then bam, it locks up. My mouse will still move, and if I have music playing, the music will continue to play, as well as go to the next song automatically, although not even my hotkeys will change the song. I cant click anything, and even ctrl alt backspace wont work.

This all started about 2 days ago when my Xwindow crashed. I hadnt installed any updates for my kernel or the xorg.conf file, so I dont have a clue what caused it. I created a new Xorg.conf and reinstalled my video drivers, as well as recompiling and installing my madwifi drivers. I added "load dbe" to the modules section of my xorg.conf, as well as the visuals (ARGBX visuals or something like that). I uninstalled and reinstalled Beryl. 

I dont know what to do.. its so bad, im actually thinking about getting on Windows and staying there for a while until someone has an answer. Im all for working on problems, but at a forced shutdown every 15-20 minutes, this is getting rediculous. God I hope my CPU isnt overheating or something.. I may be forced to abandon Linux due to my BIOSes lack of ACPI support...

Any ideas??](*,)

---

### Post by tictacman on 2007-04-29
Have you tried running the live cd for any length of time?  Does it still have the same effect? Are you sure its not the wifi card, a wrongly configured wifi card had similar effects on one of my machines.  Perhaps, if you can, remove the wifi card and run the machine for a while to see if it makes any difference.  Also I have to wonder how good driver for particularly card is, as there has been some gripes on forums regarding nvidia drivers.

I did think for a moment it might be power supply or loose leads in the machine, but the fact that machine keeps playing your music rules that out.  I bet if you had another machine you would be able ssh into it without problems.

If your concerned about temperature why not install lm sensors?

---

### Post by GSF1200S on 2007-04-29
> **tictacman said:**
> Have you tried running the live cd for any length of time?  Does it still have the same effect? Are you sure its not the wifi card, a wrongly configured wifi card had similar effects on one of my machines.  Perhaps, if you can, remove the wifi card and run the machine for a while to see if it makes any difference.  Also I have to wonder how good driver for particularly card is, as there has been some gripes on forums regarding nvidia drivers.

I did think for a moment it might be power supply or loose leads in the machine, but the fact that machine keeps playing your music rules that out.  I bet if you had another machine you would be able ssh into it without problems.

If your concerned about temperature why not install lm sensors?

I cant use LM sensors because my ACPI support from my Phoenix BIOS sucks. The thing is, I havent had this problem before; it started happening after my Xwindow unexplainably crashed. My wifi card was installed the same way Ive done it for a while now without any problems... madwifi from source
sudo make
sudo make install
sudo make clean

Yeah, for Nvidia cards being so highly regaurded.. we sure are having problems.. I wonder if my drivers are a problem. Does anyone have any idea when the next set of drivers is going to be released? How about reverting to older drivers?

---

### Post by tictacman on 2007-04-29
> Phoenix BIOS sucks - yeah you're right there, I have 2 boards with phoenix, hopefully I will check next time I go to buy another board

---

### Post by Wiebelhaus on 2007-04-29
As with any freezing problems always check 

[Power supply]("http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=1647108&Sku=ULT31553&SRCCODE=GOOGLEBASE&CMP=OTC-GOOGLEBASE")

[Ram]("http://www.memtest86.com/")

[Hdd]("http://pcsupport.about.com/gi/dynamic/offsite.htm?zi=1/XJ&sdn=pcsupport&cdn=compute&tm=8&f=00&su=p284.7.420.ip_&tt=3&bt=0&bts=0&zu=http%3A//support.wdc.com/download/index.asp%3Fcxml%3Dn%26pid%3D999%26swid%3D3")

Mainboard diags as well as all the others can be found [here]("http://www.ultimatebootcd.com/")

I'm not saying your hardware is faulty but as a matter of protocol you always check these things.

---

