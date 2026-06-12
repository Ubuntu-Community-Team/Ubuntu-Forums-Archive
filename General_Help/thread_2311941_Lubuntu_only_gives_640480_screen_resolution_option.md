---
title: "Lubuntu only gives 640*480 screen resolution option"
date: 2016-01-31
forum: General Help
---

### Post by ipooroo on 2016-01-31
So I installed Lubuntu on this really old PC - AMD Duron 800, 350MB RAM, and it is running fine. But, at first the GRUB2 bootloader did not run in the correct resolution and then neither did Lubuntu. So I applied the fix where you uncomment the line in /etc/default/grub so that it runs with resolution 640*480. Now, it appears fine, but when in Lubuntu, that is the only resolution option I had! Previously it would work fine in recovery mode. The optimum resolution for my monitor is 1280*1024

---

### Post by grahammechanical on 2016-01-31
The screen resolution for Grub and the screen resolution for Lubuntu are two different things.

I do not use Lubuntu so I cannot give precise details but if you are using the open source video driver then system settings should have a utility, may be called Screen Displays, that will let you detect displays and even set a screen resolution.

If you are using a proprietary video driver then there will be a setting utility that should let you do the same things. There is a command that we can run that will give us information about our display

```
xrandr
```

Lets us see the output, please. I have also noticed that the type of connection we make to the monitor also affects the screen resolutions available. VGA connections do limit the screen resolutions available I have found.

Regards.

---

### Post by ipooroo on 2016-01-31
In Lubuntu the setting you are referring to is found under  preferences->monitor settings. There is a drop down menu that usually has a bunch of resolutions in it, but only has 640*480 available. This is not true in recovery mode. The output from xrandr:

[http://www.pastebin.com/ThFJDU44](http://www.pastebin.com/ThFJDU44)

---

### Post by mörgæs on 2016-01-31
I think it would be good to have your hardware details. Please run ```
sudo lshw - sanitize > lshw.txt
``` and post lshw.txt here in CODE tags (better than uploading to an external site).

---

### Post by syntaxerror74 on 2016-01-31
[quote="grahammechanical"]Lets us see the output, please.[/quote]
(of xrandr)

Yes, that's a good suggestion.  And even before I can check it out:
Should you read something like "Unable to determine gamma" (or can't remember the exact wording), it looks for some reason that **nomodeset** is enabled.
This will also make it impossile to use some GUI tool (more exactly: frontend) like ARandR to crank up your resolution, as there will be only exactly one generic resolution available.

Oh, and **@**mörgæs:
I think that it *IS* better to use Pastebin for lshw output, as I really do NOT want to read several pagefuls of output here in CODE text on this forum.

---

### Post by mörgæs on 2016-02-01
> **syntaxerror74 said:**
> 
Oh, and **@**mörgæs:
I think that it *IS* better to use Pastebin for lshw output, as I really do NOT want to read several pagefuls of output here in CODE text on this forum.

Maybe for a human but not for a search engine, Ipooroo, please stick to the CODE tags.

---

### Post by sudodus on 2016-02-01
Sometimes you can solve such problems with low resolution according to these links

[how to increase screen resolution on laptop]("http://ubuntuforums.org/showthread.php?t=2260082")

[Change display resolution]("http://ubuntuforums.org/showthread.php?t=2269309")


Did you reboot? And it did not work. Then you have another problem ... Maybe you can read the following thread carefully and try

[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

or try according to the following wiki page

[Sometimes it takes real tweaking to solve the problem](https://help.ubuntu.com/community/Lubuntu/Monitor_or_Screens#Sometimes_it_takes_real_tweaking_to_solve_the_problem)

---

