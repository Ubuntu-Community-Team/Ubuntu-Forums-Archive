---
title: "2 Computers (1 Going Back To Vista)"
date: 2008-02-20
forum: General Help
---

### Post by ToaStOmGi on 2008-02-20
Alright well i have Ubuntu installed on both of my computers. But i decided i wanted to have Vista back on 1 of them and keep Ubuntu on the other. So i tryed to install Vista back onto my computer and it says my drivers arnt in the right format? Says it ahs to be in the format of NTFS. So im guessing it changed when i switched to Ubuntu? Idk, i need some help tog et those back to the right format.

---

### Post by overdrank on 2008-02-20
> **ToaStOmGi said:**
> Alright well i have Ubuntu installed on both of my computers. But i decided i wanted to have Vista back on 1 of them and keep Ubuntu on the other. So i tryed to install Vista back onto my computer and it says my drivers arnt in the right format? Says it ahs to be in the format of NTFS. So im guessing it changed when i switched to Ubuntu? Idk, i need some help tog et those back to the right format.

HI and what drivers are we speaking of? Can you download the window drivers?

---

### Post by ToaStOmGi on 2008-02-20
> **overdrank said:**
> HI and what drivers are we speaking of? Can you download the window drivers?
I try to install Vista and it says drivers arnt found, wrong format. needs to be in NTFS format. Thats all i know. I can take a screenshot if needed. And how do i download the windows drivers?

---

### Post by ToaStOmGi on 2008-02-20
any1 else know what to do?

---

### Post by overdrank on 2008-02-20
> **ToaStOmGi said:**
> I try to install Vista and it says drivers arnt found, wrong format. needs to be in NTFS format. Thats all i know. I can take a screenshot if needed. And how do i download the windows drivers?

HI and are you saying the drives are not found? Like trying to install vista it says no hard drives found. If so then use the Ubuntu live cd and just format the drive with gpated under system, administration.

---

### Post by djheadley on 2008-02-20
I think you mean drives - not drivers.  So you're saying that Vista is telling you that it can't work with the drive because it isn't NTFS?

---

### Post by ToaStOmGi on 2008-02-20
> **djheadley said:**
> I think you mean drives - not drivers.  So you're saying that Vista is telling you that it can't work with the drive because it isn't NTFS?
Ya

---

### Post by jordafitz9 on 2008-02-20
> **ToaStOmGi said:**
> Alright well i have Ubuntu installed on both of my computers. But i decided i wanted to have Vista back on 1 of them and keep Ubuntu on the other. So i tryed to install Vista back onto my computer and it says my drivers arnt in the right format? Says it ahs to be in the format of NTFS. So im guessing it changed when i switched to Ubuntu? Idk, i need some help tog et those back to the right format.

i have the same problem please help:confused::confused::confused::confused:

---

### Post by ToaStOmGi on 2008-02-20
> **djheadley said:**
> I think you mean drives - not drivers.  So you're saying that Vista is telling you that it can't work with the drive because it isn't NTFS?
Ya

---

### Post by soccerguy53 on 2008-02-20
Can you use the ubuntu live cd to format the hard drive as NTFS?

---

### Post by ToaStOmGi on 2008-02-20
How do i do that?

---

### Post by overdrank on 2008-02-20
> **ToaStOmGi said:**
> How do i do that?

Hi as stated previously, use gparted under system, administration on the live cd. Delete the windows  partition then before formating you will have to restart the system. If the windows partition is mounted during the live cd make sure you unmount it. You can tell if the drive is mounted by a lock being present in gparted.
This link has some screen shots of gparted in action but during installation. [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by ToaStOmGi on 2008-02-20
I dont want to dual boot tho. Will that still work?

---

### Post by overdrank on 2008-02-20
> **ToaStOmGi said:**
> I dont want to dual boot tho. Will that still work?

I just posted the link so that you could see a screen shot of gparted in action.

---

### Post by nicholas1520 on 2008-02-20
Just use the Vista install cd, just select the parititions and press delete and hit format - it will format it in NTFS and you will be able to continue the installation.

---

### Post by ToaStOmGi on 2008-02-20
> **nicholas1520 said:**
> Just use the Vista install cd, just select the parititions and press delete and hit format - it will format it in NTFS and you will be able to continue the installation.
So if i click delete it wont ruin my harddrive? It will elt me change it to NTFS?

Also, im in gpartions. What do i do now?

---

### Post by ToaStOmGi on 2008-02-20
Im in partions editor. So how do i format it to NTFS?

---

### Post by soccerguy53 on 2008-02-21
As stated earlier it would just be easier to use the vista cd and delete all the current partitions on the hard drive.  Then format the entire hard drive and continue with the Vista install process.  I've never installed Vista but it should work this way is it does in XP.

---

### Post by jespdj on 2008-02-21
Forget about doing difficult things with gparted. If you just want to reformat the whole harddrive and install only Windows on it, then just boot the computer from your Windows Vista DVD. Delete the existing Linux partition(s). That will ofcourse not ruin your harddrive. You cannot normally ruin hardware by using software.

(It works the same way in the setup of Windows Vista as in XP).

---

