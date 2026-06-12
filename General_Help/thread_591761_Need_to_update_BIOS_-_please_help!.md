---
title: "Need to update BIOS - please help!"
date: 2007-10-25
forum: General Help
---

### Post by the badger on 2007-10-25
Hi!

I seem to need to update my BIOS. If I grabbed the right line in the terminal, then my mobo is ASUS A7N8X-X ACPI BIOS Rev 1006. 

Why do I want to update my BIOS? I've got an older 'puter and been getting error 18 in grub everytime i boot up for about a month now. i am able to launch ubuntu (i only have ubuntu 6.06) by choosing a slightly earlier kernel version. i'm wary about uninstalling the latest kernel version because it looks like synaptic wants to grab a lot of other kernel stuff along with it...scary. i'd like to upgrade to (or, all else failing, re-install with) gutsy. seems like updating the BIOS would be better to do before attempting upgrade. 

so...I can only find a windows program for updating an ASUS BIOS. Please help!

many thanks.

---

### Post by drs305 on 2007-10-25
I am not sure why you need windows. Backup your BIOS. Download the latest version from ASUS (I tried checking for you but don't know the type of socket you have). I am pretty sure that if you can put it on a floppy, CD or DVD you will be able to initiate a BIOS update  during boot up. The ASUS site or a google search should provide the details. 

I don't want to get into specifics since dealing with BIOS issues is beyond my comfort zone. But you shouldn't need windows as long as you can get a copy of the BIOS onto some sort of media.

ASUS BIOS Updates: [http://support.asus.com/download/download.aspx](http://support.asus.com/download/download.aspx)
That page has a menu for downloading the latest BIOS and there is also a link on how to update BIOS.

I looked at the instructions for your mobo. The first part discusses making a bootable floppy with DOS, but this is for first time users. Look at the second section (Use Built-In BIOS Refresh Procedure) in which you only need the BIOS on media and don't need to use DOS or windows.

---

### Post by the badger on 2007-10-25
drs305 - thanks for that! i guess i wasn't searching for the right page(s)...

so if you or anyone else can help me find a solution to the step I am now stuck at, that too would be fabulous.

I have downloaded and unzipped the update info for my mobo from support.asus.com - it is a bin file. i've copied onto cd and managed to navigate my way to POST during start up. it asks me to "insert disk" but seems to only consult the floppy drive for a disk. i have no floppies. i don't think i can easily obtain one where i live.

any ideas on how i can get the POST to check my dvd drive for the disk it is seeking?

thanks :)

oh - i should maybe add that the dvd drive in question *is* set to be first in the boot-up sequence (such as, live cd boots from here first).

---

### Post by sultanoswing on 2007-10-26
The other annoying problem these days is that many people don't even have a floppy drive anymore (myself included). The more 'normal' way to BIOS update these days is via windows based utilities, which is incredibly annoying when it's mandatory as above.

Having said that - a solution I have used is this: 

Download a FreeDOS (or similar) bootable ISO, then put the BIOS file and awdflash.exe or whatever on a second CD and boot from the CD drive, swap the discs, and flash away sans windows and sans floppy!

---

### Post by drs305 on 2007-10-26
badger,

I've spent about half an hour looking for a solution. I am usually pretty good with google but I'm having limited success. I came across several mentions of making a bootable CD but with the number of computers without floppies I expected hundreds of hits.

If what sultanoswing's post isn't enough, I'd go directly to the ASUS forum and post the question there. You might have to register to post a question but that should be worth the effort. I don't know how often their tech people look at each forum, but the forum for your particular mobo is:

[http://vip.asus.com/forum/topic.aspx?board_id=1&model=A7N8X-X&SLanguage=en-us](http://vip.asus.com/forum/topic.aspx?board_id=1&model=A7N8X-X&SLanguage=en-us)

I did find a site with a link "Need to Flash Your BIOS On a PC With No 1.44"  It wasn't the most professional looking site but here it is:
[http://www.bootdisk.com/](http://www.bootdisk.com/)
Personally I'd wait to see if one of the 'VIPs' on the ASUS forum answers you.

When searching for stuff on the ASUS site: on the drop down menus you would put: motherboard, SocketA(462), A7N8X-X.

If you have success, please let us know. I have two computers without floppies  :-)
Good luck.

---

### Post by drs305 on 2007-10-26
badger,

I've sent you a PM regarding ASUS's EZ Flash 2 utility.

For other forum users interested in this subject, ASUS's newer boards allow you to update the BIOS without windows or a floppy. 

I didn't want this thread to turn into a non-ubuntu topic but thought readers should know that windows isn't the only solution!

---

