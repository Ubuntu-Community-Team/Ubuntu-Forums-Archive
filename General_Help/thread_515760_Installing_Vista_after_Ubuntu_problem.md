---
title: "Installing Vista after Ubuntu problem"
date: 2007-08-02
forum: General Help
---

### Post by samopal on 2007-08-02
hi there, 
is it even possible to install Vista next to existing Ubuntu installation? I have Ubuntu (actualy kubuntu 7.04 32bit)  that I'm working with and want to install Vista on same hdd. 

my partitions> 
40GB free - primary, boot flag 
150GB ext3 kubuntu - primary 
4GB linux swap 

I need to reinstall Vista/XP OS in this 40GB partitions often and I really don't want to backup and reinstall my kubuntu OS everytime... 
now, I have tried to burn 100% right Vista x86 Business image to 100% right DVD-RW (and DVD+RW too) and booted. I said I want to install Vista on 40GB partition, no problem, but after Vista installer stage of "Expanding files" at 89% it everytime hang up with error code 0x800706F8 - Vista can't find required files, or similar error message. I've tried to google this error code without success. Does anybody faced similar situation and could give a hint? Can it be associated with my grub configuration?

---

### Post by FleetAdmiral74 on 2007-08-02
Maybe you have a bad download? I am assuming you are just pirating it.

I hate to condone piracy, but you might try another download and see if you get the same error.

---

### Post by dfreer on 2007-08-02
Well, when you boot to CD, it doesn't even boot GRUB, so I don't think it is that. I believe the "Expanding Files" Stage has to due with uncompressing data from the Install CD/DVD into RAM, so it may possible be a RAM error. You probably would've noticed problems before this if it was RAM, so my primary guess would be the Install CD/DVD.

EDIT: "Vista can't find required files" definitely sounds like a bad CD/DVD.
You can definitely install Vista alongside Kubuntu, although Vista will take over the MBR so you will be unable to boot kubuntu right away. You can either keep the vista MBR and use NTLDR or whatever the vista equivelent is to boot kubuntu, or you can reinstall GRUB into the MBR and use it to boot Vista.

---

### Post by shdwsclan on 2007-08-03
Yeah, generally its a bad pirate, probably a chinese one which is a POS. 
Maybe the same one i got.....
For those that think im evil for pirating, im not. I  HAVE a key provided to my through msdnaa, and my msndaa admin told me to just torrent the 64 bit version, since they didnt get one yet M$. They got one now, so i have to order the dvd for $12, and totally wash this chinese version. I dont know, i might not even install it, and just run xp, cause vista is really getting on my nerves.....


Anyways, the way i did it on my ibm z61 is i installed partitioned  part of the drive for vista, rebooted, and then installed, then i ran mac os, partitoned the HFS partion space after ntfs, and left the rest as free space. Then i used ubuntu live to install the lat part on sda 3 and sd5, .....sda 4 is the logic break on the drive....

I didnt have any trouble. THe only trouble was when i go into hibernation, then ntfs-3g doesnt recognize the drive at all....

---

### Post by samopal on 2007-08-03
thanks for suggestions. no pirate am I, I'm clean and completely legal. I've got Vista from msdnaa too. I've tried to download it 2 times and I downloaded completely identical copies and tried to burn them on 2 different brands of DVD-RW, so I "assume" it's not bad media problem, but I will check it out to make sure. Also I will do some memory test and will let you guys know there, how I did.

---

### Post by dfreer on 2007-08-03
> **samopal said:**
> thanks for suggestions. no pirate am I, I'm clean and completely legal. I've got Vista from msdnaa too. I've tried to download it 2 times and I downloaded completely identical copies and tried to burn them on 2 different brands of DVD-RW, so I "assume" it's not bad media problem, but I will check it out to make sure. Also I will do some memory test and will let you guys know there, how I did.

On a side note, I also got Vista from MSDNAA... although I only had it installed for a grand total of 3 days. ;)

---

### Post by samopal on 2007-08-04
ouch, sorry guys, my fault. It was nothing else than badly downloaded dvd image... I had got 2 of them and I burned wrong one... Now it works again. 
I hope that this topic will at least help other people, because when I was googling about this error code, nothing good I found. :guitar:

---

