---
title: "GRUB will not time out and boot default"
date: 2007-02-25
forum: General Help
---

### Post by addicted_to_the_net on 2007-02-25
Hello, I have looked and searched for an answer to my problem and havent found a solution..

I can't get GRUB to use the default entry to boot without selecting from the the list of options.  I have tried the timeout, default, and it just sits at the menu waiting for my selection.  The menu even says the selected option will boot in 3 seconds, but never does.

Any one have a hint on what could be the problem?

---

### Post by wireddad on 2007-02-25
Can you post your menu.lst?

---

### Post by addicted_to_the_net on 2007-02-25
here it is, thanks..

---

### Post by dcstar on 2007-02-25
> **addicted_to_the_net said:**
> here it is, thanks..

Well, as far as I can tell the "timeout" line is commented out, which is one good reason why it won't timeout and continue booting.

---

### Post by addicted_to_the_net on 2007-02-25
Both the default and the timeout were uncommented and still no auto boot.. the menu would show the correct option highlighted and say at the that it will be 3 seconds.. but just sat there waiting until I hit return on the default option..?

---

### Post by dcstar on 2007-02-25
> **addicted_to_the_net said:**
> Both the default and the timeout were uncommented and still no auto boot.. the menu would show the correct option highlighted and say at the that it will be 3 seconds.. but just sat there waiting until I hit return on the default option..?

I think that means that a keyboard character has been sent to Grub and interrupted the process, perhaps something in your hardware is erroneously sending a character during the boot process?

---

### Post by addicted_to_the_net on 2007-02-25
Well I am at my wits end, searching with no results and I even unplugged the keyboard, mouse and same result.  Ran sudo update-grub, no change.  This has been happening from the begining, install of Edgy server 6-10.  Can I re-install GRUB or do I have to re-install the whole os?.. Maybe another boot-loader possible?  I have to have this option working so that I can add it to my other server and only have access through ssh.  Thanks for your help.

---

### Post by rsambuca on 2007-02-25
When you take out the "#" in front of the "timeout" line are you sure you are saving it?  Have you closed it, and then opened it again to see that the "#" is in fact gone?

---

### Post by addicted_to_the_net on 2007-02-25
I have tried changing the default option to 0, 1, 2 as well as changing the timeout to 3, 5, 10 etc.  I have run update-grub I have set the default to "saved" and reboot twice just to be sure it was setting the default after I had selected it at boot... This has been my first problem with ubuntu since I sarted about 5 installs ago.  My other server box has allmost all the same settings and it works fine.  Going to keep trying, any other suggestions most welcome...

---

### Post by addicted_to_the_net on 2007-02-26
Is it possible to use apt-get to remove GRUB and then install again without messing up the whole boot?

---

### Post by rsambuca on 2007-02-26
Do you have another keyboard you can try?

---

### Post by addicted_to_the_net on 2007-02-26
But I didn't even have the keyboard hooked up on several tries.. but let me see if that helps anyways.. thanks will try now..

---

### Post by addicted_to_the_net on 2007-02-26
"The Highlighted entry will be automatically booted in 3 seconds"... no auto boot, with new keyboard, the correct selection is highlighted.. boots fine when I hit enter on the selected option... thanks again for your help

---

### Post by rsambuca on 2007-02-26
Sorry, but all I can think of at this stage is to completely re-install grub from scratch (although I am the kinda guy that would prefer to figure out what was wrong in the first place).

---

### Post by addicted_to_the_net on 2007-02-26
Well I just don't know what could be the problem.. besides hardware issues.. using an old 667mhz cpu and 256 sdram.. anyways.. could you give me some pointer on re-installing GRUB?.. It might be just as easy at this point to re-install Ubuntu server 6.10 or a new version.. what do you suggest that I do? Thanks again!

---

### Post by JohnPhys on 2007-02-26
if you do sudo grub-install /dev/hdwhatever it should write a new menu.lst file and re-install grub to the mbr, if you think something there is messing up your install.

---

### Post by addicted_to_the_net on 2007-02-26
I just did the sudo apt-get remove grub and then sudo apt-get install grub and it went flawlessly... then same boot problem after two boots (just to check).. so somthing is just not working right...??

---

### Post by addicted_to_the_net on 2007-02-26
and I did a grub-install /dev/hda1 still no timeout

---

### Post by addicted_to_the_net on 2007-02-27
Allright so to solve my agony I found a very helpfull person on the #ubuntu irc channel that had me try the timeout to = 0 and low and behold!!! it worked,, so timeout = 0 works and thanks alot <qhartman> I really appreaciate it!.. And thanks for all the other help I have got on these forums.. thank you thank you... what I would do without this kind of support... go with another distro of course!!,... THANKS!!!

---

### Post by pissedoffdude on 2007-02-27
> **addicted_to_the_net said:**
> and I did a grub-install /dev/hda1 still no timeout

try ```
grub-install /dev/hda
```

---

### Post by addicted_to_the_net on 2007-02-27
yep just did that, thanks, and same deal with the timeout set to 3 it doesn't work.. but with timeout set to 0 it works...thanks for the input

---

### Post by addicted_to_the_net on 2007-02-27
i just don't get how it works on 0 timeout but not on any other,, could this be a bug?

---

