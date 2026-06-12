---
title: "Weirdest problem ever! Keyboard stops out of the blue."
date: 2008-03-05
forum: General Help
---

### Post by daizumi on 2008-03-05
Hey people,

This is the weirdest problem ever.

I was typing in gutsu openoffice, and all of a sudden my keyboard became unresponsive. I had to bash it really hard to get some typing out of it, so it was still working, but veeeerry unresponsive.

At first I thought maybe my laptop's keyboard had gone bad, but then when I logged out of gnome, inputting name and password was no problem! What's more, rebooting in windows and I could just work normally. 

Then I waited for a while, worked in windows, and went back to gnome, but keyboard still unresponsive!

How can this happen, especially all of a sudden like that, and is there anyone with a suggestion what I could do?

Regards,

Daniel

---

### Post by dthomas08 on 2008-03-05
I, too, have this problem. Using programs such as OpenOffice, Firefox, or Matlab and all of a sudden the keyboard becomes unresponsive. It only shuts off in those programs, and I have only seen it happen in one program at a time. The only way to fix it that I have found is by closing all instances of that program and restarting it. 

It is actually really annoying because I once lost an entire Word Document because I couldn't type in the name of the file I wanted to save it as. Sometimes (keyword 'sometimes') I can type it into a text editor and then drag text in, but that isn't quite a fix.

Please somebody help us fix this, I have been living with this problem for months now.

I have a Dell laptop. Could this have anything to do with the problem as it has caused problems in the past? Oh and I also have Gutsy as daizumi does, despite the fact that the forum seems to think I have Feisty ...

---

### Post by jeremyk on 2008-03-05
A friend of mine has the same problem. His keyboard just stopped working at all. He can just log in, but then what ever application he opens, he cannot write anything. He also tried to log in in safe mode but this did not help.

As for a logging in root terminal, he did it and tried to reconfigure xorg with this method, but it did not help. 

So please, is there some someone to help? This is a very very big problem. 

Thanks!

---

### Post by daizumi on 2008-03-05
The problem is that my keyboard is unresponsive now in every program, but only in Ubuntu. And it came suddenly once, but now it has been like this for days. I have know idea what might cause this, since it doesn't seem related to any program.

---

### Post by mlfrancis on 2008-03-05
Old thread, but going to post anyway.  My keyboard totally stops working right after the Nvidia splash screen before KDM login.  What I have found is if I keep pressing capslock on, off, on, off... etc from before the Nvidia init until the login screen is shown, then my keyboard will work fine from then on.  

Still searching for a solution.

---

### Post by jeremyk on 2008-03-06
Does anyone have a solution? This is a very serious and critical problem. Please. Thanks.

---

### Post by dthomas08 on 2008-03-06
Ah, I was wondering if people ever have trouble typing in the names of files when renaming or creating new files. Sometimes I need to go into into the terminal just to use mv or mkdir just for this purpose. This is awful

---

### Post by deepclutch on 2008-03-06
isnt it due to bad keyboard map?u may have to select generic-104 kbd as it works for most ps/2 kbds.
do it by booting with "rw init=/bin/bash" line in kernel line of grub removing "quiet,splash ro" options(press "e" to edit" ).then do a "sudo dpkg-reconfigure xserver-xorg" may be set debconf to "medium" via "sudo dpkg-reconfigure debconf"

---

### Post by mlfrancis on 2008-03-06
What I found after a lot of forum and Google searches is it has something to do with the "Legacy USB" support in the BIOS settings of some machines.  This is called something different from machine to machine and may not even be there.

What I read is the problem has something to do with the BIOS reporting the support of a USB keyboard and Ubuntu trying to use it instead of the PS/2 keyboard.

The way I had mine set up was a PS/2 keyboard and USB mouse.  I turned off the "USB Keyboard" support in my BIOS but didn't find anything that talked about "Legacy USB".  That still didn't fix my problem.

So, I swapped out a temporary USB keyboard and all was well again.  

What I ended up doing in the end was using my PS/2 keyboard and using a different PS/2 mouse instead of the USB mouse.  Now all is well and good again.

BTW, No, my keyboard and mouseisn't going out as they works fine in Windows, the BIOS, Grub but stops responding just after the start of the video init for kdm.  Oh, and the mouse continued to work well into the kdm login session.

Hope that helps someone.

---

### Post by mlfrancis on 2008-03-06
Oh, and in my first post when I said this was an old thread.... well, I was a doof... I was looking at the Join Date of the original poster.  LOL

---

### Post by jeremyk on 2008-03-06
Concerning my friend's problem, it turned out that it has turned out the keyboard accessibility option (and enabled slow keys) incidentally. This made his keyboard working very very slowly, but there was not an actual problem. 

Maybe others would check this point too (System->preferences->universal access->keyboard accessibility). 

Good luck for all, because I thing this is really a bad problem.

---

### Post by deepclutch on 2008-03-06
I have searched whole Ubuntu forum and other sources.but there are random problems listed for the system freeze including keyboard not working!
Is there any help that any Ubuntu (kernel) developer can provide us?
That will be great :)

---

### Post by sports fan Matt on 2008-03-06
Also you can try this as well (worked for me)  In System>Preferences>Keyboard Under "layouts" the 1st option is Keyboard Model:  Note: you will have a ton on choices depending on computer Keyboard Model and in my case PC maker and tick "Choose" ..In my case Mine is a HP..Try that, see if it works and report back..Thanks

---

### Post by dthomas08 on 2008-03-06
wow, that did the trick. I changed the layout to "Dell Latitude Series"

I just can't believe I didn't check that a long time ago.

Thanks a lot

---

### Post by daizumi on 2008-03-07
Changing the 'keyboard accessibility option' did it for me! Thanks a lot guys.

---

### Post by Adman on 2008-03-29
Hi guys

I'm having this problem, particularly in Matlab - keyboard just "switches off"!  Highly frustrating.

I can't find my keyboard layout in the keyboard system options.  The keyboard is the Logitech MX5000 Bluetooth...  I've tried the ones which appear similar - but the problem still persists!

Please help !! :(

---

