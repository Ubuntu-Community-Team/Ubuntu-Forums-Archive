---
title: "What command to get a Samsung SCX-4100 multifunction printer to scan under 14.04"
date: 2016-08-07
forum: General Help
---

### Post by nicnok on 2016-08-07
I am having similar problems with my Samsung SCX-4100, reporting "**Error: Failed to start scanner: Error during device I/O**" but on 14.04, not 16.04.
I am following the helpful advice above but only get so far: 
I get outputs of:
[B]~$ scanimage -L
device `smfp:usb;04e8;3413;0123456789ABCDEF' is a Samsung Samsung SCX-4100 Series on USB Scanner[/B]
however when I input: **~$  scanimage -A -d `smfp:usb;04e8;3413;0123456789ABCDEF'**
all I get is **'> **' 
As far as I am aware this is the Terminal prompt saying 'instruction incomplete'. 
What have I done wrong please?

---

### Post by pqwoerituytrueiwoq on 2016-08-07
> **nicnok said:**
> I am having similar problems with my Samsung SCX-4100, reporting "**Error: Failed to start scanner: Error during device I/O**" but on 14.04, not 16.04.
I am following the helpful advice above but only get so far: 
I get outputs of:
[B]~$ scanimage -L
device `smfp:usb;04e8;3413;0123456789ABCDEF' is a Samsung Samsung SCX-4100 Series on USB Scanner[/B]
however when I input: **~$  scanimage -A -d `smfp:usb;04e8;3413;0123456789ABCDEF'**
all I get is **'> **' 
As far as I am aware this is the Terminal prompt saying 'instruction incomplete'. 
What have I done wrong please?
you should have made your own thread, if you feel this thread is relevant link to it
your issues is you used a ` not a ' to the left of smfp, you must use either single or double quotes not a tick
ticks are using for putting commands inside commands

---

### Post by nicnok on 2016-08-08
many thanks for the answer - the 'tick' came from the output of [B]~$ scanimage -L
 [/B]ie[B] device `smfp:usb;04e8;3413;0123456789ABCDEF' is a Samsung Samsung SCX-4100 Series on USB Scanner
[/B]
I have adjusted the input to:
**~$ scanimage -A -d 'smfp:usb:04e8:3413:0123456789ABCDEF'**
it now runs but the output just says
**scanimage: open of device smfp:usb:04e8:3413:0123456789ABCDEF failed: Invalid argument**

Sorry if this is in the wrong thread - the reason I deliberately put it here is that my query relates only to the operation of instructions given earlier in the thread [& _only_ to that issue - - is it ok to start another thread if I can get the instructions in this helpful post to work but still have a problem? - if not what should I call the new thread?].

---

### Post by pqwoerituytrueiwoq on 2016-08-08
scanimage -L is using semi colons you used colons this time
how about you just do this:
```
scanimage -A -d "$(scanimage -L | cut -d'`' -f2 | cut -d"'" -f1;sleep 1)"
```
yes the sleep 1 is needed, at least with a networked scanner

---

### Post by nicnok on 2016-08-09
[**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("https://ubuntuforums.org/member.php?u=865458"), thanks for your help.
I input **scanimage -A -d "$(scanimage -L | cut -d'`' -f2 | cut -d"'" -f1;sleep 1)"**

and got:
[B]All options specific to device `smfp:usb;04e8;3413;0123456789ABCDEF':
    --preview[=(yes|no)] [no]
        Request a preview-quality scan
  Image Quality:
    --mode Color - 16 Million Colors|Grayscale - 256 Levels|Black and White - Line Art [Color - 16 Million Colors]
        Set the color composition mode of the scanned image
    --resolution 75|100|150|200|300|600|1200dpi [300]
        Set the resolution of the scanned image
  Scan Area:
    --page-format Statement|Statement(Rotated)|A5|A5(Rotated)|B5(JIS)|Executive|A4|Letter|Custom [A4]
        Set the paper format of the scanned page
    -l 0..215mm [0]
        Set left position of the scan area
    -t 0..297mm [0]
        Set top position of the scan area
    -x 0..215mm [210]
        Width of scan-area.
    -y 0..297mm [297]
        Height of scan-area.[/B]

So I went onto thread #11 above. After some adjusting I input:
[B]sudo scanimage -d 'smfp:usb;04e8;3413;0123456789ABCDEF' -l 0 -t 0 -x 210 -y 279 --resolution 75 --mode 'Color' --format=pnm > '/tmp/scan_file1.pnm'

[/B]and got:
[B]scanimage: setting of option --mode failed (Invalid argument)

[/B]I went into the WSane dialogue and changed 'Colourscan' to 'Greyscale' [its a B&W printer] then input:
[B]scanimage -A -d "$(scanimage -L | cut -d'`' -f2 | cut -d"'" -f1;sleep 1)"
[/B]and was amazed by this output:
[B]scanimage: open of device smfp:usb;04e8;3413;0123456789ABCDEF failed: Error during device I/O
[/B]
I am confused. Perhaps it's time for me to follow your wise advice and open another thread? If so where should I open it and what sould I call it please?

---

### Post by pqwoerituytrueiwoq on 2016-08-09
With your scanner  you mode options are **Color - 16 Million Colors|Grayscale - 256 Levels|Black and White - Line Art**

i do NOT see "Color" as a option do you? but, i do see "Color - 16 Million Colors" 
Tthat last command tells you all scanner specific options

therefore you would use this command
[FONT=courier new]sudo scanimage -d 'smfp:usb;04e8;3413;0123456789ABCDEF' -l 0 -t 0 -x 210 -y 279 --resolution 75 --mode 'Color - 16 Million Colors' --format=pnm > '/tmp/scan_file1.pnm'[/FONT]
if that command gives you a usable file in your /tmp folder the software in my signature will work fine for you

you would be better off at this point asking a mod to split the thread at this point
i would classify this as general help as what you are seeking is how to format your command for your scanner

i would say your scanner driver tried to over simplify its settings, but that is just my $0.02 opinion

as for that I/O error your scanner probably does not like to get more than 1 command at a time (that is why i put a sleep 1 in that command i gave you)

---

### Post by howefield on 2016-08-11
Posts split to own thread and moved to the "*General Help*" forum as requested.

---

### Post by nicnok on 2016-08-11
[**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("https://ubuntuforums.org/member.php?u=865458")  thank you for your patience and very appropriate simple advice. I have  tried the command in thread #19 but there are still problems. 
I see mad has split the thread - once I find where mod has put it I'll  continue to post & update in whatever thread that turns out to be.
I  could add in passing that I discovered a file called 'test.pnm' in  Desktop [sadly value =0bytes] but, [so] something at least must be  working!

---

### Post by pqwoerituytrueiwoq on 2016-08-11
how about i make the command save it to your desktop folder, i use the /tmp folder almost everything i do when testing stuff casue it will be deleted later when i reboot after a kernel update (i never bother to delete the junk later)
```
sudo scanimage -d  'smfp:usb;04e8;3413;0123456789ABCDEF' -l 0 -t 0 -x 210 -y 279  --resolution 75 --mode 'Color - 16 Million Colors' --format=pnm > ~/Desktop/"testScan_$(date).pnm"
```

---

### Post by nicnok on 2016-08-12
Thanks again for persisting with this.
I input the code line you very kindly worked out for me and got 
**scanimage: sane_start: Error during device I/O**
 but I did find a file on Desktop called “testScan_Fri Aug 12 09:26:02 BST 2016” BUT, again size was 0bytes. 

However a bit strange …As I was doing other work I needed to print something, so I loaded the empty paper tray, then thought 'wonder whether that makes any difference?' Well – I got a nice 1.5Mb scan. 

We're there I thought, so I then tried to scan using the drop-down on the ubuntu menu bar [Applications>Graphics>XSane image scanning program] - alas, no result [ERROR report]. 
So returned to Terminal and re-input
** sudo scanimage -d  'smfp:usb;04e8;3413;0123456789ABCDEF' -l 0 -t 0 -x 210 -y 279  --resolution 75 --mode 'Color - 16 Million Colors' --format=pnm > ~/Desktop/"testScan_$(date).pnm" **
Puzzlingly, output is [B]scanimage: open of device smfp:usb;04e8;3413;0123456789ABCDEF failed: Error during device I/O.
[/B]
I opened and closed the paper drawer then tried again – no result. I turned off and on the printer – tried to scan from dialogue – scanner whirrs & moves but no scan appears on-screen [where would GUI save it?] 

Turn prntr off & on & tried terminal input: output now **scanimage: sane_start: Error during device I/O.** 
Do you think you're on to something when you conjectured that maybe the  “scanner driver tried to over simplify its settings,.. “ & “...... your scanner probably does not like to get more than 1 command at a time” 

Any suggestions please?

---

### Post by pqwoerituytrueiwoq on 2016-08-12
the scanner software in my signature should work (very nice web based gui)
if the debug console gives you a I/O error when detecting scanners comment out this line:
[https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/index.php#L631](https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/index.php#L631) (the line right above [FONT=courier new]sleep(1);[/FONT])
i have actually encountered this error before, but it only only affected shared scanners
* if this does NOT give a I/O error you will not have a issue
```
scanimage -A -d "$(scanimage -L | cut -d'`' -f2 | cut -d"'" -f1)"
```

you could try a newer driver, or test on a live usb/cd of 16.04
[https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git)
```
sudo apt-add-repository ppa:rolfbensch/sane-git -y && sudo apt-get update && sudo apt-get upgrade
```

---

### Post by nicnok on 2016-08-19
***I have tried without success to get mod to move the following exchange from 'Private' into this thread:***

Sorry to check but do I do this to get the SCX-4100 to scan on 14.04?:
Go to [https://github.com/GM-Script-Writer-...wiki/Downloads]("https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/wiki/Downloads") 
Download [URL="https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/archive/master.tar.gz"]PHP-Scanner-Server_NEXT.tar.gz 
[/URL] Presumably this will give a start button on Desktop?
Hitting the start button will automatically open a "debug console".
If the debug console gives a I/O error when detecting scanners put '#' at the beginning and end of this line:
[https://github.com/GM-Script-Writer-...index.php#L631]("https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/index.php#L631") (the line right above [FONT=courier new]sleep(1);[/FONT])

If the above is incorrect will [PHP-Scanner-Server_NEXT.tar.gz ]("https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/archive/master.tar.gz")only allow scans from Terminal with the following code?:
scanimage -A -d "$(scanimage -L | cut -d'`' -f2 | cut -d"'" -f1)"   ]

The alternative you suggest is taking:
 [ttps://launchpad.net/~rolfbensch/+a...buntu/sane-git]("https://launchpad.net/%7Erolfbensch/+archive/ubuntu/sane-git") 
but that will only work on 16.04 {after the troubles I had tuning 14.04 to my needs I am reluctant to upgrade for now}

I hope I have got this at least nearly right - thanks again for your attention!

**[[B][COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("https://ubuntuforums.org/member.php?u=865458") KINDLY REPLIED:[/B]

that PPA does work on 14.04 i am using it right now on 14.04
i'm not moving my main system off 14.04 till i get all the kinks worked out to my liking on my laptop
i re-read your last post, i'd say try the PPA and hope that removes the I/O error you are getting
once you are able to get this command to NOT give a I/O error:
[FONT=Courier New]sudo scanimage -d  'smfp:usb;04e8;3413;0123456789ABCDEF' -l 0 -t 0 -x 209 -y 278  --resolution 75 --mode 'Color - 16 Million Colors' --format=pnm >  ~/Desktop/"testScan_$(date).pnm" [/FONT]
and just for kicks try a different format
[FONT=Courier New]
[LIST]
[*]sudo scanimage  -d 'smfp:usb;04e8;3413;0123456789ABCDEF' -l 0 -t 0 -x 209 -y 278  --resolution 75 --mode 'Color - 16 Million Colors' --format=tiff >  ~/Desktop/"testScan_$(date).tiff" 
[*]sudo scanimage -d  'smfp:usb;04e8;3413;0123456789ABCDEF' -l 0 -t 0 -x 209 -y 278  --resolution 75 --mode 'Color - 16 Million Colors' --format=png >  ~/Desktop/"testScan_$(date).png" 
[*]sudo scanimage -d  'smfp:usb;04e8;3413;0123456789ABCDEF' -l 0 -t 0 -x 209 -y 278  --resolution 75 --mode 'Color - 16 Million Colors' --format=jpeg >  ~/Desktop/"testScan_$(date).jpg" 
[/LIST]
[/FONT]
this alternate GUI will work
*just use the install script see the video guide to install the software
**I now say: Sorry, I have been busy. I need to bone up on PPAs.  **Once I am confident I shall give it a go, thanks again.

---

### Post by kurt18947 on 2016-08-19
A couple alternatives if you wish to explore them

1- Samsung has Linux drives for many of their devices. [http://www.samsung.com/us/support/downloads#Printers](http://www.samsung.com/us/support/downloads#Printers)

2- VueScan. You'd need to check if it supports your printer. It finds a networked Samsung SL-M2870 with no user intervention at all. [https://www.hamrick.com/#download](https://www.hamrick.com/#download).  The download looks like it's for Windows only but includes Linux files as well. It doesn't install like a .deb or .rpm package but rather is self contained. Double click the linux executable (set the execute bit of needed) and away it goes. The download is functional but scans have a watermark on them. Paying for a license removes the watermark. We paid for a license because of a Canon scanner being supported but not fully (light in the scanner lid didn't come on).

---

### Post by pqwoerituytrueiwoq on 2016-09-04
to add the ppa you can run this command
[FONT=Courier New]sudo add-apt-repository ppa:rolfbensch/sane-git -y && sudo apt-get update && sudo apt-get install sane-backends[/FONT]
This will get you the latest version of the scanner backend system, by latest i mean it is updated daily if there are any changes

---

### Post by nicnok on 2017-03-17
Managed to hobble on for a while however trouble's struck again, but sadly > **pqwoerituytrueiwoq said:**
> to add the ppa you can run this command
[FONT=Courier New]sudo add-apt-repository ppa:rolfbensch/sane-git -y && sudo apt-get update && sudo apt-get install sane-backends[/FONT]
This will get you the latest version of the scanner backend system, by latest i mean it is updated daily if there are any changes

this doesn't work: Terminal reports 62 data lines ending with "E: Unable to locate package sane-backends".
I can paste the lines into this thread if deemed helpful.

---

### Post by nicnok on 2017-04-07
> **nicnok said:**
> Managed to hobble on for a while however trouble's struck again, but sadly 

this doesn't work: Terminal reports 62 data lines ending with "E: Unable to locate package sane-backends".
I can paste the lines into this thread if deemed helpful.

I thought to record progress on this to finalise this thread. Rather than repeat quite a lot of intercourse here, my Q  [http://www.bchemnet.com/suldr/forum/index.php?topic=319.0](http://www.bchemnet.com/suldr/forum/index.php?topic=319.0)  on the[ Samsung Unified Linux Driver Repository Forum ]("http://www.bchemnet.com/suldr/forum/index.php") shows how I eventually got Sane to work.

I have residual problems with getting Sane to function properly - hopefully recorded elsewhere on this, or the Sane site.

---

