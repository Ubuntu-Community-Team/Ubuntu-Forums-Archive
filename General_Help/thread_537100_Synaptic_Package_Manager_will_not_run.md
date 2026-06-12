---
title: "Synaptic Package Manager will not run"
date: 2007-08-28
forum: General Help
---

### Post by Mini Me on 2007-08-28
I have recently converted to Ubuntu and been trying to load Turbo Print to get my Canon MP170 printer working but have run into problems with Synaptic Package Manager....

I downloaded the Deb free version and tried to install the package - this failed due to an "exit source error 127"..I tried down loading it again and reinstalling it through various methods but was never able too succesful instal it due to the error

At this point whilist performing software updates I noticed the operation was completing the examining system step but then closing without giving me any updates... hence I opened up the synaptic package manager to preform updates this way - the manager displayed nothing in any of the fields so I hit reload at which point I got the following error message

"E: The package turboprint needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

This error is now displayed everytime I open the Synaptic Manager

If I hover over the software update icon a similliar error message it also displayed

At this point I tried to uninstall turbo print but of course this had never completed the installation due to the error and hence I could not get it to uninstall....

Eventually after more research I have download the tzg file of turbo print got it loaded and eventually managed to remove turboprint it...

However I'm still left with the error in Synaptec Package Manager as reported above

I've tried running "apt-get upgrade" from the terminal and get the following error message

"E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory"

Has anyone got any suggestions.....

---

### Post by wjr74 on 2007-08-28
Login as root, the try again

---

### Post by nitro_n2o on 2007-08-28
yeah.. you only need sudo before your command 
so it'll be ```
sudo apt-get update
```

---

### Post by gundumfx on 2007-08-28
well i would say is that to put this in terminal first 

sudo apt-get update

an yea i do agaree with nitro_n2o

---

### Post by Mini Me on 2007-08-29
Sorry I did not make it clear - in Terminal I entered "Sudo apt-get update" then entered my pass word then got the error

"E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory"

Any other ideas.....

---

### Post by Mini Me on 2007-08-30
ok tried the "sudo apt-get update" in the terminal again and this time it worked with no errors....

However clicking on the software update icon and the operation does not complete as per my original post 

And the synaptic pacage manager still shows nothing in any of the fields and upon reloading it now shoes the following error

"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

Press Close and it comes up with the following error on" your system"

"E: The package turboprint needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
E: Unable to lock the list directory"

Any ideas i'm considering updating to 7.04 to see if this corrects but this seems a bit desperate....

---

