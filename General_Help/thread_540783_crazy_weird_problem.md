---
title: "crazy weird problem"
date: 2007-09-02
forum: General Help
---

### Post by danip on 2007-09-02
Well I dont know where this should go so feel free to move it if its not here.  I booted my computer up and to start it off there was this white bar across the boot screen.  Second it was way way slower than usual.  I got to the log in screen, log in and the log in load bar sort of appears but the log in screen doesnt really go away.  Once it finally logs in though when i open up programs only the border of the window appears.  Things are really choppy when i try to minimize it again.  I basically cant get access to anything on the computer.  I would imagine something got messed up with xorg somehow.  I would think I would then have to boot up into text mode and fix somethings there.  But as of right now ive forgotten how to do all those things.  If I have to reinstall ubuntu and you tell me how i can get my home folder backed up under console mode? Any help is much needed, am on a barrowed computer right now, sorry if I havent explained the problem very well..its a little hard but, ill try to answer any questions to make it clearer.

---

### Post by psmar on 2007-09-02
"dpkg-reconfigure xserver-xorg " would  be  used in the command line to reset your xorg settings
hope this helps

---

### Post by danip on 2007-09-02
well that seems to have done the trick it looks like. thanks for the reply.  it still starts up pretty slow but its back to being usable.  When running through that program i didnt know really what i was doing so i just hit ok for most everything...hope that wont cause anyharm.  I figured since I didnt have to do that on the install I was running on the defaults before hand anyways.

---

### Post by danip on 2007-09-02
one more problem ive noticed since i ran the x configuration.  my moniter seems to always be flashing.  its very slight but you can see it and it kind of gets to you.  i thought maybe the refresh rate needed to be upped but i went to go change that and there was only one option 61hz.  perhaps my moniter is starting to go out but im not sure.  its an lcd on a laptop.  anything else it could be?  anything anyone would recomend i change in the xorg file and if so how would i got about doing it?

---

### Post by banewman on 2007-09-02
Are you running beryl or compiz?

---

### Post by danip on 2007-09-02
no not running anything of the sort.  i had beryl installed at one time bu it didnt work to well

---

### Post by banewman on 2007-09-02
My first reaction is to suggest you look for a more appropriate driver for your video card. maybe the choice you made in sudo dpkg-reconfigure xserver-xorg was not the best choice - or the correct driver was never installed to begin with. It seems like a good starting point.

---

### Post by danip on 2007-09-03
Ok so i am running xserver-xorg so that i can edit my xorg file more comfortably.  for my video card it says its generic and its running a vesa driver.  id like to change it to something else to see if it works better to get rid of this flashyness.  my laptop is running some sort of 32bit onboard graphics by intel.  does anybody know what kind of appropriate driver would be to pick for that.  i dont have a choice of intel under it. the chocies it lists are:

ati, cirrus, cyrix, fbodev, fglrx, i810, mga, na, nvidia, raedon, s3, savage, sis, trident, tseng, vesa, vga, voodoo.

if vesa is the correct choice for the driver, are there any other suggestions of what to do to get rid of the screen flashing?

---

### Post by psmar on 2007-09-04
vesa is sort  of a generic driver.  What you might look at is the refresh rates  as that can leave some quick flickering on the screen, I might suggest that you research for the specs on your laptop on there Website, (there is usually some sort of spec sheet for each model) or theres good old google     :biggrin:
Good luck

---

### Post by danip on 2007-09-05
well i finally got around to fixing it. not sure what the problem was but i re did xorg and its working beautifully now!

---

