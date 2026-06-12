---
title: "Failed to set Xfer mode"
date: 2007-04-22
forum: General Help
---

### Post by phoenixankit on 2007-04-22
I burned the downloaded Ubuntu .iso to a CD-RW, then booted by pc from the disc. I got a couple of options, i chose the first one(something like 'install') Then some more things happed, and then a black screen appeared which said :[the stars stand for some other stuff written above it]
********************************
********************************
cant access tty;job control turned off
failed to set xfermode (err-mast=0x4)
failed to set xfermode (err-mast=0x40)


and then nothing happens

this is not the full stuff written, it's the one i remember. Help please!!!!

---

### Post by ChadMC on 2007-04-22
I have this same problem on one of my computers. I finally got it installed. But every time I boot, I get the same error. It eventually boots up perfectly without any side effects. But it adds about 1-2 minutes to the boot time while it spits out those errors.
edit: using the final release of feisty by the way

---

### Post by phoenixankit on 2007-04-22
How did you get the Installation done?

---

### Post by phoenixankit on 2007-04-22
SOMEONE....PLEASE....I'm DESPERATE FOR UBUNTU

---

### Post by phoenixankit on 2007-04-22
OMG...SOMEONE atleast

---

### Post by BackwardsDown on 2007-04-22
Try hitting F6 at the install screen an add acpi=off to the bootline of the Kernel. That helped for me.

When ubuntu is installed you will still have this error but ubuntu will boot just fine (although the booting process wil take 2 minutes longer). The bug is already reported on launchpad.

---

### Post by phoenixankit on 2007-04-23
f6 acpi=off 
when do i do this. you mean at the first screen which has 5-6 options including "Start & Install" ???
if it IS at that screen, then I just type it there or do i have to delete some text too? After typing what do i do...press enter? 
PLEASE HELP

---

### Post by phoenixankit on 2007-04-23
So, I guess, Bye bye Ubuntu, welcome SUSE

---

### Post by kernelsandirs on 2007-04-24
try this [http://ubuntuforums.org/showpost.php?p=2513159&postcount=4]("http://ubuntuforums.org/showpost.php?p=2513159&postcount=4")

---

### Post by amosharper on 2007-06-09
> **kernelsandirs said:**
> try this [http://ubuntuforums.org/showpost.php?p=2513159&postcount=4]("http://ubuntuforums.org/showpost.php?p=2513159&postcount=4")

Yeah, adding IRQPOLL helped me.

---

### Post by pravinba on 2007-07-25
Hi ppl,

I too have the same problem while trying to install. Was really happy to see a solution. Am a newbie to LINUX. Can someone please help me on how to add irqpoll to kernel line ? Would really appreciate your help.

Thanks,
Pravin

---

### Post by thomasvdb on 2008-01-15
> **amosharper said:**
> Yeah, adding IRQPOLL helped me.[FONT="Tahoma"]Yes indeed, it did the trick![/FONT]

---

### Post by Skneepa on 2008-01-18
Had a similar issue while trying to install Feisty...I managed to overcome it by getting help from this forum, they suggested adding the line 'all_generic_ide'  on menu.lst in the kernell line...

Something like that:
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash all_generic_ide

In 7.10 installation went on without any problems but the issue shows up randomly when i restart or power on my pc. 

I did however add the 'all_generic_ide' line on the grub menu and 7.10 started with no problems 4 times in a row. I ll watch and post back.

ButI cannot remember how to add this or the irqpoll lines to my menu.lst...So please post the correct way to do that! :(

---

