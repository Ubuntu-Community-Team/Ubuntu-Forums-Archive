---
title: "Dual Boot - Can't access Ubuntu"
date: 2014-10-15
forum: General Help
---

### Post by BNZBKK on 2014-10-15
Ubuntu 12. is installed alongside Windows but now after 'arrowing' to Ubuntu I get a 'No Signal' and a dark screen 

I can access BIOS etc but where do I start  - to trigger it back up again ?

---

### Post by Vladlenin5000 on 2014-10-15
What Ubuntu release? 12. is meaningless... It's either 12.04 LTS (supported) or 12.10 (EoL = unsupported)
Which graphics card/chip?

---

### Post by BNZBKK on 2014-10-15
Thanks for your prompt reply ..it's 12.04 LTS 

Graphics card / chip ? I have no idea but here's the only info I have..

[h=1]Acer eMachines EL1358 Desktop PC (AMD Athlon II 220 X2 Processor,[/h]
[TABLE="width: 605"]
[TR]
[TD="class: label, bgcolor: #F5F5F5"]Processor Brand[/TD]
[TD="class: value"]AMD[/TD]
[/TR]
[TR]
[TD="class: label, bgcolor: #F5F5F5"]Processor Type[/TD]
[TD="class: value"]Athlon 64 X2[/TD]
[/TR]
[TR]
[TD="class: label, bgcolor: #F5F5F5"]Processor Speed[/TD]
[TD="class: value"]2.8 GHz[/TD]
[/TR]
[TR]
[TD="class: label, bgcolor: #F5F5F5"]RAM Size[/TD]
[TD="class: value"]2 GB[/TD]
[/TR]
[TR]
[TD="class: label, bgcolor: #F5F5F5"]Hard Drive Size[/TD]
[TD="class: value"]320 GB[/TD]
[/TR]
[TR]
[TD="class: label, bgcolor: #F5F5F5"]Graphics Card Description[/TD]
[TD="class: value"]None[/TD]
[/TR]
[/TABLE]

---

### Post by yancek on 2014-10-15
You have Ubuntu 12.04 and which windows?  Can you boot windows?  Do you get this immediately on boot or after selecting to boot Ubuntu?  Is this a new install of Ubuntu or have you been using it successfully for a time?

---

### Post by Mark Phelps on 2014-10-15
HOW did you install Ubuntu -- "alongside" doesn't give us much information.

Also, to see what video chipset you have, boot into Ubuntu install media, select Try Ubuntu, and when you get to a desktop, open a terminal, enter "lspci" (without the quotes) and look for the line containing "VGA" -- and post that line back here.

---

### Post by BNZBKK on 2014-10-15
> **yancek said:**
> You have Ubuntu 12.04 ..and which windows? 
 Can you boot windows? 
 Do you get this immediately on boot or after selecting to boot Ubuntu? 
 Is this a new install of Ubuntu or have you been using it successfully for a time?


1. Windows Premium 7

2. I'm utilizing Windows now

3. after selecting to boot to Ubuntu

4. I've been using it successfully for nearly two years

---

### Post by BNZBKK on 2014-10-15
> **Mark Phelps said:**
> HOW did you install Ubuntu -- "alongside" doesn't give us much information.

Also, to see what video chipset you have, boot into Ubuntu install media, select Try Ubuntu, and when you get to a desktop, open a terminal, enter "lspci" (without the quotes) and look for the line containing "VGA" -- and post that line back here.

1. How many choices does one have when installing a Linux OS in a machine that's already running Windows ? This is a 'General Help' forum 

2. Where is 'Ubuntu install media'  Please advise - remembering that I can't boot into Ubuntu

---

### Post by yancek on 2014-10-15
> Where is 'Ubuntu install media'  Please advise - remembering that I can't boot into Ubuntu 		

That was posted prior to your post indicating you have had it installed for two years so assuming this was a new install.  The number of choices varies, depends on what is installed but usually 2-5 choices.  Since you don't want to install it doesn't really matter.  Something like that should not happen for no reason and since you can use windows I expect it is not a hardware problem.  Had you made any changes to hardware/software just prior to this problem?  I've seen this on new installs and needed to edit a line in the /etc/default/grub although I don't see how that could be the problem if you've been using it all this time.

---

### Post by BNZBKK on 2014-10-15
> **yancek said:**
>   ...Had you made any changes to hardware/software just prior to this problem?  ...

Yes, I was trying to download some video from my portable HD into the desktop and encountered a notice ' No space available' in the desktop which is an error as this desktop probably contains 20GB at most ! ..out of a 320GB capacity

---

### Post by BNZBKK on 2014-10-16
Anybody ?

---

### Post by BNZBKK on 2014-10-16
What if I 'Uninstall' Ubuntu via Windows / Control Panel / Uninstall ?

Will it 'uninstall' cleanly ? 

...thereby freeing up that space in the computer thence allowing me to Install 14.LTS ?

---

### Post by Vladlenin5000 on 2014-10-16
> **BNZBKK said:**
> What if I 'Uninstall' Ubuntu via Windows / Control Panel / Uninstall ?

Is it a Wubi installation then?
Sorry, that's no longer supported and for good reasons. Even when it was supported the purpose was for testing ONLY.

---

### Post by BNZBKK on 2014-10-16
Thank you for your prompt reply Vladimir Hitchens but I don't know what a 'Wubi' installation is

I can see Ubuntu in the Control Panel, will it uninstall cleanly ?

---

### Post by yancek on 2014-10-16
The link below to the actual wubi site explains how to uninstall it.  Your not going to free up any space really as it is all inside your windows partition.  As mentioned above, it is not supported any longer and although some people have got it to work, it is not expected to.  If you don't want to install Ubuntu on a separate partition, you could install VirtualBox on windows and run Ubuntu from that.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by BNZBKK on 2014-10-16
Why do I need to install Wubi to uninstall when I can see Ubuntu[COLOR=#000000] in the Control Panel and with a 'Right' click can 'Uninstall' it ?[/COLOR]

---

### Post by Vladlenin5000 on 2014-10-16
Nobody said you need to install Wubi. Actually Wubi.exe is the installer you used in the first place. The guide linked also explains how to uninstall.

---

### Post by BNZBKK on 2014-10-16
I'm not understanding this ..did/does Wubi insert itself to install Ubuntu - unbeknownst to me ?

From memory I installed Ubuntu from a USB - without partitioning - into the computer - 'alongside' Windows

---

### Post by Vladlenin5000 on 2014-10-16
If there's Ubuntu in your Windows control panel _then_ it _must_ come from an installation you did _inside_ Windows by running Wubi.exe, just like any other Windows software.

---

### Post by BNZBKK on 2014-10-16
Yes Wubi is in there, thanks gentlemen  ..I'll give it a try

---

