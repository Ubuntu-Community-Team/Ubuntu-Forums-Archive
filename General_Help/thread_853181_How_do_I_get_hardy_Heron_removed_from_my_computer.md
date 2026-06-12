---
title: "How do I get hardy Heron removed from my computer?"
date: 2008-07-08
forum: General Help
---

### Post by DiamondJim on 2008-07-08
I need some help. Yesterday I downloaded Hardy Heron and burned the cd. Tried to install by booting up with the cd in the drive. No success. Then used Win Explorer to view the contents and found the Wubi installer. Used that and now I have Vista booting to the boot option of Ubuntu or Vista. 

Ubuntu will not run. Have tried to uninstall - to no avail. Have used System Restore - no effect on removing Ubuntu! Unbelievable!

My system consists of Quad core cpu, 4 GB ram, Vista Home Premium SP1. My primary hard drive is 500GB - partitioned into "C" of 50GB and "D" of the rest. I expected Ubuntu to be installed on "C" - but can find no indication of that. I've found on "D" drive the Ubuntu directory. There, I've found the Uninstall.exe for uninstalling Ubuntu - that does absolutely nothing!!! 

How do I remove Ubuntu completely from my drive **[COLOR="Red"]and[/COLOR]** revert my bootup to the normal Vista **[COLOR="red"]without[/COLOR]** the Ubuntu option?

Anyone who can assist me in this has my undying gratitude!

Thank you very much,

Jim McCants

---

### Post by overdrank on 2008-07-08
> **DiamondJim said:**
> I need some help. Yesterday I downloaded Hardy Heron and burned the cd. Tried to install by booting up with the cd in the drive. No success. Then used Win Explorer to view the contents and found the Wubi installer. Used that and now I have Vista booting to the boot option of Ubuntu or Vista. 

Ubuntu will not run. Have tried to uninstall - to no avail. Have used System Restore - no effect on removing Ubuntu! Unbelievable!

My system consists of Quad core cpu, 4 GB ram, Vista Home Premium SP1. My primary hard drive is 500GB - partitioned into "C" of 50GB and "D" of the rest. I expected Ubuntu to be installed on "C" - but can find no indication of that. I've found on "D" drive the Ubuntu directory. There, I've found the Uninstall.exe for uninstalling Ubuntu - that does absolutely nothing!!! 

How do I remove Ubuntu completely from my drive **[COLOR="Red"]and[/COLOR]** revert my bootup to the normal Vista **[COLOR="red"]without[/COLOR]** the Ubuntu option?

Anyone who can assist me in this has my undying gratitude!

Thank you very much,

Jim McCants

Hi and I believe you uninstall Wubi through add and remove programs. If you check out the FAQ's at Wubi site I am sure it can help.

---

### Post by kaola_linux on 2008-07-08
> **DiamondJim said:**
> I need some help. Yesterday I downloaded Hardy Heron and burned the cd. Tried to install by booting up with the cd in the drive. No success. Then used Win Explorer to view the contents and found the Wubi installer. Used that and now I have Vista booting to the boot option of Ubuntu or Vista. 

Ubuntu will not run. Have tried to uninstall - to no avail. Have used System Restore - no effect on removing Ubuntu! Unbelievable!

My system consists of Quad core cpu, 4 GB ram, Vista Home Premium SP1. My primary hard drive is 500GB - partitioned into "C" of 50GB and "D" of the rest. I expected Ubuntu to be installed on "C" - but can find no indication of that. I've found on "D" drive the Ubuntu directory. There, I've found the Uninstall.exe for uninstalling Ubuntu - that does absolutely nothing!!! 

How do I remove Ubuntu completely from my drive **[COLOR="Red"]and[/COLOR]** revert my bootup to the normal Vista **[COLOR="red"]without[/COLOR]** the Ubuntu option?

Anyone who can assist me in this has my undying gratitude!

Thank you very much,

Jim McCants

hi my friend...I'm new here also but I do know to remove it...use a software like Acronis Disk Director or anything that has the same feature as it is because the have an option on deleting partions EVEN ON WINDOWS!!! Tell my your progress then..I had tried this with success, after that your grub menu will be having an error which won't let you boot, if your using Vista I'm sure it can delete the MBR contents to default..Hope that helps...

---

### Post by DiamondJim on 2008-07-08
Overdrank - I tried that first. Nothing at all happened. 
Thanks!

Jim

---

### Post by DiamondJim on 2008-07-08
Kaola_linux - it is not partioned. It is in a directory on "D" drive as "Ubuntu". 

BTW - now it doesn't even show up in the Add/Remove of Vista. But, the bootup is still a dual bootup of Vista and Ubuntu. All of the files for Ubuntu are still in the directory. I can just delete the directory - that's no problem. The problem is this - how do I remove the dual bootup option from Vista?

I want to see my standard boot when I turn the computer on.

Thanks!

Jim

---

### Post by ChameleonDave on 2008-07-08
> **DiamondJim said:**
> 

BTW - now it doesn't even show up in the Add/Remove of Vista.

I suspect very much that that is because of your System Restore.

Perform another System Restore, putting the computer back as it was before the first one.

You should then be able to find Wubi Ubuntu in Add or Remove Programs.

This thread ought to be moved to the Wubi forum, where people will be more knowledgeable.

---

### Post by kaola_linux on 2008-07-08
Oh I see...so u've installed Ubuntu insde Vista? Sorry, it was not clear to me...:)

U can use a program called vista boot pro..I'm not sure how they call it coz u can edit the vista boot menu there..Then, jst delete the ubuntu entry there and delete manually the ubuntu files on your drive on safe mode if you can't on normal mode..cheers!!!.hope that helps

---

### Post by kaola_linux on 2008-07-08
[http://www.vistabootpro.org/](http://www.vistabootpro.org/)

here's a link of the software I'm referring to on editing your boot menu on vista..hope that helps...I'm on windows now, I had a thread here also...hehe..My ubuntu is broken, gonna fix it soon...

---

### Post by DiamondJim on 2008-07-08
Kaola_linux -- I've downloaded and run VistaBootPro and using it I'm able to see the part of bootup that loads the Ubuntu option. What I don't understand is how to get that part out! Any help?

Jim

---

### Post by kaola_linux on 2008-07-08
> **DiamondJim said:**
> Kaola_linux -- I've downloaded and run VistaBootPro and using it I'm able to see the part of bootup that loads the Ubuntu option. What I don't understand is how to get that part out! Any help?

Jim

Here is a forum that explains that coz I don't have the chance of using Vista...
[http://www.pronetworks.org/forum/about89653-0.html](http://www.pronetworks.org/forum/about89653-0.html)
Good Luck

---

