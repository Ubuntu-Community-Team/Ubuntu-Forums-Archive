---
title: "Ubuntu 18.04.5 LTS bionic - Does not start after grub"
date: 2022-07-04
forum: General Help
---

### Post by monera on 2022-07-04
Hi guys,

I am crazy these days trying to solve this problem with no success.

Suddenly my ubuntu does not load as expected and is not starting, staying with the black desktop. Ok, that is true that I had a couple of things that probably triggered that_

- Low disk space (I entered in the maintenance mode and I guess I solve that.)
- I also have windows, so while booting, I can chose between windows and ubuntu. I don't know if this is related but these problems started after windows got updated. 
-The battery keeps showing as 4%, very low, and does not show another value, does no charge, looks like?
- When I enter in the maintenance mode in ubuntu the system starts but the brightness is at it full, and I can't change it, or it doesn't change. Looks like something connected to the graphics? Anyway I checked the graphics in the terminal and it says they are working fine. I already added the codes to the grub:

RUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor acpi_osi=linux" and
RUB_CMDLINE_LINUX_DEFAULT="modeset" and
RUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=0" , but nothing works.

Actualy, I have to admit that it worked once when I added this last line, I could change the brightness with the keys and work as normal. But after I shutdown the computer it never worked again.

Are you able to help me? :D

Thank you!

---

### Post by #&amp;thj^% on 2022-07-04
1st check your Bios and double check Secure Boot is disabled!!!
2nd is more of a question from me>>> How did you slove>>>> - Low disk space (I entered in the maintenance mode and I guess I solve that.) 
This will be important in giving us a step by step process that you ran to solve that.
And this is me just poking a bit of fun with you, I've never seen A grub-config Like this, "RUB_CMDLINE_LINUX_DEFAULT=" :D

---

### Post by monera on 2022-07-04
> **1fallen said:**
> 1st check your Bios and double check Secure Boot is disabled!!!
2nd is more of a question from me>>> How did you slove>>> 
This will be important in giving us a step by step process that you ran to solve that.
And this is me just poking a bit of fun with you, I've never seen A grub-config Like this, "RUB_CMDLINE_LINUX_DEFAULT=" :D

THank you for your reply 1fallen.

I was checking the bios and I don't know where to start exactly. WHat do you mean about checking secure boot is disabled? How can I do it?

I entered in the maintenance mode and moved all the big files to an external disk. Now I have space.

"A grub-config Like this, "RUB_CMDLINE_LINUX_DEFAULT="

What do you mean with this? :D

Thank you!

---

### Post by #&amp;thj^% on 2022-07-04
> **monera said:**
> 
"A grub-config Like this, "RUB_CMDLINE_LINUX_DEFAULT="

What do you mean with this? :D

Thank you!
See it brought a smile to your face. ;) Just a Joke we can have fun here as well as help others.
You knew You had left  the "G" out of your first post, right?? Leavig it as "RUB"
> **monera said:**
> THank you for your reply 1fallen.

I was checking the bios and I don't know where to start exactly. WHat do you mean about checking secure boot is disabled? How can I do it?


Yours might be different, but mine is under the Security option.
> **monera said:**
> 
I entered in the maintenance mode and moved all the big files to an external disk. Now I have space.

  
So are you now able to boot to your desktop? If not show this please:
```
df -hT

```

---

### Post by monera on 2022-07-04
> **1fallen said:**
> See it brought a smile to your face. ;) Just a Joke we can have fun here as well as help others.
You knew You had left  the "G" out of your first post, right?? Leavig it as "RUB"

Yours might be different, but mine is under the Security option.
  
So are you now able to boot to your desktop? If not show this please:
```
df -hT

```


AH ok, now I got it ;D

ok I found it and it was disabled. In any case even if I would want it doesn't let me enable it.

Yeah, after doing some partial updates I could start the ubuntu normally. I will restart again and see if it keeps.

In any case I keep with the other same problems. The battery shows as very low (4% all the time), and the brightness is set to maximum, and it doesn't change even if I press up or down buttons... crazy stuff..

---

### Post by #&amp;thj^% on 2022-07-05
these are just suggestions for you, on the battery issue can you show this:
```
upower --dump
```
For the brightness there is a pretty good PPA that has better contorl over that, found here: [https://launchpad.net/~apandada1/+archive/ubuntu/brightness-controller](https://launchpad.net/~apandada1/+archive/ubuntu/brightness-controller)

I can also control my brightness using xrandr, example:
find connected displays with:
```
xrandr | grep " connected" | cut -f1 -d " "
```
then I'll run: (My display is DP-2 yours may be different)
```
xrandr --output DP-2 --brightness 0.7

```
which should dim the display.
to revert use:
```
xrandr --output DP-2 --brightness 1

```
If you choose to add the PPA and have An Nvidia card let me know there is few more tweaks to add. 
 
This all sounds like a bug in gnome-power.

---

