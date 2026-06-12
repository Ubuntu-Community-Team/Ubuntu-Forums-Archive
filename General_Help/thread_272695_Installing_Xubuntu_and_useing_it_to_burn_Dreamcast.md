---
title: "Installing Xubuntu and useing it to burn Dreamcast games"
date: 2006-10-06
forum: General Help
---

### Post by BWF89 on 2006-10-06
I have a friend who got an old computer from someone in his family. It's still running Windows 98, has 100+ viruses on it, and he didn't get any OS install discs with the computer.

For all his needs Linux should more than suffice. But one area where it might become a problem is CD burning. He needs to burn Cdi images and possibly the occasional Mds and Nrg ones. But mainly Cdi. Theres no applications AFAIK on Linux that will let you burn those formats so we'll need something to convert them to something you can burn on Linux. An Iso file.

I know of two programs, (are these in the Ubuntu repos?) Cdi2Iso and Nrg2Iso. If he's converting the a Cdi image of a Dreamcast game to an Iso file will the game play correctly on a Dreamcast? What settings on these 2 programs would I have to enable for the game to convert correctly to an Iso file and what settings while I'm burning it should I enable for it to play on a DC? Also, Cdi2Iso and Nrg2Iso are both CLI based. How easy is it to use the command line to convert the files itno an Iso file if you've never used a non-Windows OS or the command line in your life?

I don't know what the specs for the computer is but since it's running Windows 98 it's processor is probably in the 200-500MHz range (right?). Is that enough to install Xubuntu? If not, what other user-friendly distros are there that would run on an older computer?

---

### Post by tdwester on 2006-10-06
Xubuntu should work great. I have only burned dream cast games in windows but there is a linux version of nero for the .nrg files.

---

### Post by BWF89 on 2006-10-10
I talked to my friend on AIM today and he tried to install the OS from the main menu when Xubuntu cd loads up and it went to a blue screen and froze. He let it sit for 2 hours but it never unfroze. Then I told him to let the live cd part of the OS boot up and have him click on the installation icon on the desktop to see if that worked. He informed me today on AIM that it froze up when he tried that too.

What could be the problem?

---

### Post by kick6 on 2006-10-10
I don't think its necessarily a good idea for you to ask for help on pirating software on this forum.

---

### Post by matt_risi on 2006-10-10
Doesn't necessarily mean he's pirating games, he could be burning homebrew games, etc. At any rate, I think it's important that everyone gets at least the same usage out of an Ubuntu machine as they do with a Windows one, otherwise why bother?

Get your friend a Live CD of Xubuntu, but this time burn it SLOWLY, like I'm talking < 10x. I made quite a few coasters burning Live CD's too fast and I just thought Linux was shit before I finally installed it successfully (with a cd that wasn't correupted by fast burning). Now Ubuntu 6.06 is my principle operating system. :)

---

### Post by BWF89 on 2006-10-10
> **kick6 said:**
> I don't think its necessarily a good idea for you to ask for help on pirating software on this forum.
I didn't nessessarily say he was pirating software ;) 
> **matt_risi said:**
> Get your friend a Live CD of Xubuntu, but this time burn it SLOWLY
I thought that might be the problem aswell. I only burned at 8x, the format I usually burn CD-R's at but I'll try 1x this time and give it to his mom (shes a lunchlady) when I see her at school tomarrow.

---

### Post by matt_risi on 2006-10-10
8x should have been plenty slow, maybe something's weird with his bios booting from cd's or something. Meh, 1x is worth a shot. Xubuntu is the bomb.

---

### Post by BWF89 on 2006-10-12
Talked to his mom at lunch and she told me the version burned at 1x froze up during the pre-installation process as well.

Then I talked to him online when I got home and he thinks he knows where the old Windows 98 installation discs are. So he won't need my help setting up Linux, which is a burden off my back.

---

### Post by matt_risi on 2006-10-12
lol yeah I was gonna ask if you were prepared to take calls and try to diagnose and fix a computer over the phone. Linux problems are UGLY like that. You definitely have to be there, or at least post a detailed description of the problem with the offending script pasted in. Oh well.

---

### Post by BWF89 on 2006-10-14
Talked to him yesterday and he said whenever he puts in his Windows 98 install disc on bootup he gets a blue screen with one of those flashing white boxes your supposted to type commands in over in the corner. I didn't know what to tell him.

---

### Post by Zyphrexi on 2007-01-13
I don't know why, but I always end up making coasters as well. It angers me. I found the suse cdi2iso package, installed using alien, converting the isos didn't seem to work though. (I mounted it in ubuntu via a script) It's annoying how many self-boot discs are in .cdi format. There's a custom v2 pso server out there for the dc, but requires some tweaking. Have you ever tried the dreamsnes? There's a pike installer i believe.

---

### Post by BWF89 on 2007-01-17
> **Zyphrexi said:**
> I don't know why, but I always end up making coasters as well. It angers me. I found the suse cdi2iso package, installed using alien, converting the isos didn't seem to work though. (I mounted it in ubuntu via a script) It's annoying how many self-boot discs are in .cdi format. There's a custom v2 pso server out there for the dc, but requires some tweaking. Have you ever tried the dreamsnes? There's a pike installer i believe.
I've never tried DreamSnes. Can you burn Nero or Discjuggler images on Linux or a Mac? If I did this I'd probably do it on my Mac.

---

### Post by sdk7_25 on 2007-01-19
Well, since lurking and searching these forums has provided me with countless answers, I think i'll lend a hand. dreamcast et al used to be a big hobby of mine so a lot of this is from memory but I do have a lot of experience with getting homebrew to selfboot

> I found the suse cdi2iso package

A Dreamcast image will never be self-booting if you burn in ISO format.  Why? Because you can't selfboot from a single session disc.  The reason why everyone used cdi is because, at the time people were developing extensively, DiscJuggler's cdi format was particularly good at multisession images.  

AFAIK, there are no open source tools to do what you need in linux.  That being said, I think that you could use the newest version (there's a trial) of Isobuster in the newest version of Wine to convert just about any selfboot dreamcast image into bin/cue and then burn it with K3b or GnomeBaker but, I don't have any personal investment in figuring this out at the moment and my DC is in storage.  If there's a large enough interest (which I really doubt there is ATM) I could look into it further.

Anyways, that's where I would start if I was going to try to burn selfbooting images of stuff like DreamSNES (way slow BTW) in Linux.  But, more than likely, the speed you're burning at has little to do with why your burning coasters.

But, as if I haven't drawn this out long enough, I agree that this isn't the place for piracy.  However, there are a lot of really cool homebrew apps for DC.

---

### Post by Zyphrexi on 2007-02-05
beating dead horses - 


now i got the wii... i think i'll run "homebrew" from that

---

