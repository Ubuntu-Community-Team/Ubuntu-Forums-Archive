---
title: "Sometimes it doesn't boot"
date: 2007-06-04
forum: General Help
---

### Post by miLl3niUm on 2007-06-04
I start my computer, I wait for few seconds and then I see that.... how do you call it? GURU or GUBU menu to select operating system to boot. Sometimes when I select "*ubuntu*.16*" I see ubuntu logo and a line (below it)-(as usual). The line stops and I see a black screen with an underscore (_) flashing. It's not like CMD, I cannot use any commands......

...........I bet that most of you didn't understand what I mean, hope you can help.
Thank you :D

EDIT: I formatted my drive more than 5 times (with ubuntu). All of them were with the LiveCD. The last time I installed ubuntu was with the text installation wizard. At the last step I chose to install GURU (or GUBU, not sure)-(to select an operating system). How can I uninstall it?

---

### Post by miLl3niUm on 2007-06-04
Anyone?

---

### Post by rax_m on 2007-06-04
What kind of computer do you have?

I had a similar problem with Edgy and I what I found was that I must have my wireless card enabled when booting. I have a switch on the front of my laptop to turn my wireless on/off. If it's turned off every 2nd or 3rd boot would freeze. 

If that's not the issue then I guess you'll have to give a bit more info about what version of Ubuntu, machine details, log files etc. 


PS I think you're referring to the GRUB menu :)

---

### Post by rax_m on 2007-06-04
Oh yeah.. as soon as you see the Ubuntu loading screen you can hit Ctrl-Alt-F1 together and it should show you what is being loaded. That may give a better idea to where the freeze is ocurring.

---

### Post by miLl3niUm on 2007-06-04
> **rax_m said:**
> What kind of computer do you have?

I had a similar problem with Edgy and I what I found was that I must have my wireless card enabled when booting. I have a switch on the front of my laptop to turn my wireless on/off. If it's turned off every 2nd or 3rd boot would freeze. 

If that's not the issue then I guess you'll have to give a bit more info about what version of Ubuntu, machine details, log files etc. 


PS I think you're referring to the GRUB menu :)

I use desktop computer and latest version of Ubuntu (feisty 7.04). My father connects to the internet at his laptop from the router. What other info do you want?
About GRUB, I have 4 options for Ubuntu. Here is the list (I don't remember exactly):
ubuntu....16
ubuntu....16 (recovery mode)
ubuntu....15
ubuntu....15 (recovery mode)

How can I delete the one with 15? (16 was created after an update which restart was needed)

> **rax_m said:**
> Oh yeah.. as soon as you see the Ubuntu loading screen you can hit Ctrl-Alt-F1 together and it should show you what is being loaded. That may give a better idea to where the freeze is ocurring.

When I select Ubuntu in GRUB menu, I see "starting up...." and then the loading screen. When I press alt+alt+f1 I see again "starting up..."

---

### Post by Crafty Kisses on 2007-06-04
> **miLl3niUm said:**
> I start my computer, I wait for few seconds and then I see that.... how do you call it? GURU or GUBU menu to select operating system to boot. Sometimes when I select "*ubuntu*.16*" I see ubuntu logo and a line (below it)-(as usual). The line stops and I see a black screen with an underscore (_) flashing. It's not like CMD, I cannot use any commands......

...........I bet that most of you didn't understand what I mean, hope you can help.
Thank you :D

EDIT: I formatted my drive more than 5 times (with ubuntu). All of them were with the LiveCD. The last time I installed ubuntu was with the text installation wizard. At the last step I chose to install GURU (or GUBU, not sure)-(to select an operating system). How can I uninstall it?

You can try booting in verbose mode, and the screen before it freezes, press:
```
Ctrl+Alt+F2
```
You can see if any errors are visible.

---

### Post by miLl3niUm on 2007-06-05
> **Codename said:**
> You can try booting in verbose mode, and the screen before it freezes, press:
```
Ctrl+Alt+F2
```
You can see if any errors are visible.

How can I boot in verbose mode?
When do I have to press Ctrl+Alt+F2? The loading bar has many small boxes. If the first or second (sometimes) small box gets full and then it doesn't continue, it'll show me that black screen. Do I have to press it few seconds before the black screen appears?

EDIT: I think I can boot in verbose with Esc, right?

---

### Post by scott_g on 2007-06-05
If this happens regularily, you could also try to boot in recovery mode (should be an option on the GRUB menu).  Recovery mode lets you boot to a command prompt; no graphical display at all.

Does the bar stop and sit there?

Is your CPU appear to be in use when it is stuck?

Good luck,
Scott

---

### Post by Crafty Kisses on 2007-06-06
> **scott_g said:**
> If this happens regularily, you could also try to boot in recovery mode (should be an option on the GRUB menu).  Recovery mode lets you boot to a command prompt; no graphical display at all.

Does the bar stop and sit there?

Is your CPU appear to be in use when it is stuck?

Good luck,
Scott

That's another option too.

---

### Post by miLl3niUm on 2007-06-06
> **scott_g said:**
> If this happens regularily, you could also try to boot in recovery mode (should be an option on the GRUB menu).  Recovery mode lets you boot to a command prompt; no graphical display at all.

Does the bar stop and sit there?

Is your CPU appear to be in use when it is stuck?

Good luck,
Scott

> **Codename said:**
> That's another option too.

No, the bar stops for a few seconds (2 min - 7 max). Then a black screen appears with an underscore flashing (_). About the CPU I'm not sure where I can see it. On the tower there are two lights. A green one is on while the computer is on. The other is orange I think and it's on (most times flashes) when I open I program, file or something. If you mean this, yes it stops.

---

### Post by scott_g on 2007-06-06
Also: if the cpu light stayed on, it would mean it was frozen (it has happened to me before; it said it was a spinlock error, but that doesnt seem to be your problem).

Can you try to start it in recovery mode and see what line it stops at?

Scott

---

### Post by miLl3niUm on 2007-06-06
> **scott_g said:**
> Also: if the cpu light stayed on, it would mean it was frozen (it has happened to me before; it said it was a spinlock error, but that doesnt seem to be your problem).

Can you try to start it in recovery mode and see what line it stops at?

Scott

Do you mean what box it stops?

PS: I think it doesn't stuck at recovery mode.

---

### Post by scott_g on 2007-06-06
> **miLl3niUm said:**
> Do you mean what box it stops?

PS: I think it doesn't stuck at recovery mode.

I think he means the loading bar during a graphical boot.

---

### Post by miLl3niUm on 2007-06-06
> **scott_g said:**
> I think he means the loading bar during a graphical boot.

Rofl, wtf? You said that, not another guy. Thanks anyway, I am "studying" for exams now. I'll check it later.

---

### Post by scott_g on 2007-06-06
> **miLl3niUm said:**
> Rofl, wtf? You said that, not another guy. Thanks anyway, I am "studying" for exams now. I'll check it later.

I know, I was just saying what I interpreted the question as.  Exams eh?  I should start studying too...  what subject?

Scott

---

### Post by miLl3niUm on 2007-06-07
It boots normally in recovery mode.

---

