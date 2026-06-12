---
title: "Add/remove programs not staying active!  PLEASE HELP ME!!"
date: 2008-01-07
forum: General Help
---

### Post by iamkidd on 2008-01-07
I did a search of the forums and came up with nothing so I guess this would be the next step…  I am running a computer with Windows XP and Ubuntu 7.10.  I’m not sure when it started, but I discovered recently that I’m having trouble with the installing/removing applications program. When I click on it for it to run, it will bring up the program, scan through the dependencies, and then close down!  I can’t, for the life of me, figure out why it keeps doing this!  The OS also does the same thing for the “update OS” application, as well as for all of the “package managers” there are installed.  I am a newer Unbuntu and Linux user, so maybe it’s something really easy that I missed.  Will someone please tell me how to fix this?  I’m sick of stressing out over this!  Please HELP ME!!!  Thank you everyone for your time and answers!  -J. Kidd

---

### Post by njparton on 2008-01-07
Does it ask you for the root password first when you open Synaptic?

---

### Post by p_quarles on 2008-01-07
You'll get more helpful error output if you run the update through the command line package manager. Try the following, and post the error output here:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by iamkidd on 2008-01-07
I tried the command line route… however it does the same thing.  It will do that little scan before the program appears on the screen, then the programs/application will just shut itself down.

---

### Post by p_quarles on 2008-01-07
Yeah, I understand that. What I'm requesting is an actual verbatim copy of the output of the command.

---

### Post by iamkidd on 2008-01-07
The output is this... 

[sudo] password for iamkidd:


Which would make sense to put in my password at this time, however, when i try to do that it won't let me type my password in the space, nor will it even all me to cut and paste it.

What next?

---

### Post by p_quarles on 2008-01-07
Type your password when it asks, and then press enter. Your password doesn't show up on the screen, but it's still being entered.

---

### Post by iamkidd on 2008-01-08
I entered my password, then hit enter.  It started doing its checks and stuff, and said there was X amount of upgrades, press y or no to continue.  I followed the whole upgrade process through until the end.  Then I rebooted it and everything works again!  WOO HOO!!
Thank you so much for you guys helping me!!  I guess the question that I have next is WHY did it do that in the first place?  Not that it’s a big deal knowing, but it would be nice to know so I can take care of it if it happens again.  Once again, thanks guys!!

---

### Post by sancho panza on 2008-01-08
Great to hear that you fixed the problem...Please mark this thread as Solved using the menu.

---

