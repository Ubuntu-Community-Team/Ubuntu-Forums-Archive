---
title: "Burning .CUE and .BIN"
date: 2005-06-28
forum: General Help
---

### Post by danf_1979 on 2005-06-28
How can I burn the .cue format? What program can I use?? I'm a complete newbie  :| 
Thanks everyone...

---

### Post by sonny on 2005-06-28
Install GnomeBaker, that should do.
> Code:
$sudo apt-get install gnomebaker
If you're having problems, search in the repositories for some program to conver cue bin to iso, you can use synaptics or in a console.
> Code:
$apt-cache search bin iso
I'm not in Linux right now, so I cannot tell you wich programs are shown, but you get the idea.

---

### Post by domo on 2005-08-03
I did it in a other way: transform the bin/cue into a iso file

#sudo apt-get install bchunk
#bchunk image.bin image.cue image.iso

You just have to burn the iso as normal after that

---

### Post by lol on 2005-08-04
you should use k3b, it can burn CUE/BIN directly and is much better than any gnome CD burner...

---

### Post by troughton on 2005-10-28
i am a ubuntu newbie but uesed to computers and difrent os i have been reading the web forums and ubuntu forums for 3 days now on how to burn an .bin .cue file
you state that gnoem baker and k3b dose will burn them for me but having wasted sevrel dvd's on this i now have some nice cup mats but no film as both programs will only burn them as data files and not as a playable dvd and having check both websights and help files they dont even tell you how to burn unless alerady and iso 
i downloaded and installed bchunk and after a long time desyfering there help files i managed to get it to burn the bin and cue to iso but it has created 2 iso,s instead of one and when i burn them it wont put the film on the disk i dont need any more cup mats at the moment so can some one please explane step by step how to burn a .bin and .cue into a playable dvd

---

### Post by ored on 2005-11-21
I use cdrdao in terminal to burn cue/bin cd images, the command is:

sudo cdrdao write --device /dev/hdc --driver generic-mmc-raw --eject video.cue

Note that you have to install cdrdao in your system:
sudo apt-get install cdrdao

;)

---

### Post by JoBangles on 2007-04-15
I liked the simplicity
 but my 800mb .bin file turned into an 39mb iso?

---

