---
title: "How to reach the operating system"
date: 2013-06-10
forum: General Help
---

### Post by TheWomanWhoLivesInAShoe on 2013-06-10
Yesterday GRUB fell back into command-line mode which I can't operate. How can I start Ubuntu from this mode to repair GRUB?

---

### Post by Lars Noodén on 2013-06-10
If you still have the installation CD or DVD, one of the options there is to use the rescue utilities to fix Grub.  I'd try that.

---

### Post by TheWomanWhoLivesInAShoe on 2013-06-10
I'll try it.
EDIT: I can't find the rescue utilities on the LiveCD. I use 12.10

---

### Post by Bucky Ball on 2013-06-10
Welcome to the forums.

When you boot and it drops to the command line (rather than the login in window), as I'm presuming it is doing, trying typing:

 ```
startx
```
 Anything?

At the command, you can also try:

```
sudo update-grub
```

... then reboot. Let us know what happened with both these things and we'll move on.

PS: Did this happen after doing something specific? Did you do an update yesterday? Were you launching a program? 
PPS: Must be a big shoe. ;)

---

### Post by zombifier25 on 2013-06-10
He stated that he was dropped into Grub's command line, which is about as helpful as a rock.

Like Lars said, if you still have the Live CD or USB, boot into it. Boot-Repair is a pretty good tool at fixing Grub problems. Install it:
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install boot-repair
```

Then launch Boot-Repair, choose "Recommended Repair" and sit back.

More info here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Bucky Ball on 2013-06-10
> **zombifier25 said:**
> He stated that he was dropped into Grub's command line, which is about as helpful as a rock.

TheWomanWhoLivesInAShoe is a he??? 

Be aware: The forums are not gender specific and cater for all genders. There are many females forum users, including staff, so best to address other users by something gender-neutral if you have no idea which gender they are. (OP = original poster/original post is good.)

The forums cater for all nationalities, therefore English is not a first language for some users. This can often be what causes confusion and a lack of clarity. The majority of users do not intend to be unclear, they're here to get help. New users can also be unsure about how to post effectively until the get to know the ropes. ;)

---

### Post by grahammechanical on 2013-06-10
I would like a bit more clarity. Do you get a Grub menu at all? Or do you get put straight to grub rescue prompt without seeing a grub menu. A grub rescue prompt is a way of telling us that grub is broken.

If you get a grub menu and you are using 12.10 do you see Advanced Options for Ubuntu? If so select that and select to boot Ubuntu recovery mode. At the recovery mode screen select Resume. Try that and tell us what happens. If you get to a working desktop you might try selecting a different video driver.

If you can get into Advanced Options you might try booting into one of the previous kernel listed there.

As far as I know we only get a grub command line when we press c at the grub menu. We get the ability to edit boot parameters when we press e at the grub menu. I have experienced getting a grub rescue prompt and I have used both grub edit mode and command line but I have not been put, unwanted, into a grub command line before. I have had Ubuntu load and been put into a Linux command line and even just a flashing cursor on a black screen. I am getting that at the moment with an experimental installation of saucy salamander. So, perhaps you can see why I need clarification about the actual state of affairs.

Regards.

---

### Post by zombifier25 on 2013-06-11
> **Bucky Ball said:**
> TheWomanWhoLivesInAShoe is a he??? 

Be aware: The forums are not gender specific and cater for all genders. There are many females forum users, including staff, so best to address other users by something gender-neutral if you have no idea which gender they are. (OP = original poster/original post is good.)

The forums cater for all nationalities, therefore English is not a first language for some users. This can often be what causes confusion and a lack of clarity. The majority of users do not intend to be unclear, they're here to get help. New users can also be unsure about how to post effectively until the get to know the ropes. ;)

Heheheh, my bad. Since English does not have any gender-neutral pronouns, I usually default to "he" (of course, that does not explain how I could have missed OP's username) [color=white]not taking any chances here[/color]

---

