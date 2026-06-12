---
title: "How do i find out what video card i have?"
date: 2007-03-14
forum: General Help
---

### Post by Atrio05 on 2007-03-14
ok i'm not rertarded or anything i know how to find it by opening the case and looking at it but it's an old computer with an old mother board in it with onboard video. i was wondering this because i can't seem to get anything above 640x480 for resolution. anything above that i start getting horizontal lines flickering on the screen. anyone know how to fix this or how to find out what driver i need to download to get it to work with at least 1024x768?

it work in 1024x768 in windows why not now in linux?

---

### Post by taurus on 2007-03-14
You can tell which onboard graphic card controller you have from the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
lspci
```

---

### Post by Atrio05 on 2007-03-15
ok i got this for my onboard video : Trident Microsystems CyberBlade/i1 (rev 6a) does anyone know if i need to get an updated driver for this so that i can get a res of at least 1024x768?

---

### Post by fragos on 2007-03-15
1024x768 should be available with the default "vesa" driver.  Did you try System-> Preferences-> Screen Resolution.  It should be there.  If not we'll go to the next step.

---

### Post by Atrio05 on 2007-03-15
i can get to it but i get these weird horizontal skipping type line thing's. kind of like static . they are not on there permanently they just show up for like a millisecond at a time. it's kinda hard to explain.

could it be that i don't have enough video memory to run a res of 1024x768?

how do i check that?

---

### Post by fragos on 2007-03-15
I don't know of any current video cards with les than 64MB which ought to be enough for 1024x768.  If its a mobo chip set instead of a separate card you can configure in the BIOS how much of your actual memory is allocated for video.  I don't know much about your video chip set.  If you've installed eye candy like Beryl you really need a more powerful video card like Nvida to get 3D rendering.  It takes a lot of CPU to create these effects and that could show up in the display on perhaps a random basis.

---

### Post by Atrio05 on 2007-03-16
well it's on board video and it's a pretty old computer, i think it's a pentium 3. i don't have anything like beryl installed on it just standard kubuntu.

i only get the horizontal lines when viewing resolutions above 800x600.

i don't think i ever had a problem with the video in windows 2000

i guess i can try looking in bios to see if i can fix it in there.

well if anyone has any other ideas on how to fix it so i get a res of 1024x768 that would be great!

---

### Post by Atrio05 on 2007-03-16
well does anyone know how to help me?

---

### Post by llamakc on 2007-03-16
I think we're waiting to hear what you changed in BIOS, if anything and whether or not that helped.

Next, post HERE the output of 

```

lspci

```

and then cut-n-paste the contents of your /etc/X11/xorg.conf file so we can see how you have it currently configured.

---

### Post by Atrio05 on 2007-03-16
ok well i will have to get back to you on that, because the computer is at my girlfriends house(it's her computer). so when i get to it agian i will post back every thing you asked for!

---

### Post by Atrio05 on 2007-03-17
ok problem fixed. i found the video settings in the bios. now it's all better! 

thanks for the help!!!

---

### Post by fragos on 2007-03-17
Just curious, do you remember what you changed?  How much memory was and now is allocated for video?

---

### Post by Atrio05 on 2007-03-18
i'm not sure exactly sure what it was i changed but i changed it from 64mb to 128mb. i think thats what did it. sorry i don't remember what i did exactly i just changed a few things real fast and tested to see if it worked and it did so i just left it at that.

thanx for all the help guys!

---

