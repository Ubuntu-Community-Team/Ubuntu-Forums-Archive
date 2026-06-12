---
title: "Part of the screen (Desktop) is black [Pic inside] (happens with 17.10s on Atom n270)"
date: 2017-10-25
forum: General Help
---

### Post by xp15 on 2017-10-25
The mouse is visible on the black part, and i can drag windows from there.
Print screen produces a normal pic with all the desktop as it should look like.

I have this problem with 2 atom n270 laptops, With the first one I could "fix"
it temproary by connecting an external screen, then switching to CLI (Ctrl+Alt+F1) and
back to the gui (Ctrl+Alt+F7). It might be a temporary fix for the second
laptop too, just didn't check it.

It happens only in 17.10 versions (Ubuntu, Ubuntu mate, Lubuntu).
Previous versions of Ubuntu are fine. Also Windows and Manjaro are fine.

Pic of second laptop having this: [https://imgur.com/b6iTmFi](https://imgur.com/b6iTmFi)

Possible tags: screen, screen black, monitor, laptop, monitor and laptop, monitor display, 17.10, atom, atom n270, n270, intel atom,

---

### Post by DuckHook on 2017-10-25
Many people are frustrated when I say this, but it's true, so it must be said:

Non-LTS releases are considered less stable and supported for only 9 months for a reason… They are meant for those who either need to be on the bleeding edge (testers, developers), or have HW so new that they have no other choice.

Everyone else should be on LTS versions, which as of today, means Xenial (16.04).

Aardvark is, in my opinion, especially problematic. It is the first release that switches from Unity to Gnome, and replaces X with Wayland (though not, I am told, by default). It is bound to have hidden issues, bugs and inconsistencies.

My advice is to reinstall Xenial. Unless your objective is to participate in the testing of Aardvark or unless you have HW issues that leave you no other choice, you really should wait until the next LTS, 18.04, to upgrade, and even then, not until the first point release.

---

### Post by felix-niaou on 2017-10-26
Hello. I have a notebook asus eeepc 1005ha and i installed xubuntu 17.10. I have the same problem with you [**[COLOR=#000000]xp15[/COLOR]**]("https://ubuntuforums.org/member.php?u=1325903"). When i open the notebook, the screen is black except a part right of the monitor. I install the drivers but the problem insist.
Do the followings and write back if that worked. Open the notebook and press the power button at the right up corner of the screen. Select suspend. Wakeup the notebook and all are back to normal!!! Until the next reboot. You have to follow the previous steps every time you open the notebook.

---

### Post by xp15 on 2017-10-26
Thanks for the tip felix! So I need to press my power button to make the Shut-down, reboot, etc... manu appear? I can press suspend there (Now I understood that ender is enter :P ).


Is it permanent or would come back next reboot? My workaround was to connect a monitor, then go Cli and GUi again.
I may try it, Im trying Windows 10 now, it can run words... and slow internet... Can't have smooth video though (Though Smtube and smplayer with sld output was pretty good).


Thanks DuckHook for the suggestion, I might as well downgrade back to the LTS. It's just that my ;aptops are not new (2008-2009) or powerful (Atom n270, 1GB ram), So I want the newest system that would be lnewest, lightest and fastest. I think I read that 16.04s performance was less than 16.10, or 17.**.


I was told it's a bug in the kernel (commented on my post here [https://askubuntu.com/questions/969014/part-of-the-screen-desktop-is-black-pic-inside-happens-with-17-10s-on-atom](https://askubuntu.com/questions/969014/part-of-the-screen-desktop-is-black-pic-inside-happens-with-17-10s-on-atom))


The bug is [https://bugs.launchpad.net/ubuntu/+bug/1724639?comments=all](https://bugs.launchpad.net/ubuntu/+bug/1724639?comments=all)


Any more suggestinos would be aprreciated.

---

### Post by felix-niaou on 2017-10-26
Unfortunately, this tip is not permanent. Sorry for the wrong spelling of the word enter!!!! LOL

---

### Post by felix-niaou on 2017-10-26
I hope they will repair the bug soon.

---

### Post by xp15 on 2017-10-26
My laptop is working now. I don't know how (One of them at least). I don't remember that I've done anything to it. I was using windows...

Edit: After a reboot... Same bug again ):

---

### Post by DuckHook on 2017-10-26
> **xp15 said:**
> …It's just that my ;aptops are not new (2008-2009) or powerful (Atom n270, 1GB ram), So I want the newest system that would be lnewest, lightest and fastest. I think I read that 16.04s performance was less than 16.10, or 17.**…
The biggest impact on performance is not what version you use, but what flavour. Lubuntu, MATE and Budgie would all work on the system that you describe. The versions after Xenial did tweak some things for better speed, but other things were slower, so I suspect it all evened out in the wash. Non-LTS versions are less stable. The devs don't like it when I put it that way, but it's just true. Of course, if you like playing around with the OS and solving problems (many people do) then that's another matter entirely. But if you just want productivity out of the thing, then sticking to the lightest flavours of an LTS is the way to go.

Good Luck and Happy Ubuntuing!

---

