---
title: "mouse button problem"
date: 2007-10-24
forum: General Help
---

### Post by jimod4 on 2007-10-24
I have just installed 7.10 from the alt image.  i am having a problem whre my mouse will not allow me to click on certain items.  I cant click on anything on the desktop.  I can't click on the "home folder" or "computer" selections on the menu bar.  I can select all of my applications and can use firefox without an issue.  It seems to me to be a problem with nautilius.  If i type nautilus at the command line it hangs for a minute and then returns without launching.  My computer is an ASUS P5L-VM1394 motherboard(intel 945 chipset).  I have a microsoft PS/2 wheel mouse and a nvidia 7300LE video card.  I was having the problem with the standard video driver and then I installed the restricted video driver.  I have the problem  with desktop effects enabled or disabled.  here is a piece of my xorg.conf file.

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"    
    Option        "Emulate3Buttons"    "true"
EndSection

I would consider myself fairly knowledgeable with Linux,  but this has me baffled.  I have seen other posters talk about similar problems, but theirs were intermittent and and mine is all the time.  Any help would be appreciated.

---

### Post by DagMan on 2007-10-24
The thing with nautilus taking a long time makes it sound like it, or something it depends on, is more the culprit than anything.  Nautilus draws the desktop as well as being the file browser.  Have you tried reinstalling nautilus?

---

### Post by jimod4 on 2007-11-06
I played around with reloading and reconfiguring nautilus and xwindows.  I fooled with the drivers for the video card without luck.  Then I created another user and logged in as that user and everything is fine.  i guess the gnome config somehow got corrupt on the original user.  then I edited the /etc/group file so my new user has the same group membership as the user the ubuntu setup created.  If you don;t do that you can;t use sudo or access things like the floppy and the sound card.

---

