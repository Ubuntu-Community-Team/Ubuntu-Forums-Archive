---
title: "Numlock on boot up NOT working in Lubuntu 14.04.1"
date: 2014-08-09
forum: General Help
---

### Post by Enigma12 on 2014-08-09
I would like my numlock to be ON as the computer boots up. I have not been able to achieve this. 

In the big picture this is an admittedly minor issue, I realize, but I have read numerous posts seeking the solution to this for a variety of distros, so I know that I am not alone in having this problem. Nothing that has been suggested in these posts works for me, and I've tried a bunch of advised actions. Some are listed below, many edited for space consumption: 

*"Have you tried editing /etc/xdg/lubuntu/lxdm/lxdm.conf instead? Uncomment # numlock=0 and make it numlock=1   Worked for me :)"*

Did that. Didn't work for me with the BIOS setting being either ON or OFF. 

[I]"File edit works in Raring Ringtail (13.04) but you need to open in terminal under root:
    Code:    sudo leafpad /etc/xdg/lubuntu/lxdm/lxdm.conf
    As before find the line
    Code:    # numlock-0
    and edit to
    Code:    numlock-1
    then hit save and the jobs a good 'un." [/I]

 As above, this didn't work with either BIOS setting. In my lxdm.conf file, the dash shown above for all settings is an =, and I kept that = sign. 

*"another update: so, now I'm using numlockx - doesn't need to be configured, just installed. –"*

That file or program is not on the Lubuntu Software Center, but I did find it on Synaptic. Did NOT download and install it, though. Should I? Before I do, I have to ask, has this worked for others using Lubuntu 14.04.1?

---

### Post by David_Wright on 2014-08-09
numlockx works fine for me on Lubuntu 14.04 (and 13.10 before that) - install, run and then forget it.

---

### Post by Enigma12 on 2014-08-09
> **David_Wright said:**
> numlockx works fine for me on Lubuntu 14.04 (and 13.10 before that) - install, run and then forget it.

David, I wish it worked for me also, but it didn't. Since I got all other downloads through Lubuntu Software Center successfully, this was my first time using Synaptic. Using it seemed quite straightforward. What I did was type in "numlockx" (w/o quotes) in the search field, and it came up. Highlighted it and clicked Install, which seemed to work OK. 

Rebooted the computer. As always, the numlock LED lit up for a few seconds, then went out. After I booted, I did a search in PCManFM for numlockx and it found nothing. Did I miss something? If so, what? 

Note: I've only been using Linux and Lubuntu since April 2014 and have done little command line activity. What I have done in Terminal is type in commands that I found either here or elsewhere, generally successfully. Other than a printer config problem, which got fixed, this numlock issue is the ONLY flaw that I find in Lubuntu. I have 2 computers, one running Windows 7, and the one I'm using now running Lubuntu 14.04.1. When I first started using Lubuntu, I planned on doing most of my daily computer activity on the Win 7 one and easing into Linux maybe 2 or 3 times per week with the other. That has been reversed. I like Lubuntu that much.

---

### Post by Dennis N on 2014-08-09
Lubuntu 14.04 needs numlockx if you want NumLock active on login. I installed it. It should come on and stay on after you login, not when the computer starts up. Some users don't need it or don't want it so that is probably why it is optional.

To confirm that it is installed, start your terminal and type the command in red. Press Enter. If the line **Installed:** shows a numeric code (the version), it is installed. 

```
dmn@Roxanne:~$ [COLOR="#FF0000"]apt-cache policy numlockx[/COLOR]
numlockx:
  Installed: 1.2-5
  Candidate: 1.2-5
  Version table:
 *** 1.2-5 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status

```

If it shows as installed and NumLock still fails to be active, try reversing the change to lxdm.conf. My system has [FONT=Courier New]**[COLOR="#FF0000"]# numlock=0[/COLOR]**[/FONT] in that file. If you made any other changes following other suggestions, those could be problematic as well.

---

### Post by Enigma12 on 2014-08-10
> *To confirm that it is installed, start your terminal and type the command in red. Press Enter. If the line **Installed:** shows a numeric code (the version), it is installed.*

Dennis, I typed that line into Terminal and got everything below it exactly as you got. I haven't made any other changes. Still doesn't work. 

> *If it shows as installed and NumLock still fails to be active, try reversing the change to lxdm.conf*

I've changed the lxdm.conf setting to both 0 and 1 and changed the BIOS setting to both OFF and ON and rebooted each time. Same result: numlock still doesn't work unless I press the keyboard key. All I've accomplished doing this is to solidify my memory of my password, which was already well memorized. 

It could be some not-yet-discovered setting or my hardware or planetary alignment causing this very minor problem. Since it's not that big a deal, I'll just live with it, and, maybe, some future upgrade will solve it or I'll find a solution as I learn more. 

Thanks to both you and David for your advice.

---

### Post by Dennis N on 2014-08-10
It seems to be a long-standing bug (at least since 2008) and still not resolved:

[https://bugs.launchpad.net/ubuntu/+source/numlockx/+bug/218202](https://bugs.launchpad.net/ubuntu/+source/numlockx/+bug/218202)

I have never had a problem with numlockx myself, but that is no consolation to you. This bug is not only seen in the Ubuntu family, but reported against Debian and Fedora as well.

Edit: Looking again, I think that bug is just about the light not coming on. Actually there are two open bugs in numlockx:

[https://bugs.launchpad.net/ubuntu/+source/numlockx/+bugs](https://bugs.launchpad.net/ubuntu/+source/numlockx/+bugs)

---

### Post by JKyleOKC on 2014-08-10
Have you tried using the keypad, or are you depending on the LED to be truthful?

I ask because I have one virtual machine, that I use quite often, in which the pad and the LED get out of sync with each other rather often. The result is that with the LED on, the keypad issues mouse-like actions rather than numerals, and with it off, works as I expect. Cycling the NumLock key a few times restores it to sync so I've not delved deeply into the cause, just learned to be cautious about using the keypad when filling out a database entry.

Another thought occurred to me while typing the previous paragraph. Take a look at your system settings for "accessibility" (since I use Xubuntu, not Unity, I don't know the exact menu that will have yours but they are certain to be there somewhere) and specifically, for a setting to make the keypad emulate mouse movement. If that setting is turned on, it will force the keypad into non-numlock mode but may or may not affect the LED.

Hope this helps!

---

### Post by Enigma12 on 2014-08-10
> *It seems to be a long-standing bug (at least since 2008) and still not resolved*

Since I've been coming to this site, I've learned that gobs (a very technical term ;)) of people have more significant problems than I have had, at least so far. 

I had a printer problem that went away through swapping printers around until I had working printers on both my Lubuntu and my Windows 7 computers. I don't know why that worked, but it did and now all is well enough to keep me satisfied. 

Frankly, the only reason I've even entered the Linux world is some frustration with Windows and/or Microsoft. Right now, Windows 7 will continue to be supported by MS until 2020. That gives me almost 6 years to get more proficient with Linux before --and IF-- I abandon MS, as they plan to abandon me. If I could put myself into an earlier point in my life, I would have gotten into Linux sooner.

---

### Post by Enigma12 on 2014-08-10
[I]> Have you tried using the keypad, or are you depending on the LED to be truthful?
> Take a look at your system settings for "accessibility"[/I]

Jim, you've given me some more matters to explore. Yes, I HAVE been expecting the LED to tell me the correct numlock status. Guess I need to confirm or negate that expectation. I will also, as you suggest, explore other system settings. I just need to be cautious to not create another problem. I don't see any "accessability" setting in either System Tools or Preferences. That may be buried in some other configuration title. 

I expected a learning curve in using Terminal. It seems that that also exists in just setting things up to desired state. The adventure continues!!!!!

---

### Post by Enigma12 on 2014-08-13
After being advised to download and use numlockx and to not count on the LED showing correct status, I find that numlockx is, indeed, working, but the LED does not necessarily show that. Now I simply boot up and ignore the LED. After I press any number on the number pad, the LED lights and stays lit until I shut down the computer. Problem solved.

---

### Post by LiberaTek on 2014-12-19
I know this thread is already a few months old, but this was one of the first that appeared on search results.  I had the same problem, and would like to share what worked for me (just in case someone else has the same problem):


[LIST=1]
[*]Install numlockx
[*]Add numlockx to the Autostart section of the LXSesion configuration (on the main menu, Preferences - Default Applications for LXSession - Autostart)
[/LIST]

After doing that, I get Numlock working by default on login and I see the Numlock light on.

---

### Post by JKyleOKC on 2014-12-20
That works fine, sometimes, and sometimes the exact reverse happens. The important thing to remember is that the LEDs cannot be trusted to be truthful at all times. It's not so much a bug, as it is just a result of the differences in system architecture that cause them to be controlled at additional points in the lowest-level code. In Linux, the LEDs can be used to signal problems if those problems prevent the monitor from being usable. Windows, OTOH, uses patterns of beeps from the built-in speaker to do that signalling.

Getting out of sync with the actual state of the keypad, then, doesn't really indicate a problem with the system. It just means that the LEDs can't be trusted to be accurate.

---

