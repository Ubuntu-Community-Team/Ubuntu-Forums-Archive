---
title: "Poor performance"
date: 2018-04-10
forum: General Help
---

### Post by Hungry Man on 2018-04-10
Any way I can fix performance on my system? I recently upgraded to a new laptop - it's got plenty of hardware.

It feels slower than the last. When playing games on Dolphin, or even just switching tabs in Chrome, it lags a lot - these are things I did with a much weaker laptop before.

Intel CPU, nvidia quadro GPU using the proprietary drivers.

I'm honestly just confused at how terrible performance is. It's worse than a considerably weaker system.

Maybe I can disable Unity and switch DM's or something? I don't know if that's the issue...

---

### Post by kerry_s on 2018-04-10
>  Any way I can fix performance on my system? 
yes

---

### Post by Hungry Man on 2018-04-10
How helpful.

---

### Post by wildmanne39 on 2018-04-10
@kerry_s

Can you tell him how to troubleshoot his issue? possibly give him directions to do what you say he can do?

@Hungry Man, please wait for more advice, I know you can change DM"S but I think it would be best to troubleshoot your issue first and  not take a chance of making matters worse.

---

### Post by Hungry Man on 2018-04-10
To be honest, my expectation is that it's an issue of drivers. Perhaps my old GPU was a better fit for them by virtue of being an older model.

Perhaps I should try the OSS ones.

---

### Post by wildmanne39 on 2018-04-11
This is not my field but if you post your specs and what version of Ubuntu you are using it will give people some information to be able to help you.

---

### Post by kerry_s on 2018-04-11
> **Hungry Man said:**
> How helpful.

you've given no actual information.

this is your specs:
> Intel CPU, nvidia quadro GPU using the proprietary drivers.

this is your complaint:
> It feels slower

so is it slower?
do you have enough ram, are you pushing a single core cpu?
what version of ubuntu are you running?

i'm feeling slow today. how about a little help?

---

### Post by Hungry Man on 2018-04-11
If you have questions, ask them. I'm more than willing to provide information.

Specs:

[COLOR=#555555][FONT=Arial]Intel Core i7-7820HQ Processor (8MB Cache, up to 3.90GHz)
[/FONT][/COLOR][COLOR=#555555][FONT=Arial]16GB DDR4 2400MHz SODIMM
[/FONT][/COLOR][COLOR=#555555][FONT=Arial]NVIDIA Quadro P3000 6GB
[/FONT][/COLOR][COLOR=#555555][FONT=Arial]1TB SSD PCIe TLC OPAL2


Kernel Version: 4.13.0-38-generic
Ubuntu: 16.04.01

Yes, it is slower. I can measure frame rates in Dolphin and game that was playable on a 5 year old laptop with worse specs is now unplayable. There is noticeable lag when switching windows.
[/FONT][/COLOR]

---

### Post by kerry_s on 2018-04-11
wow, those are great specs. i envy you.

are you using the standard drivers from the repo or from ppa?
have you tried disabling & re-enabling in the hardware drives? (uncheck & apply, recheck & apply)

> lag when switching windows
> I can measure frame rates in Dolphin and game

so mainly ui?

---

### Post by Hungry Man on 2018-04-11
Pretty exclusively UI, I'd say. I haven't noticed poor performance for other tasks.

> [COLOR=#000000]are you using the standard drivers from the repo or from ppa?[/COLOR]

I just used the Additional Drivers utility to install the nvidia drivers. Version 384.111.

Not sure what you mean by disconnecting and reconnecting the hardware drives.

---

### Post by kerry_s on 2018-04-11
> **Hungry Man said:**
> Pretty exclusively UI, I'd say. I haven't noticed poor performance for other tasks.



I just used the Additional Drivers utility to install the nvidia drivers. Version 384.111.

Not sure what you mean by disconnecting and reconnecting the hardware drives.

yeah, you should be able to turn then on/off from there.

---

### Post by cruzer001 on 2018-04-11
Sounds like my Dell.  Got one with similar specs, quadro 3000m video card using the nouveau driver for now.  Got 18.04 running on the ssd and its plenty fast, never ran 16.04 on it.  I'm not a gamer so don't know how it would do on frame rates.

Just thought you might like to know 18.04 is a possible option.

---

### Post by speartip on 2018-04-11
I agree with cruzer001. It's only a matter of days until 18.04 is officially released. I've been using the beta of ubuntu budgie & kubuntu, & they already feel rock solid. Plus both systems fly on my machine with way less specs than you have.

---

### Post by kathyjohnson320 on 2018-04-11
I have same issue as yours. sometimes upgrades are too bad for our system. I lost my important documents after upgrading my system.

---

### Post by speartip on 2018-04-11
> **kathyjohnson320 said:**
> I lost my important documents after upgrading my system.
That's why before making any major changes to your system, employ the number 1 rule in computing. BACKUP.

---

### Post by Hungry Man on 2018-04-11
Moving to a beta Ubuntu system has bitten me before, so I'm reluctant to do so.

Switching drivers and restarting did not help.

I think Compiz has, historically, eaten a lot of CPU. In 18.04 I believe there are some significant overhauls to the UI - perhaps that would work?

Also, 18.04 is not LTS - this bit me recently, as I could not upgrade and had to reinstall from scratch. I suppose I'd just have to stay on top of upgrades...

---

### Post by Hungry Man on 2018-04-12
Well, I'm installing 17.04, since that's at least a stable release. When 18.04 comes out I'll switch to that.

Fingers crossed...

---

### Post by wildmanne39 on 2018-04-12
17.04 has reached EOL, there is no support for it anymore not even security updates.

---

### Post by speartip on 2018-04-12
@Hungry Man..
As wildmanne39 says, 17.04 is no longer even supported.
18.04 is hardly beta now with only days to go till it's final release.
Also 18.04 is indeed an LTS edition.

---

### Post by PaulW2U on 2018-04-12
> **Hungry Man said:**
> Well, I'm installing 17.04, since that's at least a stable release. When 18.04 comes out I'll switch to that.
In addition to what speartip has said, you won't be able to install any new software or update important applications, such as Thunderbird, Firefox and Chromium, to their current and secure versions as the 17.04 repositories have been removed.

---

### Post by kathyjohnson320 on 2018-04-12
Thank you for the information @Speartip!!!

---

### Post by Hungry Man on 2018-04-12
As an update - I've now moved to 18.04. I have to say, performance is *drastically* better.

FPS in Dolphin is considerably higher, no more lag moving between windows. This is a blatant improvement.

I'll mark this thread as solved.

---

### Post by cruzer001 on 2018-04-12
Which driver did you end up using 384 or 390?

Thanks

---

### Post by Hungry Man on 2018-04-12
Oh, apparently I'm now on 390 - I'd bet that has at least something to do with the performance improvements.

---

### Post by 9cddz&amp;mK07%F@ on 2018-04-14
Maybe a lighter desktop enviroment such as LXDE?

---

