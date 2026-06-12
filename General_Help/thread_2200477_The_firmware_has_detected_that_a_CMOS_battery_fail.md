---
title: "The firmware has detected that a CMOS battery failure occurred"
date: 2014-01-19
forum: General Help
---

### Post by amjjawad on 2014-01-19
Hi,

Toshiba Satellite Laptop

```
The firmware has detected that a CMOS battery failure occurred. Press <F1> to continue. 
```

Monitor is totally black, nothing whatsoever. However, the machine is working, I can head everything, Fan, HDD, etc.

If I connect the laptop to an external monitor, I do see the above message. That is the only way I can 'see' something as of now.

Pressing F1 does nothing at all. There is no further point after this message. The machine sits there doing nothing.
[U][B]
Things I have tried:[/B][/U]
[LIST=1]
[*]Used Air-Blower to clean the machine.
[*][COLOR=#ff0000]_Bought **new** battery and changed it already._[/COLOR]
[*]Took the RAMs out, turned the machine on - nothing - and put them back in.
[*]Took the HDD out, turned the machine on - nothing - and put them back in.
[*]Tried to search for that message but all the results are useless.
[/LIST]

Nothing from the above steps changed anything yet.
Any idea how to solve this?!

Thanks in advance!

---

### Post by tgalati4 on 2014-01-19
Normally when your BIOS battery dies, you lose BIOS settings like date and time and any custom settings in BIOS.  Sometimes graphics uses shared RAM.  If you can boot to BIOS, check for video RAM and set it to a larger value than default.  Then save the BIOS settings and reboot.

It's possible that you have a failed backlight inverter.  Can you see any images if you hold a light up close to the laptop screen?  Perhaps the screen works but the backlight is not lit.  You would see a faint image if you hold a light up close.  If you see nothing, then it's possible that you have a graphics chip failure.  Delamination of graphics chips is common.  Do a web search for your specific model of laptop and see if others are having the same problem.

The CMOS battery message and screen failure may just be a coincidence--especially on an older machine.  It's possible that you had a chip delamination which then caused the motherboard to short, draining the battery.  Sort of like grandma falling and breaking her hip.  Usually it is the other way around.  Grandma's hip breaks (due to osteoporosis) and she falls because it happens so suddenly.

Try some of these things:  [http://www.youtube.com/watch?v=NAsrhpOK2Qc](http://www.youtube.com/watch?v=NAsrhpOK2Qc) Spoiler Alert:  bad keyboard prevents booting.

---

### Post by amjjawad on 2014-01-20
Hi and thanks for posting :)

> **tgalati4 said:**
> Normally when your BIOS battery dies, you lose BIOS settings like date and time and any custom settings in BIOS.  Sometimes graphics uses shared RAM.  If you can boot to BIOS, check for video RAM and set it to a larger value than default.  Then save the BIOS settings and reboot.
It can't be done because I can't enter the BIOS :(
Whenever I hit F2, it gives me the same message and sometimes a beep before that and again the same message as in the subject/title of this thread.

> It's possible that you have a failed backlight inverter.  Can you see any images if you hold a light up close to the laptop screen?  Perhaps the screen works but the backlight is not lit.  You would see a faint image if you hold a light up close.  If you see nothing, then it's possible that you have a graphics chip failure.  Delamination of graphics chips is common.  Do a web search for your specific model of laptop and see if others are having the same problem.
That was one of the things I have checked already but there is nothing at all. Search on Google didn't bring much. As I mentioned, when I connect it to an external monitor, I can see that error message, that is how I managed to write down the error message and post it here.


> The CMOS battery message and screen failure may just be a coincidence--especially on an older machine.  It's possible that you had a chip delamination which then caused the motherboard to short, draining the battery.  Sort of like grandma falling and breaking her hip.  Usually it is the other way around.  Grandma's hip breaks (due to osteoporosis) and she falls because it happens so suddenly.
It could be related and it could be not.

> Try some of these things:  [http://www.youtube.com/watch?v=NAsrhpOK2Qc](http://www.youtube.com/watch?v=NAsrhpOK2Qc) Spoiler Alert:  bad keyboard prevents booting.

The keyboard in my case, AFAIK, it works because when I press "F2" to enter BIOS, I see a message on the Toshiba Logo Screen saying entering BIOS or whatever that was and then sometimes beep, sometimes not and then blackscreen with just one line of error message, that is the title of this thread.

Any more thoughts?

---

### Post by amjjawad on 2014-01-29
> **tgalati4 said:**
> Try some of these things:  [http://www.youtube.com/watch?v=NAsrhpOK2Qc](http://www.youtube.com/watch?v=NAsrhpOK2Qc) Spoiler Alert:  bad keyboard prevents booting.

You're the best. The keyboard was the reason that is causing all the problems.

Problem fixed :D
I bought new USB keyboard for them and I will try to return back ASAP :)

[ATTACH=CONFIG]249899[/ATTACH]

Thank you!

---

### Post by tgalati4 on 2014-01-29
I just did a simple google search.  Nothing special.  Based on the wear on the paint, you have gotten some use out of your laptop.  Keyboards are like tires, they do wear out.

---

### Post by amjjawad on 2014-01-30
> **tgalati4 said:**
> I just did a simple google search.  Nothing special.  Based on the wear on the paint, you have gotten some use out of your laptop.  Keyboards are like tires, they do wear out.

At first, I didn't ever imagined my case would be similar and was about to leave it but one day, I decided to carry on and give it one last try and YES, it did work :D

By the way, that is not my own laptop. It is for one of my neighbours as [I do have a project in real life]("http://amjjawad.blogspot.com/2014/01/2014-report-project-convert-my.html") and that was part of it.

Thank you again!

---

### Post by tgalati4 on 2014-01-30
Nice story, so I guess this laptop is just a small part of the master plan.  Good luck.  Unfortunately, many machines running XP are getting so old that they suffer other problems besides running Windows.

---

### Post by amjjawad on 2014-01-31
> **tgalati4 said:**
> Nice story, so I guess this laptop is just a small part of the master plan.  Good luck.  Unfortunately, many machines running XP are getting so old that they suffer other problems besides running Windows.

Thank you :)

Some new machines I have seen so far which are suffering even worse issues than old machines :)
Trust me, old is gold. The quality of the old machines is much better than the quality of the machines in the past few years. This is from real life experience ;)

---

