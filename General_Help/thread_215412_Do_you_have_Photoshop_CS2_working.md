---
title: "Do you have Photoshop CS2 working?"
date: 2006-07-13
forum: General Help
---

### Post by dyssident on 2006-07-13
Does any one have Photoshop CS2 working? If so, can you please, for the benefit of all of us who cant seem to get it going, post detailed instructions on what you did?

After several days of heavy googling ive come up with dozens of "i copied some files and registry keys and it worked" comments, but no actual instructions on what they did. Im starting to feel like Narcissus.

Ive tried copying the contents of c:\Program Files\Adobe, c:\Program Files\Common Files\Adobe, and c:\Program Files\Common Files\Adobe Systems Shared and the HKEY_LOCAL_MACHINE/software/adobe registry key as others have indicated. Photoshop starts but displays an error that is something like "your serial number, name or organization is invalid or missing" then quits. This is only informed speculation, but I presume that this is a problem caused by the license management included in CS2; among other things, it apparently relies on the Microsoft cryptographic system.

This evening I will try to create a symbolic link in "/home/USERNAME/.wine/drive_c/Program Files" that points to "/media/c/Program Files/Adobe". Ill copy the registry files by capturing the installed keys with Advanced Registry Tracer and RegShot in the hope that one of the captures will work. Ill report back on how it works.

---

### Post by slimdog360 on 2006-07-13
what are you using to run it? Ive heard that Crossover office works.

---

### Post by dyssident on 2006-07-13
> **slimdog360 said:**
> what are you using to run it?

Im trying to run it strictly with Wine. The word on the street is that it is possible; only the installer fails, hence the need to run it from or copy it from a Windows partition.

---

### Post by testube_babies on 2006-07-13
I was never successful.  The CS2 installer doesn't work in emulation and running CS2 from a Windows partition is incredibly difficult.  Somebody should write a good tutorial on how to do it.  I use version 6 in Crossover.  I hear 7 works too, but I didn't buy that version.

---

### Post by dyssident on 2006-07-14
> **testube_babies said:**
> 
running CS2 from a Windows partition is incredibly difficult.   


Ive tried a half dozen ways, and they all fail.

> **testube_babies said:**
> 
Somebody should write a good tutorial on how to do it. 


I am sort of amazed that no one has. When you consider how many people use Photoshop, they would be a hero.

> **testube_babies said:**
> 
I hear 7 works too, but I didn't buy that version.


Everything before CS2 is supposed to install and work more or less correctly. But I have not yet tried them, so I cant say for sure.

---

### Post by ericesque on 2006-07-14
bah! I got all excited when I saw this thread-- thinking maybe one of the 4 replies so far would actually say yes.  Oh well.  I think I'll download gimpshop and call that good for most simple projects.  

Come on people!  Help me get rid of my win partition! ;)

---

### Post by dyssident on 2006-07-14
> **ericesque said:**
> 
I think I'll download gimpshop and call that good for most simple projects.


Well Photoshop 7 definiately works, but never having used it, I cant say if its better than the current gimp.

> **ericesque said:**
> 
Come on people!  Help me get rid of my win partition! ;)


Im going to go through every concievable scenario until I figure out what others have done to get CS2 working. I think the Adobe issue is the only thing holding alot of people back.

---

### Post by dyssident on 2006-07-14
Below I have listed the test procedure I will soon be embarking on; please feel free to comment. Trials are arranged in order of increasing desperation.

**Assumptions**
- Windows partition is mounted at /media/c
- Wine is reinstalled before every trial
- A registry key install log has been taken with [RegShot](http://www.paraglidernc.com/6901.html) and is called regshot.pscs2.reg

**Trial 1**
- Import registry keys: `wine regedit.exe regshot.pscs2.reg`
- Copy installed directories
`cp "/media/c/Program Files/Adobe/Adobe Photoshop CS2" ".wine/drive_c/Program Files/Adobe"`
`cp "/media/c/Program Files/Common Files/Adobe" ".wine/drive_c/Program Files/Common Files"`
`cp "/media/c/Program Files/Common Files/Adobe Systems Shared" ".wine/drive_c/Program Files/Common Files"`
- `wine ".wine/drive_c/Program Files/Adobe/Adobe Photoshop CS2/Photoshop.exe" > trial1.log 2>&1`

**Trial 2**
- Create a wine drive to our former c: `ln -s /media/c ~/.wine/dosdevices/w:`
- Search and replace 'c:' with 'w:' in regshot.pscs2.reg
- Import registry keys: `wine regedit.exe regshot.pscs2.reg`
- `wine ".wine/dosdevices/w:/Program Files/Adobe/Adobe Photoshop CS2/Photoshop.exe" > trial2.log 2>&1`

**Trial 3**
- Import registry keys: `wine regedit.exe regshot.pscs2.reg`
- Link Photoshop directories
`ln -s "/media/c/Program Files/Adobe" ".wine/drive_c/Program Files"`
`ln -s "/media/c/Program Files/Common Files/Adobe" ".wine/drive_c/Program Files/Common Files"`
`ln -s "/media/c/Program Files/Common Files/Adobe Systems Shared" ".wine/drive_c/Program Files/Common Files"`
- `wine ".wine/drive_c/Program Files/Adobe/Adobe Photoshop CS2/Photoshop.exe" > trial3.log 2>&1`

**Trial 4**
- Import registry keys: `wine regedit.exe regshot.pscs2.reg`
- Replace wines drive_c with old windows c:
`mv .wine/drive_c .wine/drive_c.old`
`ln -s /media/c ~/.wine/drive_c`
- `wine ".wine/drive_c/Program Files/Adobe/Adobe Photoshop CS2/Photoshop.exe" > trial4.log 2>&1`

**Trial 5**
- Import registry keys: `wine regedit.exe regshot.pscs2.reg`
- Replace wines c: with old windows c:
`mv .wine/dosdevices/c: .wine/dosdevices/c:.old`
`ln -s /media/c ~/.wine/dosdevices/c:`
- `wine ".wine/dosdevices/c:/Program Files/Adobe/Adobe Photoshop CS2/Photoshop.exe" > trial5.log 2>&1`

---

### Post by cleentrax on 2006-07-14
This is the most important thread in the universe! I am in my Windows partition right now, so that I can use Dreamweaver 8 and Photoshop CS2, neither of which work properly in Wine for me right now.

---

### Post by dyssident on 2006-07-14
> **cleentrax said:**
> 
neither of which work properly in Wine for me right now.


Dreamweaver 8 allegedly works: [WineHQ AppDB]("http://appdb.winehq.org/appview.php?iVersionId=3482") and [tutorial]("http://bkcreation.info/Blog_Macromedia8OnWine.html")

The problem with installing Dreamweaver 8 sounds like the same problem with Photoshop: the stupid installer fails.

---

### Post by cleentrax on 2006-07-14
> **dyssident said:**
> Dreamweaver 8 allegedly works: [WineHQ AppDB]("http://appdb.winehq.org/appview.php?iVersionId=3482") and [tutorial]("http://bkcreation.info/Blog_Macromedia8OnWine.html")

The problem with installing Dreamweaver 8 sounds like the same problem with Photoshop: the stupid installer fails.

I have tried Dreamweaver 8 both by copying from another partition, and by installing. Neither works for me. Same with Photoshop CS2.

---

### Post by dyssident on 2006-07-15
Ive tried method 1 listed previously. Photoshop loads but fails with an error popup. "An error has been detected with a required application library and the product cannot continue. Please re-install the application."

The error is documented [here](http://www.adobe.com/support/techdocs/331419.html) but it doesnt fix anything.

Im convinced that the problem lies with Adobes new licensing system, Adobe LM Service. Im not sure exactly what the problem is though;' I would expect the "your system configuration has changed error" instead of the one im getting.

Either these people had a version of Photoshop CS2 without the license management like with volume licensing, or they were mistaken about which version they had.

---

### Post by Unknowndeepness on 2006-07-15
I have it up and working.

VMware is the shit ;)

---

### Post by dyssident on 2006-07-19
so after running through the trials i previously listed, im convinced that people that claim to have CS2 running under wine are either a) halucinating b) actually running <= CS1

the problem must be in the license management junk, but i have not a clue how to fix it.

maybe what is needed is a sizeable bounty for someone to fix the MSI installer thing under wine.

---

### Post by userundefine on 2006-07-20
I've seen one guy who has it working... he posts on Anandtech forums.  I'll try to alert him to this thread, maybe he can enlighten you all.

---

### Post by dyssident on 2006-07-20
> **userundefine said:**
> 
I'll try to alert him to this thread, maybe he can enlighten you all.


it would be greatly appreciated.

---

### Post by dyssident on 2006-07-20
ive just searched Anandtech forums for "photoshop linux" and "photoshop wine" and ive come up with one post

xtknight: "Yeah, I've run CS2 under wine in Linux fine after modifying a registry key (using wine regedit) regarding memory usage."

he didnt respond to subsequent requests for details. this is what has driven me nuts about this; ive seen about three dozen posts claiming to have PS working, but never a single detail. i swear, im starting to think its some kind of conspiracy.

---

### Post by userundefine on 2006-07-20
Yeah, xtknight, that's him.

---

### Post by dyssident on 2006-07-20
> **userundefine said:**
> Yeah, xtknight, that's him.

well if you can get him to give up some details,, i will erect a statue in you honor..

---

### Post by JoWilly on 2006-07-20
According to wine and crossover only Photoshop 7 works.

---

### Post by Onyros on 2006-07-20
Yup, Photoshop 7.0 works on WINE... but even that is far from flawless. Mainly GUI problems, but it's not stable enough for professional use.

The GIMP is an adequate replacement for everyday use, it just needs some time to get used to the different GUI, other than that, it's a fine replacement.

---

### Post by DragonTU84 on 2006-07-20
I got PS 7 to work flawlessly using Wine. I never upgraded to CS2, so I dunno if there is any way to install it via Wine. I will keep looking for you if anything else comes up. ;)

---

### Post by andy_cowman on 2006-07-20
I tried WINE and version 7 but the clone tool wouldnt work due to a conflict with the key you need to press!! However I suggest VMPlayer :D its  genius.

[IMG]http://i50.photobucket.com/albums/f338/andycowman/cs2.jpg[/IMG]

Combine this with a simple samba share (if anyone gets stuck I have the very simple config file for this that I wrote) to allow windows MyDocuments to be your home directory and you are away. The mouse moves seamlessly across and you can run it totally full screen aswell. 

I know some people refuse to use windows but to get CS2 to work at the moment its the best way I have found. Personnally I actually use the GIMP but my father likes CS2 at the moment although he is slowly learning to use GIMP.

Andy

---

### Post by dyssident on 2006-07-20
> **andy_cowman said:**
> However I suggest VMPlayer :D its  genius.


thats fantastic. ive never really used vmware/vmplayer but maybe its time. 

what did you use to create the image? VMWare or a free alternative?

---

### Post by Epperly on 2006-07-21
Ha, someone really should get Photoshop working on Linux, because, well... GIMP sucks (IMO).

---

### Post by dyssident on 2006-07-21
> **Epperly said:**
> GIMP sucks (IMO).

i was wondering how long it would take for this to turn into a "gimp sucks" thread. ](*,) 

the shame of it is, its really on the installer thats broken.

---

### Post by Epperly on 2006-07-21
well, it's not that it sucks... I'm sure once somebody learns it they can be just as good with it as any other digital enhancement software... I just mean it sucks in terms of it's hard to use at first and I'm too lazy to learn to use it.

---

### Post by userundefine on 2006-07-21
Funny, I remember how hard Photoshop was to learn when I started...

---

### Post by Epperly on 2006-07-21
Ok, me too

---

### Post by andy_cowman on 2006-07-21
I used a free alternative, if you search the forums there was a good start up guide but basically create and ISO image of either XP or 2000. 

You need to use Qemu (either windows version through WINE or the latest linux release will do) to create your virtual drive. You need make a config file called (for XP)

WindowsXPPro.vmx 

mine has the following content

#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "WindowsXPPro.vmdk"
memsize = "512"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "WindowsXPPro.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
ethernet0.present = "TRUE"
floppy0.present = "FALSE"
usb.present = "TRUE"
sound.present = "FALSE"
sound.virtualDev = "es1371"
displayName = "Windows XP Pro"
guestOS = "winxppro"
nvram = " WindowsXPPro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 62 b4 39 29 23 cc-f0 57 0e ee 6f 01 20 92"
uuid.bios = "56 4d 62 b4 39 29 23 cc-f0 57 0e ee 6f 01 20 92"
ethernet0.generatedAddress = "00:0c:29:01:20:92"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = "WindowsXPPro.vmss"
tools.remindInstall = "FALSE"

usb.autoConnect.device0 = ""



then you install VMPlayer which is a free download and load the file. You then can run the windows installation process and away you go. You need a decent amount of space for this (I allocated somewhere around 10gb) and also I recommend 1gb of RAM that means you can have 512mb per OS. 

You then need the VMWare Tools which you can get hold of. If you struggle to find it I think I have the little ISO somewhere. Then you can have decent graphics and move the mouse between linux and windows seamlessly

While I think about it turn off all the garbage theme stuff in XP! Makes a speed differnce, and some people had a real problem with speed but thats apparently a common fault. There was something on another post about it recently. Its worth a try!


I really like the GIMP, I use that and find it very easy. It also impresses me no end that its free!

Andy

---

### Post by dyssident on 2006-07-28
some relatively good news.. it looks like a fix for the MSI installer is slated for WINE 1.0.. 

[See the bug report here..]("http://bugs.winehq.org/show_bug.cgi?id=5348")

anyone that has error logging or details is encouraged to contribute them..

---

