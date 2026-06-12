---
title: "problem getting gui for bios chip reprogrammer"
date: 2018-01-06
forum: General Help
---

### Post by ortermagic on 2018-01-06
Some time ago I managed to kill the cmos chip on a motherboard (asus m5a 78l-m) the chip is detatchable from the mobo, so I ordered a usb reprogrammer
from China,
 [ATTACH=CONFIG]278071[/ATTACH][ATTACH=CONFIG]278072[/ATTACH]
the image shows the chipper wirh the cmos/bios chip in situ. Heres the problem...
 The chipper arrived with no usage details, so i went to google and found some helpful info relating to windows but zilch on Linux/Ubuntu...
I think I found a driver (CH341PAR_LINUX) but I can't seem to raise the gui in the way others were able in the win environment.
Has anyone had experience  of this that can help me?

---

### Post by dragonfly41 on 2018-01-06
I know zilch about this topic but surely you can google? ...

[https://github.com/setarcos/ch341prog](https://github.com/setarcos/ch341prog)

and here ... [https://blog.danman.eu/ch341a-usb-serial-eeprom-reader-under-linux/](https://blog.danman.eu/ch341a-usb-serial-eeprom-reader-under-linux/)

---

### Post by ortermagic on 2018-01-06
Thanks df I have already searched the net and perused the danman blog.
 It's useful but does not help me with the 'make' commands necessary. 
I have very limited knowlege of the art of compiling.
 I think I need to be shown the necessary compilation commands using the terminal.
Hoping to find someone who can help me.
Thanks for the git hub link I missed that, I have just downloaded that prog, but I have no idea how to implement it.

---

### Post by ortermagic on 2018-01-06
Please bear in mind that I'm an old timer (73) with only a fragmentary knowlege of computers.

---

### Post by dragonfly41 on 2018-01-06
Copy the download into a convenient folder.

Reading the README file it says ..

Compiling
=========


	gcc -o ch341eeprom ch341eeprom.c ch341funcs.c -lusb-1.0


and then after running the above compilation command, to run ...

./ch341eeprom

---

### Post by ortermagic on 2018-01-06
Thank you Looking at the git hub results I see a confusing list [https://github.com/setarcos/ch341prog](https://github.com/setarcos/ch341prog)[https://github.com/setarcos/ch341prog()](https://github.com/setarcos/ch341prog()) which of these should I use?

---

### Post by dragonfly41 on 2018-01-06
Actually, if you read the page here

[https://github.com/setarcos/ch341prog](https://github.com/setarcos/ch341prog)

there is a link in there ...

[http://sourceforge.net/projects/ch341eepromtool/](http://sourceforge.net/projects/ch341eepromtool/)

click on the green download button.

You will see a downloaded file in your ~/Downloads folder.
ch341eepromtool_0.5.tar.gz

Untar this file and place ch341eepromtool_0.5 in folder such as ~/ch341eepromtool_0.5

I am referring to the README in that latter download 8.5 MB in size.
Also useful pdf documents in docs folder.

Make sure that you run your gcc command in the ~/ch341eepromtool_0.5 folder.

You might find some missing dependencies .. read README again.

---

### Post by ortermagic on 2018-01-06
Oh MAN I feel so blind (i tend to assume that these links only serve to confuse me more, I really aught to try harder)
Thanks for pointing that out...I think I might be able to unravel the mystery now thanks again. 
I will now implement data received and let you know how I got on ...  laters my friend!

---

### Post by dragonfly41 on 2018-01-06
Also in reading from the two links earlier there is this package flashrom which is actually seen in my Ubuntu Software Centre.

[https://www.flashrom.org/Downloads](https://www.flashrom.org/Downloads)

```
sudo apt-get update
sudo apt-get install flashrom
```

I don't know if this helps.

Reference: [danman blog]("https://blog.danman.eu/ch341a-usb-serial-eeprom-reader-under-linux/")

> [COLOR=#2B2B2B][FONT=Lato]Note that Flashrom &#8211; [/FONT][/COLOR][https://www.flashrom.org/](https://www.flashrom.org/)[COLOR=#2B2B2B][FONT=Lato] &#8211; also supports the CH341A (and is open source and runs on Linux). I&#8217;ve personally had better experience with it than with the tools listed here.[/FONT][/COLOR]

---

### Post by ortermagic on 2018-01-06
These are my naive attempts at implementing terminal commands
As you can probably see I am pretty clueless.

```
ortermagic@ortermagic:~$ sudo apt-get update
[sudo] password for ortermagic: 
Hit:1 http://archive.ubuntu.com/ubuntu artful InRelease
Get:2 http://archive.ubuntu.com/ubuntu artful-updates InRelease [78.6 kB]
Hit:3 http://archive.canonical.com/ubuntu artful InRelease
Get:4 http://archive.ubuntu.com/ubuntu artful-backports InRelease [72.2 kB]
Get:5 http://archive.ubuntu.com/ubuntu artful-security InRelease [78.6 kB]
Get:6 http://archive.ubuntu.com/ubuntu artful-proposed InRelease [235 kB]
Fetched 464 kB in 1s (383 kB/s)                             
Reading package lists... Done
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:107
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:107
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:107
W: Target Translations (multiverse/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:107
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:107
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:107
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:107
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:107
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:107
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:107
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:107
W: Target Translations (multiverse/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:107
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:107
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:107
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:107
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:107
ortermagic@ortermagic:~$ sudo apt-get install flashrom
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashrom is already the newest version (0.9.9+r1954-1).
The following packages were automatically installed and are no longer required:
  linux-headers-4.13.0-16 linux-headers-4.13.0-16-generic
  linux-headers-4.13.0-17 linux-headers-4.13.0-17-generic
  linux-headers-4.13.0-19 linux-headers-4.13.0-19-generic
  linux-image-4.10.0-38-generic linux-image-4.13.0-16-generic
  linux-image-4.13.0-17-generic linux-image-4.13.0-19-generic
  linux-image-extra-4.10.0-38-generic linux-image-extra-4.13.0-16-generic
  linux-image-extra-4.13.0-17-generic linux-image-extra-4.13.0-19-generic
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
ortermagic@ortermagic:~$ flashrom --programmer ch341a_spi_
flashrom v0.9.9-r1954 on Linux 4.13.0-22-generic (x86_64)
flashrom is free software, get the source code at https://flashrom.org

Error: Unknown programmer "ch341a_spi_". Valid choices are:
internal, dummy, nic3com, nicrealtek, gfxnvidia, drkaiser, satasii, atavia,
it8212, ft2232_spi, serprog, buspirate_spi, dediprog, rayer_spi, pony_spi,
nicintel, nicintel_spi, nicintel_eeprom, ogp_spi, satamv, linux_spi,
usbblaster_spi, pickit2_spi, ch341a_spi.
Please run "flashrom --help" for usage info.
ortermagic@ortermagic:~$ flashrom ch341a_spi -r
flashrom v0.9.9-r1954 on Linux 4.13.0-22-generic (x86_64)
flashrom is free software, get the source code at https://flashrom.org

flashrom: option requires an argument -- 'r'
Please run "flashrom --help" for usage info.
ortermagic@ortermagic:~$ 

```
I appreciate your help but the info you are supplying takes me a long while to process in my brain

---

### Post by ortermagic on 2018-01-06
These are the files on my desktop

[ATTACH=CONFIG]278073[/ATTACH]

---

### Post by dragonfly41 on 2018-01-06
After running the sudo apt-get update command the first few lines in your log show that you have duplicate lines in the file /etc/apt/sources.list.

The clue is &#8220;is configured multiple times in /etc/apt/sources.list&#8221;.

Correct by editing in gedit .. to remove duplicate lines .. perhaps it would be wise to backup this file first before editing to remove duplicates.

gksu gedit /etc/apt/sources.list

...

Next point to tidy up is old kernels to be removed.
As the log says run

sudo apt autoremove

...

Finally we get to flashrom.

flashrom --help
does say
To choose the mainboard of this computer use 'internal'

So try

sudo flashrom -p internal
or if internal does not work ...
sudo flashrom -p ch341a_spi


And if you use the --read (or -r) argument you must specify the target file to receive content.

So create a blank text file ~/flashrom.txt

Then run

sudo flashrom -p internal -r ~/flashrom.txt
or
sudo flashrom -p ch341a_spi  -r ~/flashrom.txt


you can view options by running commands

flashrom --help
and
**man flashrom **     << this is an **IMPORTANT** read. Take care in using flashrom and **backup** before any writing.


P.S. If flashrom works you can discard the earlier downloaded source files now on your desktop.

---

### Post by ortermagic on 2018-01-06
Oh dear it looks a bit tricky to me

---

### Post by dragonfly41 on 2018-01-06
You can forego the [COLOR=#000000]/etc/apt/sources.list [/COLOR]cleanup advice (for now) and just try running the command

```
[COLOR=#000000]sudo flashrom -p ch341a_spi -r ~/flashrom.txt[/COLOR]
```[COLOR=#000000]

to test if it works.

I don't know why you are on this adventure. It's a learning exercise for me too.

[Later Edit]

Do read the [/COLOR][COLOR=#ff0000]Emergency Help[/COLOR][COLOR=#000000] warning here ...

[/COLOR]https://www.flashrom.org/Flashrom

**IMPORTANT: If something went wrong during flashing, do [B]NOT turn off/reboot your computer. Instead, let us help you recover. We can be contacted via [IRC]("https://www.flashrom.org/IRC") ([B]#flashrom on [freenode.net]("irc://chat.freenode.net/#flashrom"), [webchat]("http://webchat.freenode.net/?channels=flashrom&uio=d4")) or [email]("https://www.flashrom.org/Mailinglist"). Please allow for a few hours until someone responds on IRC, we're all volunteers.**[/B][/B]

---

### Post by LostFarmer on 2018-01-06
I can not help with the program. 
 I will suggest just to buy a new pre-programed chip.  I did buy a programed chip for my ASUS laptop , it did work  but it was not easy to remove/replace it , soldered in.  Note: it did not have the Win8.1 key embedded, did not expect it to.

[https://www.ebay.com/sch/i.html?_from=R40&_trksid=p2060353.m570.l1313.TR0.TRC0.H0.Xbios+chip+.TRS0&_nkw=bios+chip+asus+m5a+78l-m&_sacat=0](https://www.ebay.com/sch/i.html?_from=R40&_trksid=p2060353.m570.l1313.TR0.TRC0.H0.Xbios+chip+.TRS0&_nkw=bios+chip+asus+m5a+78l-m&_sacat=0)

---

### Post by ortermagic on 2018-01-06
Sorry for the delay df, had to have a sleep. The details below seem to show the flash chip on the usb reprogrammer is that correct, and does that imply that it is functional?
or has it read the chip on my working mobo?


```
ortermagic@ortermagic:~$ sudo flashrom -p ch341a_spi -r ~/flashrom.txt
[sudo] password for ortermagic: 
flashrom v0.9.9-r1954 on Linux 4.13.0-22-generic (x86_64)
flashrom is free software, get the source code at https://flashrom.org

Calibrating delay loop... OK.
Found Winbond flash chip "W25Q16.V" (2048 kB, SPI) on ch341a_spi.
Reading flash... done.
ortermagic@ortermagic:~$ 

```

To lost farmer, I already went down that route, ordered a chip from a Dutch firm Biosmaster and waited 3 weeks for delivery
eventually I got my money back from ebay with a £10 to sweeten the deal, then I found a branch of Biosmaster here in UK, ordered one from them. It arrived after 3 days but didn't work.
It was then that I decided to get the reprogrammer. Strange that I got so few results from ebay UK.

[URL="https://www.ebay.co.uk/sch/i.html?_from=R40&_trksid=p2380057.m570.l1313.TR0.TRC0.H0.TRS0&_nkw=bios+chip+asus+m5a+78l-m&_sacat=0"]https://www.ebay.co.uk/sch/i.html?_from=R40&_trksid=p2380057.m570.l1313.TR0.TRC0.H0.TRS0&_nkw=bios+chip+asus+m5a+78l-m&_sacat=0    


[/URL]

---

### Post by ortermagic on 2018-01-06
I had a problem whereby the lsusb results that I posted in code tags turned into a live link to ebay 
strange days

---

### Post by ortermagic on 2018-01-06
This is the result of lsusb

```
 ortermagic@ortermagic:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 1d57:fa60 Xenta 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1a86:5512 QinHeng Electronics CH341 in EPP/MEM/I2C mode, EPP/I2C adapter
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 045e:0779 Microsoft Corp. LifeCam HD-3000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ortermagic@ortermagic:~$  
```

Seems to me the adaptor is recognised, where do we go from here?

---

### Post by dragonfly41 on 2018-01-07
> [COLOR=#000000]Seems to me the adaptor is recognised, where do we go from here?[/COLOR]

This is now 'beyond my ken'.

Do heed the advice I later added to post#14 above.
If you start to *write* to flash chip then you may need help if write process fails and you brick your PC (it becomes unusable).

[P.S.]
This reference refers to flashrom.

[http://www.zoobab.com/ch341-usb-spi-i2c-uart-isp-dongle](http://www.zoobab.com/ch341-usb-spi-i2c-uart-isp-dongle)

---

### Post by ortermagic on 2018-01-07
Thank you for all your time DF.
 I am sure that the flashrom link you posted will come in handy.
I am attempting to revive an already bricked mobo using my current working pc to transfer the bios onto the busted chip(i have two of those)
I only hope that I don't somehow mess up my current working pc in the process.
You have steered me up some interesting alleys and I will be settling down now for a while in order to collate the info.
Thanks again.

---

### Post by ortermagic on 2018-02-04
I want to tell anyone interested that I have solved the problem...I was unable to create the gui for the chip programmer in linux, too hard for me to unravel, so I loaded the thing in my wifes windows laptop and fixed the chip in that. It would be useful if someone were to create an app for the CH341PAR_LINUX and put it in the software centre. It was a great relief to see the bios screen emerge.

---

