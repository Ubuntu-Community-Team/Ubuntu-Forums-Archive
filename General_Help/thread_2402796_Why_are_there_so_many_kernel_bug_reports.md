---
title: "Why are there so many kernel bug reports?"
date: 2018-10-04
forum: General Help
---

### Post by pretty_whistle on 2018-10-04
Kernels 4.15.0-36, 4.15.0-34, and 4.15.0-33 all have bug reports stating that the boot process wasn't finishing.  What's going on that every kernel since -33 keeps getting major bugs?  I've been waiting to do an update/upgrade to 18.04.1 but every kernel is bad so I'm waiting for a good one.

What's going on here?

---

### Post by pretty_whistle on 2018-10-04
I Googled them.  Here's one I found and I have a question about it:

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/1795793](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/1795793)

In the "bug description" it says:

> [COLOR=#333333][FONT=monospace]Uname: Linux 4.15.0-34-generic x86_64


[/FONT][/COLOR]

Doesn't this mean the kernel they have installed is [COLOR=#333333][FONT=monospace]4.15.0-34 and not [/FONT][/COLOR][COLOR=#333333][FONT=monospace]4.15.0-36?  So why is the bug listed as being for [/FONT][/COLOR][COLOR=#333333][FONT=monospace]4.15.0-36??  Did this person just mess it up??

When I Googled, I searched for [/FONT][/COLOR][COLOR=#333333][FONT=monospace]4.15.0-36 bug and a list came up.  All but one has the uname listed as [/FONT][/COLOR][COLOR=#333333][FONT=monospace]4.15.0-34 in the bug description.  If the uname is showing [/FONT][/COLOR][COLOR=#333333][FONT=monospace]4.15.0-34 then it's not a bug for [/FONT][/COLOR][COLOR=#333333][FONT=monospace]4.15.0-36, that's my understanding of uname.  Am I right?

[/FONT][/COLOR]

---

### Post by pretty_whistle on 2018-10-05
Putting that question aside in post 2, here's something:

I've updated to 4.15.0.-33, the computer wouldn't boot.

After this I decided to Google future kernels for any bugs, found several for 4.15.0.-34 so I chose not to update to it.

Then the next kernel came out, that being 4.15.0.-36, so I took it despite finding one bug report for it well guess what now? 50% of the time my computer won't boot and I get a small error screen mumbling about being in low graphics mode and claiming it can't sense the graphics card.  I have to click "ok" to get to the next screen which gives me the option to "try and run it in low graphics mode", then I can get the desktop.  Plus, when I exited Clonezilla CD the screen froze and told me it was "freezing process", I had to shut it down and power back on again.

-33 was bad, -36 is bad, and -34 was bad according to others who reported bugs.

Why is every kernel bad? What's going on here?

What's worse is I used update manager to get this update. I waited 4 days to do it so I wouldn't get a phased update and hence a possibly bad kernel. Got one anyway.  Ugg.

I was updating from Ubuntu 16.04.4, now I've got 16.04.5 with a bug.

Can someone offer any help? I'm not just ranting.....

---

### Post by pretty_whistle on 2018-10-06
Update:

Recent kernels that weren't booting:

4.15.0-33
4.15.0-34
4.15.0-36

With -36 I got a graphics error. Then I tried upgrading to 18.04.1, it never booted at all.

I restored my system to my backup of 16.04.4 and don't have the above anymore so there's nothing to help me do since I don't have it now.

P.S.

I don't know if this has any impact on what's going on here but when Googling the kernels I found on a Fedora forum that nearly all 4.15+ kernels were bad.  This might explain it.

---

