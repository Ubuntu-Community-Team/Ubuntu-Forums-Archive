---
title: "Re: how to get scanner to work"
date: 2016-12-01
forum: General Help
---

### Post by juntjoo2 on 2016-12-01
I can print but can't scan.  I'm on the latest ubuntu and have a canon pixma mg4120 connected via my router and I can print just fine but get "unable to connect to scanner" with simple(yeah right) scan.  If I click "change printer" it shows "canon canon pixma 4100" so it looks like it's seeing the  right files I guess.  I've googled this but the information is all over the place and confusing. Any help would be appreciated.  Just a point to another thread. Something.

hi. so i'm trying to setup sane to make sure I can use my scanner and I get :

ben@Hal:~$ Applications > Graphics > XSane
Applications: command not found

I'm using this guide: [https://help.ubuntu.com/community/sane](https://help.ubuntu.com/community/sane)
and this is where I'm stuck. Thanks

---

### Post by PaulW2U on 2016-12-01
> **juntjoo2 said:**
> hi. so i'm trying to setup sane to make sure I can use my scanner and I get :

ben@Hal:~$ Applications > Graphics > XSane
Applications: command not found

I'm using this guide: [https://help.ubuntu.com/community/sane](https://help.ubuntu.com/community/sane)
and this is where I'm stuck.
I don't have a scanner and I have never used XSane but I can tell you that **Applications > Graphics > XSane** is not a command to be entered in a terminal but a way of directing you to XSane through your program menus if you have them, e.g. with Ubuntu GNOME or Xubuntu.

If you are using Unity (Ubuntu) then just search for XSane in the same way that you would search for any other program that isn't shown in the Launcher.

---

### Post by juntjoo2 on 2016-12-01
> **PaulW2U said:**
> I don't have a scanner and I have never used XSane but I can tell you that **Applications > Graphics > XSane** is not a command to be entered in a terminal but a way of directing you to XSane through your program menus if you have them, e.g. with Ubuntu GNOME or Xubuntu.

If you are using Unity (Ubuntu) then just search for XSane in the same way that you would search for any other program that isn't shown in the Launcher.



thanks. I would have figured the same but this is what it says here which I guess the language is kinda ambiguous.
**Step 2: Test your scanner**

[COLOR=#333333][FONT=Ubuntu]Run following command to test your scanner: [/FONT][/COLOR]

Applications > Graphics > XSane[COLOR=#333333][FONT=Ubuntu]You should see a dialog for scanning from your scanner. If SANE says that it can't find the scanner, you will need to do a manual installation.




anyway, it just got me an error I had been getting before working on this at the same point following other guides.  onto the next steps...[/FONT][/COLOR]

Does wifi work for scannning or do you need it to be connected via usb?

---

### Post by The Cog on 2016-12-01
Applications > Graphics > XSane
is referring to a sequence of menu choices from the Start button (or its equivalent, mine is an image of a penguin) in the top left corner. I don't know if Ubuntu even has a start button any more, in which case I don't know what you would do to start xsane from Unity.

But xsane probably an executable, try rust running the command **xsane** in a terminal (or if that fails, type **xs** and then press **tab** to see all possible commands that start with xs. Maybe also try **XS<tab>**

---

### Post by howefield on 2016-12-01
> **juntjoo2 said:**
> Does wifi work for scannning or do you need it to be connected via usb?

Ordinarily it should do if the the printer/scanner is wifi capable.

---

### Post by juntjoo2 on 2016-12-01
Thanks. I got it.

Yeah, it prints over wifi just fine but I was just wondering if maybe there was a limitation to the drivers maybe for my particular model. I checked that user reported list of devices tested or not and mine was not which probably just means noone with my model has happened to report on it so maybe I'll be the first...

these were the last steps.  didn't work.  found USB scanner (vendor=0x123a [EXAMPLE SCANNER], product=0x2089 [Example Scanner]) at libusb:001:0032. We need to add those two values to the back end configuration file. Backend configuration files are located in /etc/sane.d/. Our example backend configuration file is /etc/sane.d/example.conf (make sure to replace example.conf with the name of your back end configuration file). You can edit that file as root using this command: 

 sudo gedit /etc/sane.d/example.conf3. Find the line that reads: 

 usband after it we need to add a line with the word "usb" followed by the vendor number and the product number we got with the scanimage -L command. That line should look like this: 

 usb 0x123a 0x2089

I found mine successfully and added them as simply as instructed above, but I didn't originally have a "usb" in my file, so I just typed it in. Figure the result should be no different.  unless someone tells me otherwise...  so onto the next guide down the list of google results...  :) ....

Inside synaptic I find two of these "cup" files I'm supposed to have at least one of

[IMG]http://img-cdn.filefactory.com/embed/xl/6j1lzp5qx1n1.png[/IMG]

As you can see only one is installed.  When I try to install the other I get this:

[IMG]http://img-cdn.filefactory.com/embed/xl/2754uw8nar0n.png[/IMG]

Don't know if this is my problem or not.  

Also, I get this with xsane

[IMG]http://img-cdn.filefactory.com/embed/xl/53maacs5aekh.png[/IMG]

And when I select the first one I get:
[IMG]http://img-cdn.filefactory.com/embed/xl/6uu7d8zp9z5x.png[/IMG]

And when I select the second one I get after hitting the scan button:

[IMG]http://img-cdn.filefactory.com/embed/xl/4vliisp3q7ev.png[/IMG]
where it just hangs.

So hopefully someone out there can make sense of this....

---

### Post by howefield on 2016-12-01
Please attach your images using the paper clip icon from the Reply to Thread posting window rahter than posting oversized images within the post.

---

### Post by juntjoo2 on 2016-12-01
sorry. is there a way you know people usually keep there images smaller, like a tool or method that would automate this? maybe a popular linux app you could recommend?

---

### Post by #&amp;thj^% on 2016-12-01
> **howefield said:**
> Please attach your images using the paper clip icon from the Reply to Thread posting window rahter than posting oversized images within the post.
+1:)
> **juntjoo2 said:**
> sorry. is there a way you know people usually keep there images smaller, like a tool or method that would automate this? maybe a popular linux app you could recommend?
As howefield suggests when making or replying to a thread...in the bottom right hand side you will see>> Advanced Options click that and now you will see at the top of the reply or new thread the Paper clip option.  Screenshot Included...Use that to Attach Photos and such.:)

---

### Post by juntjoo2 on 2016-12-01
thanks.  I thought he meant the regular link button. I got ya.  still doesn't really display the pic tho.  I'll look for a small app.  I'm sure there's something.

---

### Post by #&amp;thj^% on 2016-12-01
> **juntjoo2 said:**
> t still doesn't really display the pic tho.  I'll look for a small app.  I'm sure there's something.
Please clarify... You mean the picture won't show...you will have to hit the upload button also.

---

### Post by juntjoo2 on 2016-12-01
well it comes up as a little thumbnail, where it'd be easier to see them all without having to click each one, just smaller of course.  Small list of apps out there but found a couple that do batch resizing.  hey, if you happen to have any ideas about getting my scanner to scan please share...

---

### Post by #&amp;thj^% on 2016-12-01
Well lets see if you have the necessary software installed
```
 apt policy sane sane-utils libsane-extras xsane
```
Paste back the output here in code tags please.

---

### Post by juntjoo2 on 2016-12-01
Thanks

ben@Hal:~$ apt policy sane sane-utils libsane-extras xsane
sane:
  Installed: (none)
  Candidate: 1.0.14-11
  Version table:
     1.0.14-11 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
sane-utils:
  Installed: 1.0.25+git20150528-1ubuntu2
  Candidate: 1.0.25+git20150528-1ubuntu2
  Version table:
 *** 1.0.25+git20150528-1ubuntu2 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
        100 /var/lib/dpkg/status
libsane-extras:
  Installed: (none)
  Candidate: 1.0.22.3ubuntu1
  Version table:
     1.0.22.3ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
xsane:
  Installed: 0.999-3ubuntu1
  Candidate: 0.999-3ubuntu1
  Version table:
 *** 0.999-3ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        100 /var/lib/dpkg/status

 I see a couple "none"s.  hmm...

---

### Post by #&amp;thj^% on 2016-12-01
Ok...good eye and see your learning;)...in the terminal paste this:
```
sudo apt install sane sane-utils libsane-extras
```
one will show as already installed but that's ok
After all is installed.... in the same terminal:
```
gedit /etc/sane.d/dll.conf
```
Paste back the out put here also. I guess code tags is out of the question though.
See this for adding code tags:[https://ubuntuforums.org/showthread.php?p=12776168#post12776168](https://ubuntuforums.org/showthread.php?p=12776168#post12776168)
Thanks

---

### Post by juntjoo2 on 2016-12-01
Thanks. I appreciate your time. Learning?  Not much really. Just following instructions.  Picking up a piece here and there tho.  "out of the question", huh? 

```
# /etc/sane.d/dll.conf - Configuration file for the SANE dynamic backend loader#
# Backends can also be enabled by configuration snippets under
# /etc/sane.d/dll.d directory -- packages providing backends should drop
# a config file similar to dll.conf in this directory, named after the package.
#


# The next line enables the network backend; comment it out if you don't need
# to use a remote SANE scanner over the network - see sane-net(5) and saned(8)
net
abaton
agfafocus
apple
avision
artec
artec_eplus48u
as6e
bh
canon
canon630u
canon_dr
canon_pp
cardscan
coolscan
#coolscan2
coolscan3
#dc25
#dc210
#dc240
dell1600n_net
dmc
epjitsu
#epson
epson2
epsonds
fujitsu
#gphoto2
genesys
gt68xx
hp
hp3900
hpsj5s
hp3500
hp4200
hp5400
hp5590
hpljm1005
hs2p
ibm
kodak
kodakaio
kvs1025
kvs20xx
leo
lexmark
ma1509
magicolor
matsushita
microtek
microtek2
mustek
#mustek_pp
mustek_usb
mustek_usb2
nec
niash
#p5
pie
pixma
plustek
#plustek_pp
#pnm
qcam
ricoh
rts8891
s9036
sceptre
sharp
sm3600
sm3840
snapscan
sp15c
#st400
#stv680
tamarack
teco1
teco2
teco3
#test
u12
umax
#umax_pp
umax1220u
usb
usb 0x04a9 0x1753
v4l
xerox_mfp
```

the "usb" entries I put in there myself going off this guide

---

### Post by #&amp;thj^% on 2016-12-01
Your Welcome...just disregard my bad sense of humor (with the code tags).
Now what happens when you issue this in the terminal:
```
sane-find-scanner
``` 
Post back again the output here with code tags:P

---

### Post by juntjoo2 on 2016-12-01
```
ben@Hal:~$ sudo sane-find-scanner[sudo] password for ben: 


  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


found USB scanner (vendor=0x04a9 [Canon], product=0x1753 [MG4100 series]) at libusb:002:012
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
ben@Hal:~$ scanimage -L
device `pixma:MG4100_10.0.0.6' is a CANON Canon PIXMA MG4100 multi-function peripheral
device `pixma:04A91753_50728E' is a CANON Canon PIXMA MG4100 multi-function peripheral

```

there are those two different drivers or whatever they are.  do I need two?  check back to my image salad post.  remember those two cup files? what are they for and might my problem have something to do with not being able to install the one?

---

### Post by #&amp;thj^% on 2016-12-01
With "xsane" try using the second listed device:Canon Pixma MG41....[pixma:04A91753_50728E]
Sometimes depending on the image size it takes a bit a time to complete. And should now work with all the software needed...installed.
BTW those images were very hard for me to see and read FYI.

---

### Post by juntjoo2 on 2016-12-01
oh, ya think? I shall reboot my comp then.  ...hmm.. well I DID shrink their size to conform to forum standards. what can you do?  paper clip. brb...

no go.  thanks anyway.  so what do you think about these cup files of which only one installs correctly?  

```
  (Reading database ... 246072 files and directories currently installed.)Preparing to unpack .../cndrvcups-common-32_2.50-1-2~raring1_amd64.deb ...
Unpacking cndrvcups-common-32 (2.50-1-2~raring1) ...
dpkg: error processing archive /var/cache/apt/archives/cndrvcups-common-32_2.50-1-2~raring1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libc3pl.so.0', which is also in package cndrvcups-common:i386 2.50-1-2~raring1
Errors were encountered while processing:
 /var/cache/apt/archives/cndrvcups-common-32_2.50-1-2~raring1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

these are specifically for my device no? so if one won't install shouldn't that be the issue, or at least part of it?

---

### Post by #&amp;thj^% on 2016-12-02
I have to ask...why you would have raring packages installed when it is long past support?
Where did you read those packages were needed for your printer?
The first thing I recommend is to uninstall all the .debs from raring. (Unless you were specifically told to install those by a reliable source)
And I found this...might prove to be useful for you:
[http://tipsonubuntu.com/2016/08/14/canon-printer-driver-scangear-mp-ubuntu-16-04/](http://tipsonubuntu.com/2016/08/14/canon-printer-driver-scangear-mp-ubuntu-16-04/)

---

### Post by juntjoo2 on 2016-12-02
yeah, I linked to that thread inside this one. That's where I started.  Sorry, don't know the answers to your questions. That's just the level of my knowledge.  Not sure how to uninstall debs.  I'll worry about it when I get there.  I'm currently in the middle of a couple other threads dealing directly with that error message I've been getting with those cup drivers.  I'll report back once I'm done....


actually, I read it following the instructions from the link you provided, that these drivers are what I need. cup drivers.  [B]cndrvcups-common.  now i'm stuck with this font!  i mentioned it with one of those blurry pics too. 

found
 them through synaptic.

 [/B]could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)

this is the error I get which I'm working on to get those drivers installed right.

...

okay, what I'm finding is that this happens cos some file is locked that's needed for the raring to continue whatever that means.  

```
E: /var/cache/apt/archives/cndrvcups-common-32_2.50-1-2~raring1_amd64.deb: trying to overwrite '/usr/lib/libc3pl.so.0', which is also in package cndrvcups-common:i386 2.50-1-2~raring1
``` (was I supposed to put that within "[code]"?)

So this message on further inspection looks like maybe I should only be using one or the other but not both as perhaps they function for the same purpose.  idk.  I'm just trying things.  what else can I do? okay, maybe I'll abandon this error and ignore that file except it is strange that the two files come together under one installation package I guess.  Here:[ATTACH=CONFIG]272517[/ATTACH]

I'll try deleting these packages one by one, test, add them one by one while testing...

ben@Hal:~$ mv $HOME/.sane/xsane $HOME/.sane/xsane.bak

did the trick.  Snagged it from another thread but they didn't explain how or where they got it as no one answered their thread, they just closed it with this solution.  Did we clean something out? What's "mv"? It was in stackexchange where I have 1 rep point and you need 50(??) to post.  Weird and frustrating.  Anyway...

Now if only I could figure out in less time than it took me to get here how to set it up for wifi...

---

