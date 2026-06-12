---
title: "attempting to install beryl, and aiglx with nvidia beta drivers."
date: 2006-11-05
forum: General Help
---

### Post by noktekniq on 2006-11-05
so after browsing around yesterday and attempting many howto guides of installing this beryl and aixgl stuff. i realized that it wasn't that easy for new beginnings of linux even with windows backgorund knowledge. it was nothing close to windows. so i'm attempting one more time and i think i will be needing help on what i need to do. 

i'm going to be using [http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers](http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers) this link to follow the howto. 

i'm very confused on how this works in this step.
> Step 3-Install beta nvidia driver.
IMPORTANT - Read all of step 3 before shutdown down gdm.
First download the nvidia beta driver installer package from here.
Next do Ctrl+Alt+F1 to switch to a virtual terminal and log in.
Then do the following..


    sudo /etc/init.d/gdm stop
    cd directory_containing_NVIDIA-Linux-x86-1.0-9625-pkg1.run
    sudo sh ./NVIDIA-Linux-x86-1.0-9625-pkg1.run

    #When the installer asks you if you want it to configure xorg.conf for you, answer yes.
    #After the installer has finished

    sudo nano /etc/default/linux-restricted-modules-common

    #The last line of this file should read DISABLED_MODULES="", add nv to it to it reads-

    DISABLED_MODULES="nv"

    #This will make it so the xserver loads the nvidia module you compiled instead of the one that come with the restricted modules package,
    #this may not be necessary for you if you have uninstalled linux-restriced-modules package.. But do it anyways because it doesn't hurt
    #anything and keeps your system ready if you do ever install them!

    sudo shutdown -r now

    #Restart and if you did everything properly it should work!
    #If something went wrong you can use the xorg.conf backup the nvidia-xconf makes

    sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

can someone please explain this part? how would i go about doing this? or is there any better links to help me out? i'm desperate to find out

---

### Post by Dinerty on 2006-11-05
I used excatly the same guide and it worked a dream, the reason you have to log into the terminal and stop gdm is you need to install the driver which cannot be installed while your in gnome.

If you could print off the guide it would make it a lot  easier for you to remember

---

### Post by noktekniq on 2006-11-05
i was trying to do this 

sudo /etc/init.d/gdm stop
cd directory_containing_NVIDIA-Linux-x86-1.0-9625-pkg1.run
sudo sh ./NVIDIA-Linux-x86-1.0-9625-pkg1.run

do i type all that in at once? because the command dind't allow me to install the nvidia drivers. where do i save the file to when i downlaod the driver? someone give me some tips. thanks

---

### Post by noktekniq on 2006-11-05
ok i ended up following this thread [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)
from the beryl wiki. i did everythign word for word. 
so after completing everything. it seems like i have beryl, nvidia and emerald all installed. but when i restart it doesn't seem like i get a flash screen of beryl running, but the icon is on the top right near the clock. 

i tried using like the cube thing and it doesn't switch screen in any 3D mode. somone help me. THANKS

---

### Post by johnny9794 on 2006-11-05
ok click on the beryl icon and click Beryle settings Manager.
once that has popped up, on the left is Rotate Cube/Keyboard and in there everything should be set like this.

---

### Post by noktekniq on 2006-11-05
wait, on the left panel, if i have the item checked does it mean it is enabled? or is it when unchecked?

---

### Post by johnny9794 on 2006-11-05
lol if its checked then its enabled

---

### Post by noktekniq on 2006-11-05
haha sorry, i saw in ur pic it was not checked. so i kinda wondered.

---

### Post by noktekniq on 2006-11-06
still with no luck. beryl just locks up and freezes.

---

### Post by johnny9794 on 2006-11-06
> **noktekniq said:**
> haha sorry, i saw in ur pic it was not checked. so i kinda wondered.

Yeah sorry that was the theme i was using instead of a check type thing it was a push button, darker color meaning it was checked and light color means it was unchecked. lol

---

### Post by noktekniq on 2006-11-06
still not working. couldn't get a flash screen to load. so i uninstalled the whole ubuntu and reinstalled it again to try again. i ended up following the what was in the original post. uhm still in the process of installation. iono if it will work yet

---

### Post by johnny9794 on 2006-11-06
well i have one question man. Did you get the beta driver installed??? and installed correctly as instructed? you never did answer that. and plus you gotta have that beta driver installed for beryl to work, the regular nvidia driver will not work with beryl from what i heard and tried when i first played with beryl and could not get beryl to work at all when i had the normal nvidia driver.

---

### Post by noktekniq on 2006-11-06
with success i'm done because of the link below
[http://albertomilone.com/driver_edgyunstable.html](http://albertomilone.com/driver_edgyunstable.html)
and
[http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl](http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl)

i was able to make beryl work FINALLY

---

### Post by johnny9794 on 2006-11-06
Let me guess? Your problem was that you did or did not add repositories and if you did add them you did not add the repo keys?

---

### Post by noktekniq on 2006-11-07
i don't know. i added evrything that i was suppose to. but the driver that was in the first link above helped me get my thing working.

---

### Post by johnny9794 on 2006-11-07
yeah my bad man i kinda thought about the repo key becuase that dood that has the tut on the beryl and nvidia beta dirver does not have the repo keys for any of the repositores that you need to add to your resources list. so thats not your fault if it was not working because of the repository key. That tutorial " http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers"

SHOULD have a step saying you must add this or these repostiory keys 
xxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxx

blah blah blah uhwell good to hear ya got it working man :) sorry i could not help you get it working.

---

### Post by noktekniq on 2006-11-07
thanks dood. you helped me a lot.

---

