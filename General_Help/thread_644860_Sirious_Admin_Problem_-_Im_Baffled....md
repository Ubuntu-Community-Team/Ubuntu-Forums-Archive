---
title: "Sirious Admin Problem - Im Baffled..."
date: 2007-12-19
forum: General Help
---

### Post by RioCunliffe on 2007-12-19
im running Ubuntu 7.10 and I seem to have lost my admin capabilities,
I think this is due to me typing "sudo usermod -g admin rio" or somthing simmilar in terminal..

The thing is, now i am no longer an admin, i cannot do certain tasks (obvoiusly) this account is also the only one i have. Also whenenver i use a sudo command it seems to either ignore me or tell me i dont have permission...

What ive tried:

'sudo usermod -G admin rio' - it ignores me completely
'sudo su' - tells me i dont have permission
'su' - tells me i dont have permisson
ive also tired many other things and folowed varoius tutorials, but they all end up doing nothing...

Then, Just when i thought i could sort it!! :

I resorted to asking people on a Ubuntu IRC, and many told me to press esc at boot to enter the grub menu and then sort it out from recover mode, i thought it a good idea so i tried it only to find that when i boot it doesnt ask for me to press esc to enter grub menu. so i pressed esc at every avalable interval anyways, this resluted in doing nothing.

I then found a tutorial on the net saying that if such a thing happens then i should edit the grub config file to altomaticly boot into the grub menu, so i opened up the config file and edited it, HOWEVER, when i came to save the damn thing had the cheek to tell me that i didnt have permission to edit the file !!!

Please can someone help?? i need my admin capabiltys back fast...

Thanks,

Rio.

---

### Post by chewearn on 2007-12-19
You can boot using the ubuntu livecd, mount your harddrive and edit menu.lst there.

---

### Post by jken146 on 2007-12-19
You can boot into recovery mode, where you automatically become root.  There you can add yourself back to the admin group.

---

### Post by RioCunliffe on 2007-12-19
AstalaVista, Thank you so much!

i never thought of that!!

I will forever be in your debt.. :)

Cheers,

Rio.

---

