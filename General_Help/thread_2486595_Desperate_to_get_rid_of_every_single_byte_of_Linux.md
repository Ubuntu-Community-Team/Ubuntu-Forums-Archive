---
title: "Desperate to get rid of every single byte of Linux on my machine, willing to pay"
date: 2023-05-05
forum: General Help
---

### Post by fjellstrom on 2023-05-05
So, ill not go in to details because I know from experience on other forums that I was never able to get help due to people getting more curious about me showing proof of "the hacking" etc, but I feel it could be relevant to how you perceive my issue

Ive been battling this monster of an RDP/trojan who installs linux partitions and modifies my booting/kernel/bios (i can easily reclaim the bios using linux myself, but i just use the uefi until he is gone)

Few facts: His "base" is the X:, that is completely unremovable in every single way as far as i know. 
Formatting on every lowest level possible does not do anything even remotely close to getting rid of it (dban, erase etc)

Ive bought new laptops, all got infected right off the bat, which i realize now has to do with USB. I can not buy another one, but if I get this sorted I can at least sell the others after removing it from them


I have full access to his root when i log in to linux using a rescue disc like Parted Magic, which is great. I had to speedlearn linux over the course of 2 weeks since i never used it before. Tried to remove all his stuff like in windows the first time (delete all files/folder, yeah you can imagine how that went)

He basically uses udisks2 to hide my real HD and lets me use a virtual one in its place, so i was formatting the virtual one for ages :)
I found the real one yesterday, formatted it hardcore, but then i gave up not knowing what to do after, after every single secure erase (its an SSD) using NVME, theree is like 1.5gb left on it, and after 10 minutes, that is 5gb, 20 mins, 30gb. With me just idling.

All of these /etc/ /dev/ lib folders has a ton of symlinks and files which im scared to touch, i just modify all his config files to mess him up in order for me to get to protect my windows installation better on the next install, which usually works so i can use my machine for a day before he breaks through and is back in full control.


So, nevermind dealing with the rdp hacker in question, ive contacted authorities but they take months. Offline does not matter much it seems since he has virtual hotspots around/nearby as well based on my neighbours wifi's I believe, or bluetooth stuff, i know he uses a lot of bluetooth and samba to get a direct connection with me. Turning it off in windows does nothing, he is in full regedit mode, anything i turn off instantly gets reactivated.



TLDR: How can I uninstall linux FULLY, as in remove every single file and folder after cruising in to the environment using a live cd? I don't trust any sort of formatting tool, or any DD/shred command. Can I just rm -fs every dir one by one from the live cd?

Tell me what screenshots you need while in the linux environment and I will get them asap

---

### Post by fjellstrom on 2023-05-05
At the moment ive never been so close to get rid of this, im shaking

Ive formatted it differently with namespace, crypto erase etc and only 1.08mb remains and it doesnt increase ever, the 1.08 was added after i created a gpt partition table

HOWEVER. There is this persistent "File System" (its called that) in linux where all his files are, that is 7.5gb. Where are those 7.5gb coming from?? It drives me nuts

---

### Post by dragonfly41 on 2023-05-05
Some guesses .

Rogue USB perhaps?


Some tips I read ..


[https://uk.pcmag.com/security/138149/dont-plug-it-in-how-to-prevent-a-usb-attack](https://uk.pcmag.com/security/138149/dont-plug-it-in-how-to-prevent-a-usb-attack)


[https://www.bleepingcomputer.com/news/security/heres-a-list-of-29-different-types-of-usb-attacks/](https://www.bleepingcomputer.com/news/security/heres-a-list-of-29-different-types-of-usb-attacks/)
[URL="https://www.makeuseof.com/what-is-a-usb-drop-attack/"]
https://www.makeuseof.com/what-is-a-usb-drop-attack/[/URL]


OR


perhaps you allowed a guest to access your router?
[https://www.lifewire.com/guest-network-for-home-tutorial-818204](https://www.lifewire.com/guest-network-for-home-tutorial-818204)

Change the router passwotd but the intruder is still inside, which is a cleanup job.

The above just raises the bar for hacker gaining access.


Finally, cleaning your SSD

[https://security.stackexchange.com/questions/256037/how-can-i-wipe-an-infected-ssd](https://security.stackexchange.com/questions/256037/how-can-i-wipe-an-infected-ssd)


Pro help from this Security sub-forum .. 
[https://ubuntuforums.org/forumdisplay.php?f=338](https://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by yancek on 2023-05-05
Which Linux system are you using?  There are over 1,000 different ones and they differ in many ways.  You are posting on an Ubuntu forum, so does that mean you have one of the dozens of Ubuntu derivatives?  If you format a drive, part of it is used by the filesystem so some small part will show even with no data, usually about 5% of the drive size.

How do you know this 'hacker' is a he.  Could be a she or do you have someone specific in mind?

---

### Post by QIII on 2023-05-05
The reason you were asked to show that hacking took place is that often what seems like "hacking" is a misunderstanding on the part of the user.

But we'll assume you were somehow attacked.

[This Arch article]("https://wiki.archlinux.org/title/Solid_state_drive/Memory_cell_clearing") has a good, step-by-step process for clearing/factory-resetting the memory cells on an SSD.  That is the very lowest "formatting" possible. You'll need to look at the NVME section if your device is such.

In case someone has compromised your router, go to the Arch article, print it, keep it handy and unplug your machine from the router and the router from the web before you start the cell clearing process.  An intruder could otherwise watch your every move and counter you.

If your router is compromised, you may have to shoot it, burn it and bury it in a rural area in an unmarked grave.  Compromised routers are difficult in the extreme to deal with for an end-user, even using the "factory reset" process.  If you plug it back in to update its firmware after cleaning up everything else, the intruder could just foil you and watch you fixing that.  The current firmware itself can be compromised and the intruder will just chuckle.

Just for grins ... it is not impossible for an intruder to compromise motherboard firmware.  If that is the case, you may have to shoot the machine, burn it, throw it in your car and roll the car off a cliff into the sea.

I am being slightly facetious, of course, but such compromises can and do happen.  It is highly unlikely in the case of a personal machine, since there would be little profit in the effort for a hacker.  But it is possible.

---

### Post by yancek on 2023-05-06
>  
So, nevermind dealing with the rdp hacker in question, ive contacted authorities but they take months. 

I would not expect much help from the police as they will usually be dealing with situations where there are thousands of users/machines compromised.  As pointed out above, there is not much likelihood an unknown hacker will spend as much time as s/he apparently has on a single machine unless that person has an extreme dislike for you personally.  Have you anyone in mind and if so, have you given that information to the police?

---

### Post by fjellstrom on 2023-05-06
Thanks,
dev
I get that, but trust me i wouldnt spend every waking moment on trying to get rid of some invisible ghost im just imagining for over a month.. Ive never used linux in my life and i see a whole environment there with full logs of everything i do, every single piece of device and how he manipulates it/changes PCI

before i knew what was even going on i spent 2 weeks formatting his stupid virtual HD he put me on to install windows on each time, while he had hidden the real one using udisks2. So now im a bit more seasoned and he actually makes real efforts on stopping me since he saw i got close to cleaning his environment once, i think at least, i could also not even be remotely close and in for just another rabbit hole. Ive been through several of them already. Infinite symlinks exploit, an old polkit exploit from 2012 that never got fixed (or got fixed very recently, regardless i dont know how to deal)

Plus i just also realized he has had a special profile for me every single time i use any chromium browser or firefox basically, he logs every keystroke and can watch my screen, i saw it in chrome://flags and firefox:about  i believe it is. 

WHATS EVEN MORE INSANE IS THAT HE HAS NOT ASKED FOR MONEY, COMMUNICATED AND HE EVEN KEEPS UP WITH ME WHEN I SIT 20 HOURS STRAIGHT WTFFFFF. I find it absolutely insane, he cant be doing this for fun. Plus , the amount of information he has on me by now he will DEFINTELY know im the wrong guy if he wants money. He just wants to see me suffer

Ive been up since i was just about to reply to dragonfly and yanncek right after their posts, i was downloading kubuntu and kali. Going to try quber-os next i guess, which probably wont do much since its a preventative OS, does nothing if hes already inside :/ 

Before i get suggestions on new machine, new hd, police, all that stuff - already done that. But theres at least 2 months before ANYTHING happens, i will literally pay up to 500 depending on how long it takes if someone would guide me through this linux maze of shithole he has created. To be honest, i think 70% of his **** is from chatpgt or some extremely advanced automated self-learning RAT , like 30% him and 70% automated. There is no way he is creating so insanely comprenesive scripts and logs of what im doing, how im doing it, when im doing it, how its countered etc


For some reason he is having issues dealing with me when i use magicparted livecd and logging in with the HYPER-V option, so ive been sitting and sanitizing and secure erasing his rubbish randomly finding real devices to do it on, but 99% not. nvme list does absolutely nothing, no linux command does anything as far as i know from googling when he is hiding it among 300 blocks and udisks2


I mean i guess i can uninstall his **** with the packet manager but he has INFINITE amount of apps and there is this stupid order in linux , i cant delete X because it has dependencies to X V Y N and M.

Let me just post this text so he doesnt mess me up before that and then ill take some screenshots or video to show you whats going on

---

### Post by fjellstrom on 2023-05-06
peacehttps://files.fm/u/gp5r6qnfk

It is a .webm video, just showin*g some stuff that makes it really obvious im not making any of t*his up, but as you can see i have *no clue what is going on or what i* am doing out*side of the basics, secure erasing his stuff uninstalling, then* *the n*ext phase is usua*lly me flashing the bi*os which buys *me 15-20 mins, during that i install windows, which of course, always is on his condition* since every single installation get*s pre-seeded with his drivers and his setup via OOBE* / helpers *before i can even log in. I gain advantage there thro*ugh *really crazy "block everyt*hing , tele*metre, remote desktop* etc with one *click app , i got several of those, then* i use regedit special softwares too so i can mass search and get full access to regedit and remove a lot of stuff there, like his proxies and network control of me. its 50/50 if i remove stuff that ends up messing me up so i have to reformat again, or if i mess him up enough so i get like 4 hours or so of peace with youtube and some calm browsing. Man, that feels so good its hard to describe, like finally kicking the intruder out of my home so I can get some peace of mind a few hours. 

It is stressful to say the least, it literally feels like having an intruder in my home that Im trying to get rid of most of the days, its affecting my work too. Luckily i work from home these days but still\\

Ill try to upload it somewhere so you dont have to download it. But i am certain that is safe, both due to its format and i also scanned it with that linux antivirus thing, clam something. And its very likely his stuff is from both USB , and also synching drive, since he hijacked two of my phones also, so he can utilize them constantly if i have them on. Its I N S A N E.

---

### Post by fjellstrom on 2023-05-06
So yeah, i did not write that "peace" and it was nowhere in my vocabulary or thought during that text. That is definitely him too, i think here has been a word here or there a total of 4-5 times for the month+ we battled. Earlier today when i was downloading ubuntu and other stuff he cancelled them last second and the link became "hi.no/ubuntu.iso" so yeah i know hes watching every keystroke, hes always eager to put sound on every time he makes a connection, web cam ive covered since long ago so he wont have too much fun there, unless on the phones i guess.

Anyway, please help me get rid of his blocks, and I absolutely need to find a way to reset and delete the windows X: partition and regedit, regedit is like it resets itself everytime i reboot or something. He has like 100 different task scheduling tasks that triggers upon everything i do basically, so i have to shut those off also. And dont even mention the policies , group/local etc. I cant believe there is no simple way to mass insert policies outside of having an IoT or enterprise windows / insider. Thats when I am in windows, which i usually have a bigger chance to fend him off, just that i do a lot of stuff manulally, he just automates most and pre made powershell scripts. His whole entire setup for the first hour or two is like fully automated, i know exactly what will happen and when after a windows installation, also dependant on if i use a build with defender enabled or disabled, both has pros and cons.
c 
I have a good idea on how ill get the bios back that he has hijacked (i only boot from uefi) , but i wont mention that here for obvious reasons. I just need the linux part, i have literally used linux for 2 weeks, i never even saw how it looked before that, even if ive used computers for a long time, its clear he outclasses me on every front


My advantage has to be that i have physical access to everything, that has to be such a big enough advantage that I will be able to deal with this shitface.


Oh, I should also say he has been sloppy and left traces here and there. I have saved his whole de-encrypted regedits and also recovered a lot of files that he thought he had overwritten well enough, which will be used for police later on, some really good evidence. But some stuff are just dumb by him, he took a screenshot once and laid it on my desktop when he obliterated Eset cloud end point, a high cost business type anti virus that i managed to get a full version trial for, and he broke the software down in 10 minutes , and then logged in to the site , took over admin and made a fool of me and them. But he made  a fool of himself too because there was timestamps  in his screenshots (in the picture itself), showing 6 hours behind me, and im in sweden, so he is in Us east. 

He also speaks fluent chinese. Those are two things I can share that I know about him, and also because i know he reads and i want him to understand that this will not end well for him, the longer this keeps  going, the closer I will get to him, especially when professionals gets involved.



Sorry for straing off so much, im overtired, just typing whatever comes in to my mind.
Just please think of it as ive just received a computer from a relative, but theres a bunch of his old linux stuff in there and i never use linux, and formatting doesnt seem to help get rid of it. Ignore the hacking part, i really am desperate for some expertise, and anyone who is willing  to put a bit  effort in to helping me, and it yields results, i will pay without hesitation

---

### Post by fjellstrom on 2023-05-06
Sorry about the quality, i saw it was horrendous.. but i uploaded another one, hopefully better


[https://vimeo.com/824358279?share=copy](https://vimeo.com/824358279?share=copy)  - no download there just streamed

the initial first one there too: [https://vimeo.com/824357416?share=copy](https://vimeo.com/824357416?share=copy)

Turns out both are poor quality, either way its better if anyone who thinks he or she has enough knowledge to assist in linux, would tell me what info they need/what i should screenshot or record for them to brainstorm or troubleshoot this the best way

---

### Post by ajgreeny on 2023-05-06
> **fjellstrom said:**
> Thanks,
dev
I get that, but trust me i wouldnt spend every waking moment on trying to get rid of some invisible ghost im just imagining for over a month..[COLOR="#FF0000"] Ive never used linux in my life and i see a whole environment there with full logs of everything i do, every single piece of device and how he manipulates it/changes PCI[/COLOR]



Please explain; are you or are you not using Linux, ie, Ubuntu or another of its flavours?

And please restrain your bad language as this is a family used forum so you use of such language is totally unacceptable and will not be tolerated here no matter how frustrated you are.

---

### Post by fjellstrom on 2023-05-06
Apologies, i appreciate that you give it to me straight. Its been so tolling on me mentally, to hate being in your own home and have no way of not being there, that i become numb to everything else (including of how i express myself), so that puts me back to reality a bit.f a
  
I am using Medicat live cd there, which is a disk with a ton of various environment rescue stuff, boot manipulation, drive utilities etc, and one of the tools i been using the most is Parted magic, a live cd in that "kit" Medicat
But I have access to ubuntu, kubuntu, kali live cd etc, but i just dont know what to do really, im at a bigger disadvantage when i do a real installment of linux rather than just using live cd, because the usb/live cd is more protected (often mounts in the ram etc) 

Plus, every time i install or write to a flash it seems like he has some auto script that puts a preseed list of what packages i will download, there are  files called "preseed" i notice afterwards


I did buy ubuntu one out of desperation, and the hacker did not like that, he was really active in preventing me from enabling the protective mechanisms that it offers. But i havent given it another go for quite some time. I am still subscribed to it though so I do have access to it if I were to use an ubuntu livecd or installment.


Heres a bunch of screenshots also, task manager, and folders containing some of his environment etc

[https://i.imgur.com/KuyEPY0.png](https://i.imgur.com/KuyEPY0.png)

[https://i.imgur.com/e8HT4qo.png](https://i.imgur.com/e8HT4qo.png)

[https://i.imgur.com/fxxpLjT.png](https://i.imgur.com/fxxpLjT.png)

[https://i.imgur.com/9MPkTGF.png](https://i.imgur.com/9MPkTGF.png)

[https://i.imgur.com/r31y7Me.png](https://i.imgur.com/r31y7Me.png)


As you might guess, im quite lost here. Its too hard to learn linux at that level in two weeks. Its overwhelmingly open.

So to clarify, i have no environment of my own, and i dont care about any data, its routine t o format once or twice daily lately. He even has a silly file called ResetSystem or something in windows when ive sabotaged too much in regedit for him, so within an hour of him using that, windows is dead, gone and unbootable. The lucky few times are when i manage to keep him out for a long period of time through a mix of an antivirus/firewall he hasnt seen before so he doesnt have a premade anti setup for it, as well as having all samba stuff, rdp etc blocked. 

Im really considering virtual machines would be the safest option, like a VM from a live cd if i cant get anywhere until the authorities finds time, and that can take months, at least, unfortunately. 
So the VM option is in case it looks impossible even for you experts/experienced with linux. 


I am also not caring much about bricking my whole system anymore if it means a shot of getting it cleansed. I know he uses efivars and I also know that can brick my system unfortunately.


Oh - guess whats even more fascinating, and shocking out of a security perspective. He can use my environment offline, and Im not talking about hibernate. He can use it for much longer and then sync it online, thanks to something in linux called Hot plug, think its a part of efivars if i read it correctly. Thats crazy for real.
s
Heres his efivars folder. Just one look at the filenames and you know he got most things covered. I still think I can win this though, its all still software-level, except for the USBs. As long as it stays at that, its always possible to clean him out, its just a matter of how , and once you know, you apply it swiftly in a pure offline environment with no internet or phone even close.


[https://i.imgur.com/kmbFFWq.png](https://i.imgur.com/kmbFFWq.png)s

---

### Post by TheFu on 2023-05-06
Why not just replace the HDD/SSD and be done with it?

You can boot from a USB Flash drive with "permanent" storage areas setup and never use any internal HDD/SSD.  
If the "hacker" comes back under that situation, then the problem isn't linux or the storage. It is with some peripheral or your LAN security.  Until you clean those other things up, forget about having any computer on your LAN in a safe way.

If you think efi is the issue, switch to legacy boot.  I assume you've already put new firmware onto the motherboard BIOS, retrieved using a different system.

While highly, highly, highly unlikely, there have been cases where supply chains were hacked and viruses were inserted in firmware for different devices BEFORE they were shipped.  In very few situations, govts have intercepted hardware during shipping and replaced some parts with thing computers to prevent any work-around.  I've never seen either of these in real life.  This is CIA-stuff (any from their counterparts around the world in the main technology 20 countries).  These methods are for extremely targeted groups, not individuals ... except tech journalists reporting about govt actions.

If you are being re-infected, then something about your normal security is flawed.  Don't allow Javascript on untrusted websites would be one of my first steps.  For example:
> If you're seeing this message, that means JavaScript has been disabled on your browser, please enable JS to make Imgur work.


---

### Post by oldfred on 2023-05-06
Not familiar with medicat. I might be more suspect it is perhaps corrupted? 
Better to use Ubuntu (or a official flavor) and add any additional apps.
I create my own flash drive with multiple ISO like gparted, parted magic, Boot-Repair, rEFInd, etc and full install of Kubuntu (my preferred flavor).

I see install of python2 which is obsolete & should not be installed or any software that needs python2 as it also then is obsolete. 
Only an advanced user perhaps converting an old python2 app to python3.

Please do not post screen shots as we cannot easily read them nor copy any useful data.
Copy & paste using Forum's advanced Reply and use # to add code tags around the text.

---

### Post by aljames2 on 2023-05-06
This all reads as though you’ve lived with this nightmare for ages. You indicate several times you have very little knowledge of Linux but yet you are expressing with confidence and such great detail of what has happened to you including technical expressions of intrusion tactics.  I guess I’m confused by what your situation really is, and where you are coming from on all this.  You have said very little about your network.

Per TheFu, get your network cleaned up and under control.  Don’t even think of reusing the gateway that you have, and don’t enable any Wi-Fi until you have things under control.  If you have to use Wi-Fi at home, put it on a separate physical network but only after you are fixed.  This guy or gal can’t own you like this if you just do some fundamental things to secure your home network.

Be cautious of any of your backups.  If you have versioned backups, you should be able to go back in time and get potentially unaffected data.  If you do not have versioned backups, then I would test the backups on a separate physical network from the LAN, before actually introducing that data back into production.

---

### Post by dragonfly41 on 2023-05-06
I have not experienced your woes. But ideas. You could start a Virtual Ubuntu Desktop session through some cloud provider to stay in touch with Ubuntu practices, quite separately from your frazzled local system. I use a cloud account which I can shut down to save costs.Then get ghostbusters on the job to purge your real local system and suspect SSD.
Your local contaminated SSD can be purged using dd administered through LiveUSB (you purchase a *new* USB SANS flash drive and create LiveUSB). To fox this perpetrator install rEFInd for booting local desktop. But he/she might be reading this forum.

You might also update your BIOS and buy a new router..

And here is yet another attack profile:

[https://uk.pcmag.com/news/119592/evil-usb-cable-can-remotely-accept-commands-from-hacker](https://uk.pcmag.com/news/119592/evil-usb-cable-can-remotely-accept-commands-from-hacker)

---

### Post by fjellstrom on 2023-05-06
I sort of knew this would happen the moment i bring up the hacking/trojan part, I tried on two other forums a few weeks ago and I gave up and went on my own again. I guess I have myself to blame though for even mentioning it, since that is much more fun and interesting to both question if its really happening (I mean, come on) or why its happening or suggest things Ive tried at least five times already. . That is why I stressed on to pretend this is a machine I received from a relative. And I want to get rid of all that stuff

On the other hand, its looking really well right now, i progressed a lot using Esets live rescue CD, for some reason I had much more access with that, i dont know how i could have, i mean root is root and encrypted is encrypted, still I did so I went ham on the delete portion to the point he couldnt do anything or even login for a long time.
Then when he finally got in, i was watching task manager for his actions and i saw something "if dd=..." or whatever it is and I stared at it thinking I know that command, i read it somewhere..yea 5 seconds later i figured out, and mid-log out my machine froze. Every single file was still in my usb though, that rescue cd is nuts. 


Lets break down what I would like help with instead since I understand this is equally confusing for everyone else when I am all over the place, im sorry about that.

1. It seems like almost all of those loops are copies or fakes of my ssd? I saw signs of it in some HD software. Is that possible, and how do I get rid of the loops?

Does anyone possibly have any idea of what or where those 7.5gb comes from that he hides in? Also when I right/click on i think lib or bin something, it counts up to around 300 000 files and 120TB.. TB! How is that possible!? Linux is a different world , no question about that.

Please look at this, is anyone able to make sense of it? Im certainly not

[https://imgur.com/a/sg15nhC](https://imgur.com/a/sg15nhC)

3 screenshots in it

---

### Post by fjellstrom on 2023-05-06
I flash my bios up and down perhaps 20 times a day, ive bought a new router, i bought new HDs, i ripped out bluetooth and wifi card from my laptops. Funny enough, the asus router is linux based, so, a few days in i was noticing some stuff didnt work properly. I kept turning off WEP, yet it enabled itself. Then i reado n forums its linux based, and this guy hangs out in the linux partitions and me in windows, so guess who was having fun with my router all while im thinking im super safe now... 

Im going to tell you something that  you wont believe, although I can prove most of this, if not all, but there is a lot Im saving for authorities since its going to become a police matter. 

The reason to why i really, really ask to not provide any advice (outside of the questions i provide along with the screenshots and more), even if they are coming from a good spirit, is because whatever it is you are suggesting, i have tried it, actually i tried more , much more.

I have bought 3 laptops, 2 phones. Brought over my dads laptop (cheap) to do a pxe boot since that seemed to bypass his commandprompt script that pops up the second before installer starts.

EVERY single one of them are infected. Got infected within an hour.
I didnt want to say it because its going to make most of you guys run in to another rabbit hole and find explanations and ask me if i did X or X for that to happen - no, no, no, is the answer to those questions. Its much more complicated, and it might be really, really bad if it is what I think it is related to, but i can absolutely not say that here. But it would involve modem, a built in sim/phone with 4g in a specific laptop in my home, and the reason for it would be a whole book. Lets just not go there please.

Just know that every single thing possible you can connect to a machine with, is being used against me. Hes actively navigated himself around my appartment using bluetooth devices. I still can not figure out where or how he can have like 4 hot spots IN my appartment that are on 24/7 even if all my electronics are off. I dont have the energy to figure that out either, im just trying to focus on figuring this secret to wiping that 7gb off once and for all, then i can save like 4 laptops (plus several neighbours who i am certain of are infected too, when I log in via live cds sometimes I log in to his environments, and I can see that he is actively, or was actively using the wifi of neighbours to get to me)


Ill leave it there, 

Currently i figured out a way to really mess his scripts and stuff up, both in the linux partitions and windows. In windows, lets just say shift-f10 is extremely effective mid-install.

Linux is still where I need your guys expertise. Like how can he lock stuff from me, or "out-root" me? in my own machine. We are both root, yet i dont have permission to delete certain things. I read something about chroot, is that what i need to do on those things? If there is no graceful way of doing this, im just going to go berserk on delete button and what happens happens.

I am waiting for a Firewalla though, i think that will be a gamebreaker for safety, non wifi version.

I tried a Pfsense firewall thing but that was much too complicated for me, and i dont have time to learn that i feel

---

### Post by QIII on 2023-05-06
Let me ask this directly, since you mention that you are "in Windows" and you mention "loops".

Are you running a Windows machine, seeing a Linux partition?

If that is the case, would you please post an image of the tool you are using to see that you have a Linux partition from Windows?  Not from the file manager, but from a Windows partition tool.

---

### Post by TheFu on 2023-05-06
I think the OP is confusing loop mounts with real storage.  It is easy for someone not used to snap packages to see that and become confused.

The OP needs to stop using any RF networking.  No wifi. No bluetooth.  

1 ethernet wire into a wired router (Asus is fine, just be certain it is patched and locked down with wifi disabled).  Ensure physical security to the router, the ISP modem, and the computer are solid.  

Encryption only helps when the computer is powered off.  The rest of the time, when the storage is unlocked, it doesn't help anything.

So the network should be this:
```
Internet/
&#9492;&#9472;&#9472; Asus-Router
    &#9492;&#9472;&#9472; Linux-PC
```
Nothing else. No wireless at all.
The Router needs to be running current firmware, have all inbound ports blocked, and wifi disabled.
No phones should have any access to the PC.
Boot from a brand new flash drive with an Ubuntu ISO dd'ed onto it.  This is a read-only boot.  Impossible for anyone to modify.
If the Linux-PC is hacked, then you know it is some perpherial hardware - that would be storage, keyboard, mouse, or any other USB device like a scanner or printer or headset or joystick or whatever.  Unplug all USB device, if you can.  A good PS2 mouse and keyboard generally can't be used to load a virus. They aren't smart enough for that.
Run in this mode for a week.  If, as you claim, it gets hacked, just reboot from the flash drive and that's all gone.
BTW, the Ubuntu ISO needs to be updated at least monthly or it will have published bugs in it and could be hackable.

You could also take this PC to a different location, say a public library, and use their internet connection. If you aren't hacked there, then it is your network, not the PC at all.

---

### Post by QIII on 2023-05-06
Snaps, WSL from Windows  ...  

Intrusion so detailed and persistent would be rogue nation-state or three letter agency level and would not likely be directed at an individual person's machine.

---

### Post by Impavidus on 2023-05-07
I've looked at your screenshots in post #12, but there's nothing suspicious in them. Remember (or look up) what /proc and /sys are: pseudofilesystems. What you find there aren't files on your SSD or livedisk, but information about your running processes and OS. They exist whenever you OS runs. Nothing strange about loop devices either. They're used to access entire filesystems stored in ordinary files, which allows compression, encryption, additional security settings and distribution of the filesystem as a single file. Preseeds on a Linux live disk are a normal part of the configuration of the software on the live disk. I'm not saying that your Windows system has no intruders, or that your router has no intruders, but with 2 weeks of Linux experience, you can't say what's normal and what's not on a Linux live system.

The root user has permission to do everything, but that doesn't mean he can do everything. Root can't modify files on a read-only fiesystem and the possibilities on pseudofilesystems (/proc, /sys, /dev are the most important) may be limited in not so obvious ways.

If there are hotspots in your appartment when all your electronics are switched off, somebody must have physically installed them (or project them from nearby). Not impossible for a service like the CIA or FSB, but only if they specifically target you (or your neighbour).

---

### Post by HermanAB on 2023-05-07
Hmm, as far as I can figure this just looks like a paranoid newbie who doesn’t quite understand how a modern Linux system works, then suffering from finger trouble.

Just relax and enjoy the machine and try not to screw it up so quickly.  It will eventually start to make sense.

---

### Post by QIII on 2023-05-07
As I said above ...

> often what seems like "hacking" is a misunderstanding on the part of the user

---

### Post by kurt18947 on 2023-05-07
> **TheFu said:**
> 
.......................
You could also take this PC to a different location, say a public library, and use their internet connection. If you aren't hacked there, then it is your network, not the PC at all.

One thing in this thread that got my attention.  OP mentioned WEP when talking about network connections. I certainly hope that was a typo or brain cramp.

---

### Post by fjellstrom on 2023-05-08
Yes, and one of all the mac addresses I looked up, most if not all being spoofed of course, I believe was not spoofed due to how I obtained it and it led me to something that seem very close to what is going on with my environment, based in Israel. About security penetration automation (which also would relate to my work in a way)

But enough of that since thats speculations

I am in pure disbelief that people are still thinking all of these objects are actually normal. These are UBUNTU INSTALLATIONS on my windows only machines. Archlinux being there too. I mean, I AM actively UNINSTALLING packages from UBUNTU, ARCHLINUX. KERNELS! 

Does anyone want to remote in to me via reminna or what its called? Or anything?

I think im very close now because of something I did, made the real drive etc exposed, but i still can not figure out how to get rid of the last 8gb

How can i obtain permission on read only stuff that he has? I dont care about bricking, i dont think this can be done in a pretty way, I will delete every single item by hand if i get the full permission access/can change read only and those persistent files. Screenshots coming

---

### Post by fjellstrom on 2023-05-08
It is the network. Ive taken it to my dads place and it was not present or active in the same way, until he or it realized that I was using that location for PXE installations, and it managed to infect his machine too, he does not care about it though, it/he doesnt bother him unless attempting to remove it. 

Again, would anyone be able to please remote in and help me with the last pieces? Ive done nvme sanitizes sanact 2 and formats, it just doesnt get rid of that last 8gb with hundreds of symlinks, as well as his efivars etc.

---

### Post by fjellstrom on 2023-05-08
Whats a bit scary about this is that there are like maximum 10 posts about this on the whole internet that I found, forums, users that are experiencing in DETAIL the very same thing I am, in precise detail. And every single thread just dies off or gets filled with people claiming troll, lie. The earliest one I saw dated back to 2013. 

I just found one that dates back to 2011. Its insane, its literally exact how he describes it. *Edit, jesus theres a lot of poor suckers who has experience with that thing like me. I think you have to actually experience this malware/hacker type in order to believe all of it, i have not even described 10% of what its capable of/what it has been doing etc because it would just call for getting a trollstamp. 
[https://social.technet.microsoft.com/Forums/windows/en-US/0b3c1a20-5438-443b-9964-f81c23950cca/how-to-delete-the-x-boot-partition?forum=w7itproinstall](https://social.technet.microsoft.com/Forums/windows/en-US/0b3c1a20-5438-443b-9964-f81c23950cca/how-to-delete-the-x-boot-partition?forum=w7itproinstall)

Here is one that is also the same but on a swedish forum, so google translate unless you know swedish. Funny enough he is so sick of it also that he is offering rewards/payment to anyone helping him getting rid of it
[https://www.sweclockers.com/forum/trad/1458360-formatera-skrivskyddad-partition-virus-fran-helvetet-beloning-utlovas](https://www.sweclockers.com/forum/trad/1458360-formatera-skrivskyddad-partition-virus-fran-helvetet-beloning-utlovas)

I will even pay half upfront to anyone who is serious on helping me with this, can remote in or have some live chat going on during this

---

### Post by fjellstrom on 2023-05-08
edit: doublepost accident

---

### Post by fjellstrom on 2023-05-08
LOL. I see now why I found a registry part that was encrypted (I decrypted it with a software) that "banned" me from installing win7 or win8, i always wondered why those installations would never work on the live CD's i obtained. This seems to be key at least, or one of the only ways of formatting/getting rid of that silly X: partition where it resides<br><br>[https://www.youtube.com/watch?v=hZivYMA2qRA](https://www.youtube.com/watch?v=hZivYMA2qRA)

I have to say it's the ultimate genius malware/hacking tool - to install itself and reside in the one place that is basically completely unremovable and untouchable. I dont know what Microsoft was thinking with that.

---

### Post by Impavidus on 2023-05-08
As suggested in post #21, is there any way WSL could be involved? It stands for Windows Subsystem for Linux and is a kind of lightweight virtual machine to run Linux in Windows. This being a Linux forum, most of us don't know much about it.

Sorry, it's a bit confusing. You mentioned that you found some parts of a Linux system on Windows, but you also use a Linux live system, and it's not entirely clear what you see where. You show a lot of symptoms, but little context.

BTW, asking people on some web forum to remote into your system is the fastest way to get intruders.

---

### Post by fjellstrom on 2023-05-08
Im using a linux live cd, i have not installed a single linux item ever on this machine. Trust me, im not spending 8-20 hours per day for 1.5 months on something that isnt ACTIVELY ruining my machines. It would take the biggest nutcake in the world for that. Please read the threads i linked for example.

Or just tell me what you want to see to believe it.

Are you telling me a folder like this would be normal on a windows only installation machine? Not on one, but on 4 in total.
I can also show you screenshot of my phones default installed applications, how my Notes app for example has 80 different, unremovable permissions (no its not rooted)

[https://imgur.com/WCd2j86.png](https://imgur.com/WCd2j86.png)

It really is as insane as I make it sound, no actually, its much much worse than I make it sound. I am downplaying this a lot to be even remotely believeable.

And yes he keeps messing up my system time / clock as you can see, i dont know how , but i can never keep it stable, i also dont know the importancy of it

---

### Post by fjellstrom on 2023-05-08
You might be right, but i have nothing to protect on this machine, and there is NO intruder in this world that can make it worse. That intruder himself would get too annoyed by whatever it is haunting my silly machine that hed probably leave asap. Why try to break something that is already FUBARd. I welcome any intruder at this point, some company at least :)


How about tell me a few commands to run to get a better/fuller overview of  things? I dont know more than the basic ones , ive been googling pretty hard, but it still takes me like 15 minutes to extract an .appimage file. 

But there must be plenty of things i can do, i have access to systemctl, just whenever i do a --help i just get exhausted, i think my brain is too overloaded with all going on, being given 10000000 options while being completely lost is exhausting. Thats why im asking fof help here, and paying for it too

Like im trying to get back control of my hard drive for one, maybe thats the wrong way to go but in this whole maze, once i find all these NVME variants, i dont know what to do either. Im also curious what "spaceman" is, he has it on all the windows installations too as startup on task scheduler.

[https://imgur.com/C6bfNs5.png](https://imgur.com/C6bfNs5.png)

---

### Post by oldfred on 2023-05-08
Not familiar with xfs nor spaceman

But google just gave me this:
[https://man7.org/linux/man-pages/man8/xfs_spaceman.8.html](https://man7.org/linux/man-pages/man8/xfs_spaceman.8.html)

If a newer user better just to use default partitioning like ext4 for Linux partitions and if UEFI FAT32 for ESP partion.

---

### Post by TheFu on 2023-05-08
I think this is a Windows user who believes Ubuntu was installed by a hacker into his Windows computer and wants Ubuntu gone.
That immediately makes me think this is 100% Windows issue and that asking for help on an MS-Windows forum would be better, since I haven't installed and MS-Windows anything except a tax program in the last 10 yrs.

If MS-Windows was more secure, then it wouldn't be so easy for someone to get into the system and take it over, as the OP suggests.

I've already suggested cleaning up the network, ensuring all network equipment was patched/current, keeping all suspect devices off the network, using dumb peripherals (no USB-anything), wiping the HDD completely, and never saw that the OP did any of those things.  Seems like a Windows problem to me.

I'll say it again.

> If you are being re-infected, then something about your normal security is flawed.
Nobody remote will be able to figure out what that is and I wouldn't think of doing this sort of full-security effort for less than US$xxxx  to start, not including replacement hardware.   Celebrities often have issues like this and their solution is to hire an IT pro to manage all their devices, home+business networks and to provide training for themselves and their immediate family, hoping to prevent reoccurance.  Sadly, even if the person paying takes everything serious, the family probably won't so the home network will be cracked again.  I've seen 2 networks setup for some homes ... which keeps important work stuff completely separate from casual users.  It is expected that the casual network will be full of viruses and worse.

There's no 1-click tool to solve this.  It is down-n-dirty systems and network architecture efforts, training, re-training, and learning to change common behavior that the world appears to do, though security pros do not.

Because there is MS-Windows involved, I'm not qualified to help.  In the 1990s, I started shifting away from Windows towards Unix and Linux systems.  My Linux systems have been hacked 3 times over the decades.  Twice was my  fault and stupidity.  The most recent time was in 2017 and I'm blaming Ubuntu for that because it enabled, by default, bluetooth.

---

### Post by QIII on 2023-05-08
Would you please go to Apps & Features and see if WSL is installed?

---

### Post by fjellstrom on 2023-05-09
Ah, Ive done that 3 weeks ago several times , this is on a different level. It does not matter what settings i chose in windows because he has already pre-set power policies and whatnot. I click turn off hibernate? Yeah sure, nothing in the slightest happens even if the command lets me think it does, simply because of how powerful regedit (and linux) is. 

Turn off all wifi in windows? Nope, he sets the interfaces in linux, makes them completely invisible to me in windows. I cant even do netsh interface set interface name=xx admin=disabled 

This night i realized i have no chance unfortunately, this is beyond me, and also beyond all of you. I had a plan to decoy with a really annoying windows installation, I shift+f10 mid-install, change regedit stuff up really bad for him, since i know exactly what happens step by step, 3 printers installed, default user enters, trustedinstaller starts doing ****, system takes over, always 2x SYSTEMs on every permission-location, one with the shield and one without, not hard to guess which one is who. appx packages
 everywhere deployed etc.

After that, i shut down my machine, hold powerbutton 2 minutes to gas out all electricity, rip out all cords for internet, phones off. I boot in to an isolated live cd environment and plug in an external HD i just bought to install linux and then a windows VM on it, first encrypting it. Encryption worked, so 15 minutes later during install i hear the HD make this vaccuum sound, spinning like insane, heat goes up and then i get some io error and restart. Next thing i see using Victoria and some other well renowned HD reparation tools is every single sector is FULL red, unusable, destroyed. Im not sure i can even repair it. f i can it would take like 30 hours.

And the final straw was after that, still everything turned off, i login and i use something called registry manager, where you can see all encrypted stuff in the registry and do mass searches, and watch updates live.

I see how bluetooth connections are being used every second basically and i just lean back and mentally give up. Bluetooth. Phones off. Wifi, i know he has access to them/neighbours. But this is bluetooth, he uses that even more than wifi, samba and printer **** to get me. WITH WHAT DEVICES? I DONT GET IT

This is govnerment level, 100%. I dont know why, but no one does this for fun, and he is not alone, its a team.

I pray neither of you ever get to experience this.

This is beyond extreme level of expertise so im not going to waste anyones time.
Ciao

Im getting a chromebook

---

### Post by fjellstrom on 2023-05-09
Before i go, want me to upload his registry and you can take a look at it for yourself and you'll see how ridicilous it is? I have a few backups of it. Use "Registry manager" to view it to see all super encrypted bits etc
I think the free version should be enough [https://www.resplendence.com/downloads](https://www.resplendence.com/downloads)

---

### Post by Impavidus on 2023-05-09
> **fjellstrom said:**
> 
Are you telling me a folder like this would be normal on a windows only installation machine? 

[https://imgur.com/WCd2j86.png](https://imgur.com/WCd2j86.png)

Not normal on a Windows machine running Windows, but it is normal when you use a Linux live disk. This looks like the live system's filesystem. Depending on the state and configuration of the Windows system, the Linux live system may not even be able to access the internal harddrive.

> And yes he keeps messing up my system time / clock as you can see, i dont know how , but i can never keep it stable, i also dont know the importancy of itNo, I can't see. I can see the time in your screenshot (18:46), but I don't know at what real time you created that screenshot. However, I do know that Linux normally stores the time in UTC, while Windows stores it in local time. Seeing the time off by plus or minus the offset between your local time and UTC is normal.

---

### Post by The Cog on 2023-05-09
@fjellsrtom: I see a few posts saying your screenshots look normal, but maybe a clearer explanation of why they look normal might help. 

Firstly, I want to point out something I think you may not be aware of (forgive me if you are aware and I'm just misunderstanding things):
When you run a Linux live CD, the OS creates a virtual disk+filesystem in memory. The whole live OS runs from this in-memory disk image. When you go exploring the filesystem, it is this in-memory disk image you are exploring. Do not confuse this with the contents of your windows SSD drive. 

To further confuse matters, Linux creates a view into the internal workings of the OS, and it makes that view look like files. The "files" in directories /dev, /proc and /sys are not real files - they don't exist on the filesystem, they are just a view into the inner workings of the OS. When you boot a live CD, you end up with virtual files that don't even exist on the in-memory virtual filesystem. 

All the screenshots I have seen in this thread show the contents of this virtual drive, and most just show the virtual files view that looks like a bunch of files in the virtual filesystem.

You may be able to see the contents of your SSD  from a live Linux CD: the drive should be listed in the left panel of the file manager. You may be able to "mount" that SSD drive, but it will very likely be mounted read-only because of the way Windows shuts down - you must disable fast-boot before shutting Windows down if you want to be able to mount the Windows drive read-write.

In summary, I suspect you are seeing alien-looking things on the live-CD virtual filesystem and mistaking those for things on your own hard disk. 

Oh, and yes, by default Windows and Linux interpret the time on the hardware clock differently which may explain your apparent messing with time. Windows likes to set the hardware clock to local time, whereas Linux likes to set it to UTC (GMT).

---

### Post by oldfred on 2023-05-09
If you are using encryption, did you not see it is a full drive install. So in partition manager drive will be full. 
But it really uses LVM - volumes. So main partition will have your / (root) volume. The / volume typically only uses part of the allocated space. You then can add volumes or expand your / to use more space. Volumes are easy to expand, but difficult to shrink, so that is why they do not use entire space at beginning.

[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

LVM &  LUKS2 install 
[https://ubuntuforums.org/showthread.php?t=2461714](https://ubuntuforums.org/showthread.php?t=2461714)
LVM as graphical organization, TheFu
[https://ubuntuforums.org/showthread.php?t=2485286](https://ubuntuforums.org/showthread.php?t=2485286) 

You post long rants without giving much information so we can help you.
We ask for results from various commands but never see that. Those can be run from your install or from the live installer.

---

### Post by fjellstrom on 2023-05-09
Im not sure how to respond to this, its so absurd to me on so many levels. Maybe I have to record a full video in high quality to really show you that a windows installation is like a fast paced starcraft match at this point. 

You can never convince me, or yourself that this is even remotely normal when booting in with a live cd. Which live CD would that be, if so? 

LOCKED, read only configurations for my whole system/firmware in an efivars kernel folder. That is one hell of a live cd!
[https://imgur.com/kmbFFWq](https://imgur.com/kmbFFWq)

And it also installed around 2000 packs for me
[https://imgur.com/r31y7Me](https://imgur.com/r31y7Me)

---

### Post by oldfred on 2023-05-09
I do not think I have ever looked at my efivars. It should be locked and some system files are even more locked than others for security reasons. Things users should not mess with. In Windows they just hide those partitions/folders.

I still see python2????
What are you installing. Specifically what distribution? And with what tool?
Best to use Ubuntu 22.04.x latest .x available or if older system a light weight flavor.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

Post this command for your install.
```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /etc/*release [/COLOR]
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=22.04 
DISTRIB_CODENAME=jammy 
DISTRIB_DESCRIPTION="Ubuntu 22.04.2 LTS" 
PRETTY_NAME="Ubuntu 22.04.2 LTS" 
NAME="Ubuntu" 
VERSION_ID="22.04" 
VERSION="22.04.2 LTS (Jammy Jellyfish)" 
VERSION_CODENAME=jammy 
ID=ubuntu 
ID_LIKE=debian 
HOME_URL="https://www.ubuntu.com/" 
SUPPORT_URL="https://help.ubuntu.com/" 
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/" 
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy" 
UBUNTU_CODENAME=jammy


[/FONT]
```

And please stop using screen shots. Copy & paste terminal output and use code tags.
Easy to add code tags using Forums Advanced editor Go Advanced and # icon.

---

### Post by The Cog on 2023-05-09
> **fjellstrom said:**
> Im not sure how to respond to this, its so absurd to me on so many levels. Maybe I have to record a full video in high quality to really show you that a windows installation is like a fast paced starcraft match at this point. 

You can never convince me, or yourself that this is even remotely normal when booting in with a live cd. Which live CD would that be, if so? 

LOCKED, read only configurations for my whole system/firmware in an efivars kernel folder. That is one hell of a live cd!
[https://imgur.com/kmbFFWq](https://imgur.com/kmbFFWq)

And it also installed around 2000 packs for me
[https://imgur.com/r31y7Me](https://imgur.com/r31y7Me)

It's not at all absurd. It's perfectly normal, except that recent live Linux "CD"s don't fit on a CD any more. For several years, I have used USB sticks, and recently I've had to use 4G sticks because 2G is too small. Again, I say that when booting **any** modern live Linux, the contents of /proc, /sys and /dev are **not real files**. They are not real even on a full Linux installation on a hard disk They are a view into the operating system's running configuration, processes and devices. Windows doesn't (as far as I know) expose its inner workings in this manner, but Linux does and it's fundamental. Here's some links to documentation for it: [https://unix.stackexchange.com/questions/188886/what-is-in-dev-proc-and-sys](https://unix.stackexchange.com/questions/188886/what-is-in-dev-proc-and-sys)

If you refuse to believe this then we are all wasting our time. 
If you will accept it and want to continue, we can go on to discuss how to mount and view the content of your actual physical SSD drive.

---

### Post by fjellstrom on 2023-05-09
That is what im saying, i'm not installing anything. I have not installed a single package except for nvme-cli. He has built his environment for about two months before I caught him, and I only did so because I noticed suspicious events on my work laptop with remote powershells coming at it with very shady scripts among other things. 

You have to understand I have no linux installment, thats the point. I boot in with a live (usb), which often mounts his loop0 or hides in the RAM and have full root access, yet i dont know what to do or how to do it. I can't stress enough how sophisticated this is, self learning, persistant, automated to probably 80%. You can use one antivirus or tool once or twice with success, after that its useless because it has self learned a counter, or he is a genius-level hacker who just lives off of this or something, he is definitly skilled though, one of his strongest tools is the calculator and he is super protective of it when I am defending a windows installation, and I figured out its due to calculating binaries for regedit. As mentioned earlier, regedit is insanely powerful and I've had him wipe the drive/pull some nasty "reset" trick a few times because of how I messed up his registry so much using Registry Manager. I just search for "remote" and delete like 30 keys, "bluet(ooth)" and delete 100 etc.

---

### Post by fjellstrom on 2023-05-09
If you find me a live cd that has efivars and will automatically add and lock the computers every single piece of device and firmware, or anything that is even close to that, i will agree. I dont understand how it can even be in someones imagination that it could possibly be the live cd. Linux is a different world, not just the OS... I am just not ready for it or even close to it

Anyway im not sure why i keep taking the bait all the time, so far i've received i think 1 or 2 piece of real advice throughout the whole thread with 5 pages.

---

### Post by tea for one on 2023-05-09
> **fjellstrom said:**
> If you find me a live cd that has efivars 
Live session using Xubuntu 23.04
Path = /sys/firmware/efi/efivars
Contents: 95 items (First file is Administrator Secure Boot)
Size: 64.6KiB (66,184 bytes)

Can I claim the reward?

---

### Post by dragonfly41 on 2023-05-09
This very old thread refers to rEFInd as an alternative boot.

[https://askubuntu.com/questions/204187/how-to-disable-uefi-variables](https://askubuntu.com/questions/204187/how-to-disable-uefi-variables)

In fact I use rEFInd every boot up. You might try booting up via rEFInd to "fox the enemy".

And another clue .. here ..

[https://imgur.com/WCd2j86](https://imgur.com/WCd2j86)

You have RescueZilla CD installed .. here we see rescuezilla-2.4.2-64bi...  raw CD image 1.1 Gb 05/08/20...

Could that be rogue? From what source?

---

### Post by QIII on 2023-05-09
Remove your Linux media.  Using Windows tools, do you still see the partition?

If you do, you have a Windows problem.  For help with that, you will need to go to a Windows forum.

If not, you are seeing the Linux partition on the live Linux media.

---

