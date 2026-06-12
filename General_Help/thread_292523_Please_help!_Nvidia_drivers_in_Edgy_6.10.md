---
title: "Please help! Nvidia drivers in Edgy 6.10"
date: 2006-11-03
forum: General Help
---

### Post by Yes_It's_Me on 2006-11-03
Just my luck, just as I get ubuntu up and running PERFECTLY Something causes it to crash and burn.

I installed the nvidia drivers and beryl a week or so ago and all was well, I then installed kubuntu-desktop, Fluxbox and xubuntu-desktop, all was well. Until just now when I fire up my box and after the boot splash screen (before i log in) the screen goes completely blank, nothing happens. Now when i reboot and go to the recovery option at boot up and cp a backup of my old xorg (back when i had no nvidia drivers) back into X11 than start gdm it works!

I go to the xorg and in the device section it says "nv" for driver, if i change it to "nvidia", it stuffs up again! I have tried restoring to a complete original xorg, reinstalling beryl and the nvidia drivers and changing settings to no avail. I have also ran "sudo dpkg-reconfigure xserver-xorg" and made xorg from scratch but nothing works.

When i type "nvidia-settings" at the terminal i get the settings window correct but it only has one tab thingy ("nvidia-settings configuration") instead of the whole lot it used to have.

When i type "beryl-manager", it says:

"Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0"."

Please someone help me! I do not want to reinstall, i just finally got 5.1 sound working after months of trying.

Thanks in advance for any help whatsoever. any q's, just ask!

---

### Post by WinterWeaver on 2006-11-03
Grats with the 5.1 sound... could you sponsor me a link, as I still need to do this :P


as for your problem... I just sorted out a nvidia driver problem I was having... I followed this Howto:

[http://www.ubuntuforums.org/showthread.php?t=281823](http://www.ubuntuforums.org/showthread.php?t=281823)

as for the xgl and beryl -- I think this actually kills your normal opengl, and uses it's own. The reason I say this, is because, once this is installed, my opengl games do not work. not really sure why, never tried to debug it, just removed it.

my suggestion is, uninstall everything, xgl and beryl included.

once that is done, install nvidia again via the method in the link I just gave you. Then install xgl again. (I'm not sure if it's necessary to uninstall beryl, but that's what I think is best :P ... mebe someone with more experience can give a more informed answer)

hope this helps you. btw... the link I posted there is for Edgy as far as I know.

---

### Post by WinterWeaver on 2006-11-03
I should mention that I had the same problem with nvidia-settings, until I used that link ^.^ ... it sorted everything out :)

---

### Post by Yes_It's_Me on 2006-11-04
thanks for the help so far guys, i will give you a link to how i got my 5.1 working when i find it.

should i follow method 1 or 2? I have so far completely removed the nvidia stuff and beryl.

---

### Post by WinterWeaver on 2006-11-04
Personally, I used the script he created for Method 2, here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

and followed that whole page
it was stupidly easy :P

Edit: oh yeah... make sure to download and install the envy script, you want to have the stable version

follow every instruction on that page, and you should be fine. I followed it word for word and I'm happy... just make sure you have a active connection to the net, cause the script will connect to Nvidia's website, and download the drivers from there.

good luck!

---

### Post by Yes_It's_Me on 2006-11-04
tried it twice and nothing worked. :cry:

"sigh", i guess i will have to reformat and do it all over again.

here is what i did to get my sound working:

type: alsamixer at the terminal and turn everything way up. double click sound icon and go to preferences and turn on master,pcm,surround,surround jack mode,lfe,center,line in,line in capture,cd,microphone,iec958,iec958 playback ac97 (don't know what this one will be for you),iec958 playback source,pc speaker,channel mode,duplicate front.

type: gedit ~/.asoundrc

type: pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

into the new file

Than in kaffeine or whatever change the sound channels to 5.1

that did it for me, but the master only changes the front volume and lfe changes the rear.

here are some links:

[http://ubuntuforums.org/showthread.php?t=113145&page=2&highlight=x-530+logitech](http://ubuntuforums.org/showthread.php?t=113145&page=2&highlight=x-530+logitech)
[http://ubuntuforums.org/showthread.php?t=40883&highlight=x-530+logitech](http://ubuntuforums.org/showthread.php?t=40883&highlight=x-530+logitech)
[http://alsa.opensrc.org/FAQ028](http://alsa.opensrc.org/FAQ028)
[https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)
[http://www.ubuntuforums.org/showthread.php?t=184814&](http://www.ubuntuforums.org/showthread.php?t=184814&)

my speakers are the x-530's but it may work for you, hope it does!

"reinstalls ubuntu"

---

### Post by der_joachim on 2006-11-04
I hope I am not too late, (and OP is not reinstalling yet) but I too never got the drivers from the repos to run. What I did, was install the drivers from the Nvidia site itself. That worked flawlessly. 

There is a catch though: with every kernel upgrade you will have to recompile the driver.

---

### Post by Yes_It's_Me on 2006-11-04
you are not too late, i am still trying things. i will report back soon...

---

