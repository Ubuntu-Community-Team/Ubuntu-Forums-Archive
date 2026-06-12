---
title: "Autocad 2000"
date: 2007-08-13
forum: General Help
---

### Post by MichaelSM on 2007-08-13
Re Autocad 2000.

I ran my Autocad 2000 disc in Edgy tonight and completed install (except for VBA parameters) with wine. Everything looked perfect, and even with a Desktop AutoCad icon!

Using wine, the install ran (off-line of course) as perfectly as it ever has on a Windows box, and I must have done THAT plenty of times; I have the registration code stuck in my memory!

But I cannot start it. ...

I'm not sure what to do now....

Obviously wine did its job; the installation ran just like a Windows install, even asking for a restart, which I did, but it was awfully slow. Obviously a big think for edgy ...

OK. So I try to open the AutoCad icon, and I wouldn't expect a result. One of the options available is Scripts>Nautilus after a right-click. That opens a box which I don't understand.

Clearly, the massive program is SOMEWHERE ....

The only error during install was the VBA issue I mentioned, which, as far as I can tell, is just a file-swapper for web use. To be honest, I  just recently ran the AutoCad install on a spare Windows box off-line and that error didn't show up.

Any advice greatly appreciated. 

I hope any replies assist someone else in the same predicament.

Mike.

---

### Post by igknighted on 2007-08-13
There should be a folder in your home directory called "wine".  Go there and search around, wine should always install into this folder in your home directory.

---

### Post by MichaelSM on 2007-08-13
Thank you igknighted.
I'll swap back to my edgy box and see what's there.
Mike.

---

### Post by MichaelSM on 2007-08-13
Hi .

I couldn't find  the wine entry in my home folder you mentioned. However I tried this:

michael@michael-desktop:~$ sudo -i
Password:
root@michael-desktop:~# wine autocad
wine: creating configuration directory '/root/.wine'...
libGL warning: 3D driver claims to not support visual 0x42
libGL warning: 3D driver claims to not support visual 0x42
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
libGL warning: 3D driver claims to not support visual 0x42
Failed to open the service control manager.
fixme:ole:ITypeInfo_fnRelease destroy child objects
wine: '/root/.wine' created successfully.
wine: could not load L"c:\\windows\\system32\\autocad.exe": Module not found
root@michael-desktop:~# 

Any ideas?

Thanks for your time. Greatly appreciated.

Mike.

---

### Post by wirelessmonkey on 2007-08-13
I don't think autocad will run in wine, but, just for fun, what video card and drivers are you using?

---

### Post by MichaelSM on 2007-08-13
Er, um. No idea, Funny you should ask, I just have a basic Shuttle all-in-one  cheapo MB and the video is part of it. 
I've plugged in video cards and just get that baking plastic smell. 

Mike.

Re. AutoCad running in wine, Hmmm 99.9% there. Every re-install loses an error.

---

### Post by wirelessmonkey on 2007-08-13
Sadly, it doesn't look like anyone has been able to get AutoCad (Any version) to work. Nearly all have been able to complete the installation though....  
See [http://appdb.winehq.org/search.php?sSearchQuery=autocad](http://appdb.winehq.org/search.php?sSearchQuery=autocad)

You might have better results with crossover or cedega.

Good Luck

---

### Post by MichaelSM on 2007-08-15
I have been taking some time to follow this up. 

AutoCad2000 seems to be the only version which might work .

On 'starting it' with wine there are six .dlls which have to be copied to the wine windows system32 folder.

I can detect each of them on the acad cd, but can't figure out how to copy them to the folder required. 

I've made the necessary adjustments in winecfg libraries to run them as native windows dlls rather than builtins. 

But I can't get them there ....

Advice appreciated.

Thank you,
Mike.

I'll put this post in the gamers section, They are past masters at this dll copying but I can't find the details.

---

### Post by MichaelSM on 2007-08-16
Replying again to my own thread! 

Thanks to shadowalker's kind advices, I'm happily running AutoCad2000 with wine/Edgy. 

The only problem I have at this stage is organising floating toolbars, which isn't worth the effort for what I  do; mainly simple engineering drawings in 2D.

No doubt I'll work on that, but meantime to achieve snaps and dimensioning it's only one extra click to access these in the top panel. Trying to move the optional toolbars around the joint crashes the program. Big deal. I'm not a perfectionist to that extent.

My Brother USB printer is recognised, configurable, and able to print directly from acad screen.

Sometimes with my work it's nice to be able to import a digital photo of a job and use it as a working and printable background with overlaid dimensions. So far I haven't been able to do this re. importing photos from my home folder. That's the next cab off the rank....

All in all I'm pretty happy with what I've got. Delighted! in fact.

Thanks to assistance from all places.

Mike.

PS I haven't recently had a job which requires sending a DXF to a laser-cutter, for instance. I'll create one soon and see what happens.:)

---

### Post by wirelessmonkey on 2007-08-16
MichaelSM, 

Congratulations!  Hope everything continues to work well!

Would you be so kind as to post what you did to get things working, so everyone can benefit?

Thanks!

---

### Post by MichaelSM on 2007-08-17
No worries WirelessMonkey. I'll try to keep it short.

Ok, I have Edgy, wine 0.9.22 and AutoCad2000.Full. I don't know anything about any other combination. I actually have NO idea what I'm doing. 

Whack in cd and see what happens. No autorun occurs but a folder full of Windows files appears. Copy those cd contents somewhere for future reference,(eg.Desktop>Create Folder >My AutoCad) so  don't have to bother with the cd again.(This takes a while)

In that folder open SETUP.EXE with 'Wine Windows Emulator.' Wait .....then follow the prompts and install the 'Typical' program. (Trying to install 'Full' caused too many errors for me,,,) Click NO when asked about migration garbage.

Install completes (No VBA OK OK) Restart manually. 

New desktop icon! Autocad2000! (It won't work.)

Go back to cd file folder you've created and open it. Top file in left-hand corner is 'ACAD'. Open it and Edit>Select All>Copy. There's heaps of dlls and crap there.

Open  Home Folder and do Ctrl+h.(Thank you Shadow_Walker) This opens hidden files. Scroll down to .WINE and paste the ACAD files there. There may be a few repeat file notifications. I just replaced them.

At his stage I did another restart which probably wasn't necessary.

R/click AUTOCAD icon on Desktop and Open.

That's it, hopefully!

Mike.

NOTES.

OK. That's about as basic as I can make it. Naturally it took many hours to figure it out, so I've left out heaps of info, but the following may be important.

I mentioned in a previous post typing 'wine autocad' in terminal which was horrible.
At some stage later I interrogated the AUTOCAD icon and looked at its launcher command which is wine "C:\Program Files etc ......and copy>pasted that into terminal, which resulted in a list of at least six missing dlls which meant the program couldn't get off the ground. After finding out about accessing hidden files, I dutifully found each missing dll in 'ACAD' and copied it to .WINE. Next time I ran the launcher command there was another list of MORE missing dlls so I carefully selected and copied them to .WINE as well. Next launch in terminal, same result; more missing dlls. So I cracked the shits and pasted the whole 'ACAD' file into .WINE because in engineering: if at first you don't succeed, try a bigger hammer......

Also, there are possibly major issues with winecfg>libraries where one is supposed to be selective about which dlls wine runs- builtin or native- because overloading with native dlls can upset the apple-cart (that's how much I know about computerspeak) so it's probably my ham-fisted approach which has caused the floating toolbar glitch and probably others I haven't encountered ..... yet.

Hopefully someone who knows what they're doing might have a closer look at my rough-as-guts how-to and finesse it a little,,,,,,,, or a lot!

Cheers.

EXTRA NOTE !!!!!!!!!!!!.

Upon reflection and having re-read THIS earlier post, I might have achieved something important there after all as sudo. In other words one can't install a program on Ubuntu except as root, and I wouldn't have a clue if this applies to wine as well.  So have a read of it, especially the few bottom lines. It looks as if running the 'wine autocad' script in terminal as sudo enabled the install, and the line , 'wine: could not load L"c:\\windows\\system32\\autocad.exe": Module not found' maybe relates to the missing dlls. This is a big guess, and demonstrates my uncertainties with what's going on, but it might help if someone has tried my basic how-to and missed out.





michael@michael-desktop:~$ sudo -i
Password:
root@michael-desktop:~# wine autocad
wine: creating configuration directory '/root/.wine'...
libGL warning: 3D driver claims to not support visual 0x42
libGL warning: 3D driver claims to not support visual 0x42
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
libGL warning: 3D driver claims to not support visual 0x42
Failed to open the service control manager.
fixmele:ITypeInfo_fnRelease destroy child objects
wine: '/root/.wine' created successfully.
wine: could not load L"c:\\windows\\system32\\autocad.exe": Module not found
root@michael-desktop:~#

---

### Post by Michl on 2008-03-29
Just installed autocad 2000 in wine, ran it, copied some
drawings I did under windows, edited, and everything
ran smoothly ---except printing.  I can print from other
applications under wine, but can't print in autocad.  It
sees the printer, but I get a memory error.

---

