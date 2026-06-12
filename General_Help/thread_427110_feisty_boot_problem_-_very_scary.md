---
title: "feisty boot problem - very scary"
date: 2007-04-29
forum: General Help
---

### Post by davezac on 2007-04-29
hi
i am not aware of any significant changes to my setup - however their may have been some system updates. the last thing to work properly was amarok (playing the killers) and then the system seemed to die.

i am unable to boot to my login page. the boot process goes so far (i see the ubuntu splash timer) and then hangs. all i get then is the timer.
i have tried this [fix]("http://swik.net/Ubuntu/Only+Ubuntu/How+to+Fix+broken+Ubuntu+Feisty+Fawn/1iah") the fix seems to run but no change to my situation - and also i am not quite sure if i am following the commands correctly.

i have tried booting from the feisty live cd but when the partition check commences it hangs at 60%.

thinking that it may be a disk/volume problem i then booted a live gparted cd. this didnt find any problem with the partition.

i do have a few things starting on boot like mySQL. one of my db's is sizable (mp3 collection) and i only have 256Mbs of ram on this box. is this lack of ram an issue?

any help appreciated.

---

### Post by happy-and-lost on 2007-04-29
Running Gnome and Amarok on a box with 256 mb is probably not the best of ideas, as it means loading both the Gnome and KDE libs into a very limited space. Rhythmbax doesn't bite, you know :)

How much swapspace do you have set up?

---

### Post by davezac on 2007-04-29
hi thanks for reply

i have 2gb set up for swap - anticipating that i would get 1gb of ram. 
the thing is though, that no h/w changes have been made.
if i want to check this by say disabling mysql on boot up how can i intercept the boot process?

thanks again

---

### Post by davezac on 2007-04-29
i have been able to load feisty in live mode. however when attempting to install form the desktop icon, the install hangs at partitioning the disk (always 60%).

anyone any ideas???

---

### Post by m.musashi on 2007-04-29
Reboot but this time don't hit enter. Hit "e" and then edit the boot line to take out the "quite splash" bit. Press enter and then press "b". You will see all the text scroll but when it hangs you will see what it was going. Take a picture of the screen or write down where it hangs. The info should help to determine what is causing the problem.

EDIT: to clarify. Choose the line that starts with "kernel"

---

### Post by davezac on 2007-04-29
is this for the live boot feisty or my installed feisty?
thanks for the tip - i will try tomorrow

---

### Post by m.musashi on 2007-04-29
> **davezac said:**
> is this for the live boot feisty or my installed feisty?
thanks for the tip - i will try tomorrow

Do that with the installed Feisty. It should help to see where things are hanging up during boot.

---

### Post by davezac on 2007-04-30
thanks for the advice. i now have the following.

*Mounting local filesystems...                                     [OK]
*Activating swapfile swap ...                                      [OK]
*Configuring network interfaces...                             [OK]
*Setting up console font and keymap...                     [OK]

root@media-centre:~#


and thats it - it just appears to crash out to the shell.
doing an ls here gives me 'Desktop' an empty directory (ls -lsa gives the . and .. dirs)

there doesnt seem to be any error messages. just seems to be lacking the command to start the desktop.

i appreciate any help :confused:

---

### Post by m.musashi on 2007-04-30
Does it mention anything about a maintence consol or pressing ctrl-d to exit? I've seen that before and after pressing ctrl-d it finishes booting. However, your problem sound different but just checking options.

On my system (and likely yours), right after

-Setting up console font and keymap

is

-loading ACPI modules or something similar.

It's probably either related to font and keymap or to ACPI.

I am betting that the problem is ACPI related. I've had my fair share of ACPI problems. However, it seems odd that you get this on a system that was already successfully installed. One possible way to check would be to boot without ACPI. I'm not 100% sure how to do this but I think you will edit the kernel line in the grub menu before you boot (similar to when you turned off quite splash). This time you want to add
```
acpi=off
```
I think you do that at the end of the kernel line. Take out quiet splash and add acpi=off. See what happens this time. I think that is the proper way to pass options to the kernel at boot but if it doesn't work we might need to see what help others can offer or do some searching on passing options.

---

### Post by davezac on 2007-04-30
thanks for this musashi - 
i will try this out tomorrow - give me a chance to research ACPI ! - strange however, that there are no error messages - just going to the prompt. i may take out my nvidea card and try that.

be seeing you ):P

---

### Post by davezac on 2007-05-03
still unable to fix this hang problem.
i have edited the grub menu line by erasing the quiet splash and adding the acpi=off config. still exactly the same place as i was.
the strange thing is though that when i tried to re-install ubuntu and it was checking the partitions i hung during the check.

does anyone have any idea as to why i am unable to boot?

getting a bit desperate now.i will be re-inserting an old HD which has Edgy on later !!

---

### Post by m.musashi on 2007-05-03
I wish I could help. I know how frustrating these types of problems can be. However, I'm pretty much out of ideas. I'm pretty new to Linux myself and we've explored the possibilities that I am aware of. It does sound like a hardware issue but I'm not sure how to collect additional information to help us pinpoint it. If you are having trouble reinstalling that seems further evidence of a HW problem. Any way to check if your drive is bad or failing? There are some tools out there that can check check a drive without booting from it. I think one is called Ultimate Boot CD. It has a variety of tools and boots from the CD. You might look into that.

---

### Post by statictonic on 2007-05-03
Just curious but have you run any type of hard drive check to make sure you hard drive isn't going bad?  It is something that could definitely be a possibility.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
Download/burn ubcd from the link above and run Drive Fitness Test on it or seatools.

---

### Post by bmorency on 2007-05-03
statictonic has a good idea. The same problem happened to me where my system would hang while booting. It happened out of nowhere too.I checked the hard drive and it turned out that I had some bad sectors.

---

### Post by m.musashi on 2007-05-03
> **statictonic said:**
> Just curious but have you run any type of hard drive check to make sure you hard drive isn't going bad?  It is something that could definitely be a possibility.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
Download/burn ubcd from the link above and run Drive Fitness Test on it or seatools.

Yeah. That's the thing I was talking about. Thanks for finding the link.

@davezac- let us know if that provides any useful clues.

---

### Post by davezac on 2007-05-03
i'm onto it. thanks guys

---

### Post by davezac on 2007-05-05
loaded the ubcd. ran a few utils to check the partition/volumes but all fine. 

now reformatted the partition - thinking that i could just re-install ubuntu (i was careful to put /home on another partition). however got into another problem because i am getting a "no root file system defined" in the partition manager and i am unable to install the os.

fantastic - thanks ubuntu!

now re-installed edgy 

went like a dream - gparted worked as it should. managed to retain existing users in home dir. just have to re-install my LAMP apps now and start again. i will wait a while before upgrading to feisty.
whoops will have to change my profile !!!

thanks to all who helped - especially m.musashi

---

### Post by m.musashi on 2007-05-06
Sounds like you got something working. Glad to hear it. The manual partition with Feisty is a step backwards in my option. I guess they assume most people will just do the default set up so maybe they are focusing on that. However, with the manual partition you have to create a partition for each part (/home, / (ie root) and swap) AND define a mount point for each. It's not a smooth as the edgy install and doing it on a drive that was one big partition to begin with took a 20 minutes to set up - mainly because I kept doing it wrong :).

Also, you can only have 4 primary partitions on a drive (unless there is a way to change that now) and on the laptop on which I was working, Dell had a hidden partition. With windows, dell, /home, root and swap that made five and I had to start over and make a logical partition for Ubuntu.

---

### Post by davezac on 2007-05-06
thanks for that m.
do you know if edgy has a problem with >5 partitions? - i am thinking of re-doing the install.
if i go for a feisty upgrade following edgy, does this mean that >5 partitions will cause it not to install?

i have come across the dell and hp hidden partitions. they sometimes keep the recovery disk there i believe, or it is used when using the recovery cd. quite often though they dont give you the recovery cd when you buy the machine. it is only when you need it that you have to buy it - or go linux of course!

---

### Post by m.musashi on 2007-05-06
The hiddent partion(s) are usually related to recovery. I've thought about copying to a CD and removing but haven't yet - just in case.

The 4 partition rule is not related to windows or Ubuntu. It's just a HD rule. It may have something to do with DOS as I think DOS still governs HDs before an OS takes over (but don't quote me on that). So, it won't matter if it's edgy, feisty or whaterver. The fix is to just to make a logical partition instead of a primary one. Linux seems to work fine that way (but I don't think windows will).

---

