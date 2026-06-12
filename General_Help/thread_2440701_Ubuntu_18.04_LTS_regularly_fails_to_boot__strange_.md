---
title: "Ubuntu 18.04 LTS regularly fails to boot / strange booting behaviour"
date: 2020-04-14
forum: General Help
---

### Post by jcdenton1995 on 2020-04-14
[COLOR=#D7DADC][COLOR=#000000]Hello all,

[/COLOR]
[COLOR=#000000]Toshiba SATELLITE-C870D-11X[/COLOR]
[COLOR=#000000]AMD® E2-1800 apu with radeon(tm) hd graphics × 2[/COLOR]
[COLOR=#000000]Ubuntu 18.04.4 LTS 64 bit[/COLOR]
[COLOR=#000000]8gb RAM (Ubuntu says 5.6gb but I thinks that's "usable ram") either way it's enough[/COLOR]

[COLOR=#000000]
[/COLOR]
[COLOR=#000000]I  recently installed Ubuntu 18.04 LTS on my Toshiba Satellite laptop, no  dual boot, just Ubuntu. On roughly 3/4 attempts Ubuntu will fail to  boot, the Toshiba logo appears when I power on the laptop, then it  disappears and is momentarily replaced by the purpley Ubuntu background  (without the little Ubuntu graphic), then the Toshiba logo appears  momentarily again before one of three things happens.[/COLOR]
[COLOR=#000000]
[/COLOR]

[LIST=1]
[*][COLOR=#000000]the  screen goes off, not just blank but off, as in no backlight or  anything. when this happens it remains this way until I hold down the  power button.[/COLOR] 
[*][COLOR=#000000]The  Ubuntu loading animation appears before displaying the login screen,  however the laptops keyboard and track pad don't work making it  impossible to login. A USB mouse will work however without a peripheral  keyboard I'm unable to log in.[/COLOR] 
[*][COLOR=#000000]the  same as number 2 but now the keyboard and track pad do work and I am  able to login, when this happens Ubuntu seems to work pretty flawlessly  once I am in[/COLOR] 
[/LIST]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]Like I say, number three occurs maybe 1/4 times I try to log in. Some things that might be important are...[/COLOR]
[COLOR=#000000]
[/COLOR]

[LIST]
[*][COLOR=#000000]I checked the SHA256 signature when I downloaded the Ubuntu ISO file and it checked out.[/COLOR] 
[*][COLOR=#000000]After  installing I updated the OS and downloaded a few packages like  gnome-tweak-tool, ubuntu-restricted-extras, OpenRA (a game) and ADB  (android debug bridge)[/COLOR] 
[*][COLOR=#000000]secure boot is deactivated[/COLOR] 
[*][COLOR=#000000]I can load the GRUB[/COLOR] 
[*][COLOR=#000000]when using the BIOS/UEFI  boot menu to select the boot device, I select my HD and it offers me two options; "ubuntu" or "Ubuntu"[/COLOR] 
[*][COLOR=#000000]For  some reason when I load the GRUB, selecting the boot options displays  two different versions of Ubuntu, and their recovery modes, so 4 options  total, i'm not sure if this is normal behavior?
[/COLOR] 
[/LIST]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]Looking at BOOT.LOG the only thing that looks out of place are two lines which read...
[/COLOR]

```

[COLOR=#000000]"[FAILED]  Failed to start Load/Save Screen Backlight Brightness of  backlight:acpi_video0. See 'systemctl status  systemd-backlight@backlight:acpi_video0.service' for details."[/COLOR]
```[COLOR=#000000]
[/COLOR]
[COLOR=#000000](However  with the aid of a helpful redditor we ascertained that the system is  falling back on the "radeon_bl0" driver, so I believe that's not a  problem.)
[/COLOR]
```
[COLOR=#000000]"[*     ] A start job is running for dev-disk-by\x2duuid-3F2E\x2d5F98.device"[/COLOR]
```[COLOR=#000000]
[/COLOR]
[COLOR=#000000]Sometimes  the above example repeats up to 5 times with an increasing number of  asterisks. The UUID apertains to the EFI partition of my HD, which is  mounted at /boot/efi. Once I'm eventually logged in I have  no problem browsing the contents through either the terminal or  nautilus, furthermore the GNOME disk tool can see the partition and  doesn't immediately ring any alarm bells.
[/COLOR]

[COLOR=#000000]I'm  not sure if the OS is actually failing to boot or if it's a driver  issue with the screen / keyboard / track pad , maybe failing to load the  necessary drivers? There is nothing else in the boot log that looks  shifty, but I don't know what I'm looking at so the only things I could  suggest are the ones with a big red "FAILED" next to them, or a red  asterisk.
[/COLOR]
[COLOR=#000000]Any help is appreciated! I have included everything I can think of, happy to provide the boot log if anyone is interested :)
[/COLOR]
[/COLOR]

---

### Post by lvm on 2020-04-14
boot.log is seldom helpful, check /var/log/syslog

---

### Post by jcdenton1995 on 2020-04-14
Is there anything in paticular I should look for in there, I've scanned over it but I wouldn't know what to look for. The log seems to begin with the first thing I did after finally getting it to boot this morning, which was plugging in my phone via usb...

---

### Post by lvm on 2020-04-14
You should look for anything suspicious at the time when computer failed to boot. Unless you changed logrotate settings, older logs can be found in syslog.1, syslog.2.gz and so on.

---

### Post by jcdenton1995 on 2020-04-14
I honestly wouldn't know what was suspicious and what wasn't, I can upload the log somewhere if that helps? it only seems to record what occurs after the system has booted i.e whatever I do as soon as I have managed to log in, nothing jumps out at me but then it wouldn't.

---

### Post by dragonfly41 on 2020-04-14
You might wish to try [petit]("http://crunchtools.com/software/petit/") to make more sense of log files.

Word frequency analysis allows searching for keywords (clues) in the corpus.

---

### Post by jcdenton1995 on 2020-04-14
Thanks that looks really handy, there is just way too much in there to go through line by line, especially if I dont know exactly what I am looking for. I'll take a moment to get to grips with the tool and see if it turns up anything suspicious and then update in a day or two!

---

### Post by dragonfly41 on 2020-04-14
I find text mining tools to have many usages, not just in analysing log files. A more advanced tool to explore is [AntConc]("https://www.laurenceanthony.net/software/antconc/").

The files must have *.txt extension so I have just copied my /var/log/syslog to /var/log/syslog.txt
then with AntConc launched inject syslog.txt into Corpus Files (left panel) then select Word List tab, use * as Search Term then Start.
Sort by Frequency or Word, followed by Start.

You can sort keys by frequency or alphabetical order. Select a keyword and Concordance tab shows where it appears in syslog.txt.

A more advanced usage (after gaining experience) is to submit a list of keywords for a particular analysis.  This list might include keywords such as 
error, warn, crash to narrow down the search. Even more advanced use is to create a lemma list which is a list of keywords to ignore.  This really is an valuable tool more used for corpus linguistics. In this case of usage the text corpus is one or more system logs.

Another usage in Ubuntu might be analysis of boot-repair log.

[P.S.] to narrow down search to a time zone you might search by date/time (e.g. around when your system froze)  ..

e.g. search term: Apr 14 10:32:20

or use regex expressions for advanced searches.

---

### Post by jcdenton1995 on 2020-04-15
Thanks for the detailed reply, I don't think my knowledge is good enough to start analyzing logs yet (but I did have a go)

So I downloaded Petit and played around with it, hashed the log, did a word count etc. but didn't really know what i was looking for, then I opened the log in gedit and searched for words like "fail", "error" etc. but there were many instances, and again I didn't know which ones were serious and which ones were trivial, for example there were 25 examples of "fail" albeit over multiple boots.

Finally I learned there is a GNOME log viewer so I opened that and under the "important" tab there is an entry with a priority of zero which reads...

```
do_IRQ: 155 No irq handler for vector
```

I googled it and it seems to be a common error for various distros, could this possibly be the cause of the problems? I get this entry for pretty much every boot.

The other unusual thing is that in the syslog there are four or five entries, all immediately before the first entry of a boot, which simply read "/00/00/00/00" but going on and on for much longer, sometimes 500 characters in a line. Gedit highlights them in red and Petit was unable to parse these lines so I had to make a copy of the log, remove the lines and then use that with Petit. Seems unsual to me?

Edit: Not to muddy the waters but something else significant seems to be that very very similar to when I try to boot and the screen just goes black, I get exactly the same symptom when closing the laptop lid. The laptop hibernates, I open the lid, the screen goes black, I close the lid and open it again and the screen is still black, I open the lid again and it works as if nothing was ever wrong, I enter my password and I'm away. Also occasionally the screen does come on but the trackpad and keyboard don't work at all, similar to when booting. I just open and close the lid and hope that it works when the laptop wakes up again...

Edit II: So I seem to have solved the black screen issue by editing the line ```
GRUB_CMDLINE_LINUX_DEFAULT=
``` and removing ```
quiet splash
``` replacing it with ```
nomodeset
```My understanding is that this stops the kernel from loading a generic Linux driver, intended to allow the splash animation to be displayed, that is incompatible with some graphics cards (I have integrated graphics though so not sure how it works with that). It would be really handy if someone more computer literate could clarify this. I still have problems with the keyboard and trackpad not working on occasion though, possibly a driver issue also?

---

