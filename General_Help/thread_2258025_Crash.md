---
title: "Crash"
date: 2014-12-24
forum: General Help
---

### Post by pingo-power on 2014-12-24
Hello, please, thanks, bye !  It's the end of the world !  When i boot on Win 8.1 he crash with a blue screen after the 4 blue square, when i boot with the liveCD of Ubuntu or Ubuntu in the PC i have this error :  [[img]http://image.noelshack.com/minis/2014/52/1419333078-img-0267.png[/img]](http://www.noelshack.com/2014-52-1419333078-img-0267.jpg)  (Here in this case it's a picture of the error message boot Ubuntu system 14.10)  What i should do ?

---

### Post by schragge on 2014-12-24
Please have a look at [thread=2230101]this thread[/thread], and follow the links from there, especially [the Wikipedia article on MCE]("http://en.wikipedia.org/wiki/Machine-check_exception").
I've run the error message through *mcelog --ascii* like suggested in the screenshot. The result:
```

Hardware event. This is not a software error.
CPU 0 BANK 1 TSC 1721b44be3 
RIP !INEXACT! 10:ffffffff81670493
MISC 86 ADDR 2335c2880 
TIME 1419332504 Tue Dec 23 12:01:44 2014
MCG status:RIPV MCIP 
MCi status:
Uncorrected error
Error enabled
MCi_MISC register valid
MCi_ADDR register valid
Processor context corrupt
SRAR
MCA: Data CACHE Level-0 Write Error
STATUS bf80000000000124 MCGSTATUS 5
RIP: skb_release_data+0x63/0x100
CPUID Vendor Intel Family 6 Model 60
SOCKET 0 APIC 0 microcode 19

```

And please run *memtest* from the boot menu. [Here]("http://www.newegg.com/Product/SingleProductReview.aspx?ReviewID=3882223") is a motherboard manufacturer response to a similar error:
> 
We sincerely apologize for any inconvenience this may have caused you. Is the system having stability issue?
Please test with single memory module, try with another memory if problem still persist.


[thread=2252207]Another forum thread[/thread] with similar issues. Try to boot your PC with the case open and a room fan blowing at it as suggested there, check that the CPU fan/heatsink fits properly and memory modules firmly sit in their slots.

---

### Post by pingo-power on 2014-12-24
Hum, im french and i don't understand a lot, globaly u want a memtest ? memtest don't return any error [http://www.noelshack.com/2014-52-1419427192-photo.jpg](http://www.noelshack.com/2014-52-1419427192-photo.jpg)

---

### Post by schragge on 2014-12-24
> **pingo-power said:**
> Hum, im french and i don't understand a lot So much the better. The OP in the thread linked above is also French and he found a solution to his problem at [the French-speaking Ubuntu forum]("http://forum.ubuntu-fr.org/viewtopic.php?id=1606381"). You probably won't have any trouble understanding what that solution was about.

I edited my previous post. Have you tried other things suggested there?

---

### Post by pingo-power on 2014-12-24
French forum have no reponses, you ask me to check connect of composant of my PC ? Everithing is ok, what i should do to boot on windows and linux ?

---

### Post by schragge on 2014-12-24
> **pingo-power said:**
> French forum have no reponses
I thought this to be a response:
> Edit : n'ayant plus eu de problème depuis que j'ai suivi les étapes C 1-2-3-4 du tuto de nam1962 ([http://forum.ubuntu-fr.org/viewtopic.php?pid=15041961]("http://forum.ubuntu-fr.org/viewtopic.php?pid=15041961#p15041961")), je considère que le problème est résolu !

> you ask me to check connect of composant of my PC ?
Yep. Especially, the CPU and the DIMMs.

> what i should do to boot on windows and linux ?
Replace memory modules. If this doesn't help, replace the CPU.

---

### Post by pingo-power on 2014-12-24
My CPU is a i5 4670k and i have 2x4Go Corsair Vangeance, you want i trash them ?

---

### Post by schragge on 2014-12-24
Look, there are many possible causes for a hardware-related machine-check exception. You say all components are properly connected and there are no memory errors. Then it could be an overloaded power supply or an overheated CPU or something else. You should find out why it's overloaded or overheated. It may be just some dust gathered in the CPU fan or it may be something much more serious.

---

### Post by pingo-power on 2014-12-24
It's a new pc and he have 35-37° for processor, you have an idea to what to do ?

---

### Post by schragge on 2014-12-24
Look at [this Microsoft response]("http://answers.microsoft.com/en-us/windows/forum/windows_7-system/bsod-code-124/9c4da612-000a-47e1-abac-7f08c64f6191"). The MCA error code you got is 0124. Intel mnemonic for it is DCACHEL0_WR_ERR. *mcelog* describes it like *MCA: Data CACHE Level-0 Write Error*. Kernel has panicked while executing the function *skb_release_data*. That's all I know. Try to google these values to find out what may have caused this error.

---

### Post by pingo-power on 2014-12-24
So i could go to a windows forum for explain of this crash ?

---

### Post by schragge on 2014-12-24
The crash is neither Windows nor Ubuntu/Linux related. It's **hardware**-related. Yes, you could go to a Windows forum, too. Obviously, you should show them the contents of BSOD, not the Linux kernel messages. I'll quote here the response from Microsoft linked above:
> 
**1.** That is likely to be the processor, the heat sink, or even the compound between them. And it could even be other hardware such as the motherboard. If over-clocking STOP. Inspect those and replace the compound.

**2.** Remove ALL power then reseat the cards, memory, and cables (on both ends when possible) - actually remove and replace - do not just snug. Carefully inspect the motherboard and other cards for damage. Clean out the dust bunnies, clear the vents, and ensure all the fans are working. Try adding a small fan blowing into the intake to see if that helps (heat related does not always mean excessive heat since a single component could be too sensitive to even the normal levels of heat). 

**3.** Check with your System maker's Support, their on-line documentation and drivers, and ask in their forums about any known issues. Update the BIOS, low level chipset drivers, and the major on-board and separate device drivers


---

### Post by pingo-power on 2014-12-24
I have reset my bios, and everything works, windows and ubuntu, but "entre temps" (i can't translate this word), i installed a new windows because i think that was the problem, so i have a new windows and the ubuntu normal.

Thanks ! :)

---

### Post by schragge on 2014-12-24
Glad you've got it figured out!

> entre tempsLet me see... *meanwhile*?

---

### Post by pingo-power on 2014-12-24
Maybe, i want o say "when i try to repair the problem"

---

