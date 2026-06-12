---
title: "[SOLVED] Installing Uplink with Wine..."
date: 2008-06-03
forum: General Help
---

### Post by paraplegicpanda on 2008-06-03
I'm not 100% sure this is the right place to post this, but the front page says the gaming forums aren't related to the support forums.

So I have my old Uplink: Hacker Elite disc and I'm trying to install it in Wine. I tried the trial software on the Introversion website and it installed without a hitch, but after I uninstalled it and tried to install the full version of the game, I got this error:
```
paraplegicpanda@hacktopix:~/foo$ wine SETUP.EXE
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:load_winedos Could not load winedos.dll, DOS subsystem unavailable
winevdm: unable to exec '--app-name': 16-bit support missing

```

Any ideas?

---

### Post by EXCiD3 on 2008-06-03
Why dont you install the native linux version of uplink? Installer should be on the cd, and you can get the patch here: [http://www.introversion.co.uk/uplink/otherfiles.html](http://www.introversion.co.uk/uplink/otherfiles.html)

---

### Post by paraplegicpanda on 2008-06-03
Okay, I tried installing the linux version... the readme says:

> LINUX

Simply extract the compressed file into a directory and run. 

You may need to set the attributes of the uplink executable to make it

runnable.

So I extracted the files to a folder on my desktop called Uplink. I also went into the properties of the file and under the Permissions tab I checked the box that says "Allow executing file as a program." At first I tried just double-clicking the file, but no go. I attempted going into a terminal, changing to the Uplink directory and typing "uplink" (the name of the program file):
```
paraplegicpanda@hacktopix:~/Desktop/Uplink$ uplink
bash: uplink: command not found

```
I also tried typing "./uplink":
```
paraplegicpanda@hacktopix:~/Desktop/Uplink$ ./uplink
./uplink: symbol lookup error: ./uplink: undefined symbol: __glutRoot

```

I'm not quite sure how to run it...

---

### Post by EXCiD3 on 2008-06-04
Ah, looks like theres a problem with it and it needs patching. Just use this tut to install with: [http://ubuntuforums.org/showpost.php?p=3396009&postcount=23](http://ubuntuforums.org/showpost.php?p=3396009&postcount=23) And if you're running 64bit by chance you will probably want to check out this: [http://whynotwiki.com/GNU/Linux_/_Running_32-bit_applications_on_64-bit_Linux](http://whynotwiki.com/GNU/Linux_/_Running_32-bit_applications_on_64-bit_Linux)

---

### Post by paraplegicpanda on 2008-06-04
Thanks a lot EXCiD3. The problem was that I was trying to install it on a 64 bit installation. I followed the link to the wiki article and it fixed all of my woes. Now I am running patch version 1.55 happily, minus my audio problem. Regardless of what audio settings I change Uplink completely takes over my audio and I cannot adjust any of my audio settings. I have shut off the music, but the beeping and such are still rather annoying blaring at full volume. I have been searching online for resources but I haven't found anything about this problem. If anybody knows how I can either block Uplink from accessing any of my audio devices or just shut off the sound in Uplink, I would really appreciate it.

---

### Post by EXCiD3 on 2008-06-04
Glad you got it working. I sure miss playing that game, i need to find my copy and start playing it again! Every introversion game is just downright incredible. Darwinia is soooo much fun.

Not sure about the sound problem...try posting on the uplink forums: [http://forums.introversion.co.uk/uplink/](http://forums.introversion.co.uk/uplink/)

Since your problem is pretty much solved dont forget to mark your thread [SOLVED] in forum tools :) I'll let you know if i find anything on the sound problem. Could have something to do with the adoptation of pulseaudio but i bet its more of a problem with Uplink...I'm sure you arent the only one with the problem so theres probably a fix somewhere out there, haha.

---

### Post by paraplegicpanda on 2008-06-05
Thanks a lot! Now that I have got Uplink, I'm definitely going to have to look into Darwinia and Defcon...

---

### Post by EXCiD3 on 2008-06-05
Darwinia is incredible, a guy creates a race of digital people that get taken by viruses ;) and so is Defcon...try playing a regular speed Defcon game with some friends...so much fun but it takes HOURS!! :D

---

