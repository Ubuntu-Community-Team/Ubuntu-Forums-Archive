---
title: "[SOLVED] Dosbox and Borland Turbo C++"
date: 2008-07-08
forum: General Help
---

### Post by ashmew2 on 2008-07-08
Hi people , I need to run Borland Turbo C++ (TC.exe) on my Ubuntu 8.04 . 
I installed Dosbox , but whenever i try to run tc.exe , dosbox just quits. Please help me ! And i do not want any other IDEs, i know there are plenty like g++ but i need the Borland one because they are using the same one in school. I can use it in a Windows Virtual Machine but i dont want to. Anyone ? Any suggestions for running it via dosbox ?
Thanks.

---

### Post by bazcor on 2008-07-08
Have you tried dosemu?

---

### Post by Rick Myers on 2008-07-08
How about trying a virtual machine (VM) like virtualbox? It'll do DOS!

---

### Post by ashmew2 on 2008-07-08
> **Rick Myers said:**
> How about trying a virtual machine (VM) like virtualbox? It'll do DOS!

Thanks for the pointer but i already mentioned in my post that i CAN do it but i do not want to.

[QUOTE=ashmew2]I can use it in a Windows Virtual Machine but i dont want to.[/QUOTE]

---

### Post by ashmew2 on 2008-07-08
> **bazcor said:**
> Have you tried dosemu?

Tried DosEmu , but when i try to run tc.exe it gives me :


Invalid Opcode at FFEC 0298 0202 0000 20CD 9FFF 9A00 FEF0 F01D 095D C453 07C6 C443

Im still clueless :-(

---

### Post by ashmew2 on 2008-07-11
Well Got it Working , DBoxFE Rocks !! Its a GUI for Dosbox AND it fixed the problem :)

---

### Post by peyre on 2009-03-30
> **ashmew2 said:**
> Well Got it Working , DBoxFE Rocks !! Its a GUI for Dosbox AND it fixed the problem :)

How did you get DBoxFE installed?  It errors out on my system.

---

### Post by ashmew2 on 2009-04-07
Hello peyre. 
Which release are you using ? and is it 64 Bit or 32 bit ?
I am pretty sure that on a 32 Bit/x86 , you can get Turbo C++ running in Dosbox flawlessly.
Fill me on the details and we'll take a look!

PS - Nice Geocities page with the "Buzz Aldrin's Race to Space" game.. and nice work with the docs.

Cheers!

---

### Post by peyre on 2009-04-07
Thanks!!  That page was a labor of love.  You're aware, I assume, that they've ported the game to Windows, Mac, and *nix?

I'm running the 32-bit version.  When I get home I can check to see if Turbo C++ is running, if you like.  Any other info you need, let me know.

Edit: I've looked for it in Synaptic, but don't see it there.  I probably just need to know how to find it...

> **ashmew2 said:**
> Hello peyre. 
Which release are you using ? and is it 64 Bit or 32 bit ?
I am pretty sure that on a 32 Bit/x86 , you can get Turbo C++ running in Dosbox flawlessly.
Fill me on the details and we'll take a look!

PS - Nice Geocities page with the "Buzz Aldrin's Race to Space" game.. and nice work with the docs.

Cheers!

---

### Post by ashmew2 on 2009-04-09
> **peyre said:**
> Thanks!!  That page was a labor of love.  You're aware, I assume, that they've ported the game to Windows, Mac, and *nix?

I'm running the 32-bit version.  When I get home I can check to see if Turbo C++ is running, if you like.  Any other info you need, let me know.

Edit: I've looked for it in Synaptic, but don't see it there.  I probably just need to know how to find it...

Hi , May i ask why do u want DBoxFE exactly ? Is Dosbox not running optimally at your end ? Anyhow , you need to compile DBoxFE from source ( I think u know that :P) , so as far as i remmeber ,if its a dependency issue , installing qt4-core should help it compile without errors. I dont have access to a Ubuntu machine right now , been stuck in Vector Linux lol..Try that and get back to me , Ill try and get my ubuntu up again.

I read it on your site that it was ported to *nix and Mac. :D weeeeeeeeeeee...

PS - Why dont you add the link to your geocities page in your signature ?

---

### Post by peyre on 2009-04-09
> **ashmew2 said:**
> Hi , May i ask why do u want DBoxFE exactly ? Is Dosbox not running optimally at your end ? Anyhow , you need to compile DBoxFE from source ( I think u know that :P) , so as far as i remmeber ,if its a dependency issue , installing qt4-core should help it compile without errors. I dont have access to a Ubuntu machine right now , been stuck in Vector Linux lol..Try that and get back to me , Ill try and get my ubuntu up again.

I read it on your site that it was ported to *nix and Mac. :D weeeeeeeeeeee...

PS - Why dont you add the link to your geocities page in your signature ?

DOSBox is running fine for most of the DOS programs I've tried so far, but some of them need non-default settings.  And if I'm going to have to tweak settings for some of them, I'd really rather do that in a GUI than work with command-line switches etc.  Besides, it's much nicer to have a list of my DOS programs and be able to open any of them with a double-click.  Not necessary, just much nicer.

Yeah, Race Into Space seems to run well on Ubuntu, anyway, although it has to be compiled from source and it's not completely straightforward (though if you read the discussions I started about compiling it, you can make out what extra steps you need to take).

Hmm, maybe I should add the link.  It's hard sometimes to choose which fan site to put in my signature though: BARIS, Master of Orion, Machiavelli the Prince, or GW-BASIC games.

I'll install qt4-core, if it's not there already, and get back to you.

---

