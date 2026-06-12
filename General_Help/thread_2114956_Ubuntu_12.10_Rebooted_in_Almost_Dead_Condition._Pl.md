---
title: "Ubuntu 12.10 Rebooted in Almost Dead Condition. Please Help"
date: 2013-02-11
forum: General Help
---

### Post by ArlieS on 2013-02-11
I had a working 12.10 installation, using the default desk top manager. On Friday I did a normal shutdown. ("sudo shutdown -h now"). When I powered it on this morning, it came up part way, completely unusable - I couldn't even do a controlled shutdown. I power cycled it and rebooted on a 12.10 install DVD. 

Symptoms: 
- graphical login seemed normal
- once logged in, I had a screen with no menu bar. The menu you get by right clicking on the desktop surface was available, but that can only get one into gedit, which appears not to have a shell escape. (*sigh*) I tried to remember keyboard shortcuts to get e.g. a command prompt. No luck, but I may have misremembered.
- I then did ctrl-alt-f2, which should have gotten me to a different screen, with non-graphical login prompt. I got the different screen, but no prompt.
- ctrl-alt-f7 got me back to the non-functional GUI screen
- I then futzed around in gedit, looking for a shell escape; got a popup about a compiz crash and reporting it. Tried the report-and-restart-it option - got another popup with the same complaint, or perhaps it was the same one.
- A coworker then came in, and I used his system to determine that my system was pingable, but refusing ssh, telnet, rlogin et al. I do not know _for sure_ that ssh was enabled on the system, but I believe that's the default. Telnet was probably disabled by default.

I do not see how a compiz issue could affect logins on alternate screens - or ssh, assuming it was indeed enabled.

I am in the habit of installing updates approx. once a week, using the GUI tool (having determined that the "apt-get upgrade" doesn't behave the same as the tool, and being unsure which is the currently supported mechanism). I normally reboot immediately after this, whether or not prompted to do so, but it's possible I didn't do so last week. 

Some questions for all:
1) How do I recover from this?!?!? I can presumably mount my disk, but even if there's a patch that supersedes this bug, it's unclear to me how to install it - the tools seem inclined to assume you want to update the system you are booted from.
2) Is this a known problem, with a fix?!?
3) I'm not all that familiar with ubuntu. How stable is 12.10? There have been a _lot_ of patches, including new kernels. Should I be on 12.04 or earlier if I want stability? What I really want is just well tested / security fixes, and maybe a feature or two _if_ I would actually use those features.  [For what it's worth, my other ubuntu system - running 12.04 - has not given me any grief. But it came from a vendor who designs their systems for linux, and is not a laptop, so the difference might be hardware related]
4) I'm not a window manager person, so I'm not sure what things would be fixed by going with a different window manager.  Is this likely to be one of them? Is kubuntu for example, more stable than ubuntu, i.e. kde less of a source of general flakiness than unity?
5) Is there any reason to believe that lenovo Thinkpads are BAD hosts for ubuntu? unity? linux?
6) (I know this is the wrong place to ask, but) What distro would folks recommend for someone who wants stability over all? My workstation needs to be a reliable tool, not a hobby project. And this is my _third_ system-unusable issue on Ubuntu in less than 3 months. 

Other possibly relevant data: my graphics setup causes windows 7 to blue screen (or ignore all external monitors). I guess that makes it "bleeding edge". It _might_ be the source of my compiz problems - or not, the impression I've gotten is that compiz is so flaky it shouldn't be out of "unstable" yet :-( This isn't the first or second compiz crash I had, to the point where I've no idea whether the compiz cores are even related to the system unusability.

[Update: I think this may be a variant of bug 106848/107042 unfortunately neither bug report explains how to recover, once you've tried to reboot, so I'm still SOL.]

---

### Post by Mark Phelps on 2013-02-11
Can't guarantee that this will work for you -- but it did for me when my Unity stuff suddenly disappeared from the desktop:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

### Post by ArlieS on 2013-02-12
It appears to have been a variant of bug 106848/107042, i.e. an unfortunate issue involving incorrect dependencies in the nvidia driver, exacerbated by tools that conceal any error messages that may be produced, and the indifferent-at-best availability of fall back logins when the GUI fails, not to mention diagnostic tools *which require a GUI to function*. 

Alternatively, it may have been straightforward nvidia breakage, not involving headers.

Recovering took 2 hours, essentially because:
1) It was extremely difficult to get a functioning non-GUI shell, with networking, when booted off the broken system - and the methods I used weren't reliable - it worked sometimes, not other times
2) It was impossible to browse the web from said non-GUI shell, in particular impossible to access these forums and the Ubuntu bug database. (No surprise here :-() 
3) I was unable to figure out how to do package upgrades/installs/removals to my broken disk-based installation when booted from a DVD etc.

1 + 3 strike me as significant problems. #1 is especially serious; the recovery boot options should _work_, not hang while bringing up networking.  I'll be filing bugs for both of them; #3 will be filed against the _documentation_ of Ubuntu and/or apt-get et al. 

Now the recipe, and the problem description:

Problem: nvidia drivers don't install sanely on a lenovo T430, and the result is an unusable system. This may be related to the presence or absence of kernel-headers; I don't know. There is no error message at installation time. 

Resolution: 
- Get into a non-graphical shell booted off the offending system. This may be extremely difficult to accomplish, at least if you want networking ;-)
- (Possibly unneeded) "sudo apt-get install linux-headers-3.5.0-17" etc. for any kernels you may have on your system (I had 3.5.0-17, 3.5.0-22, 3.5.0-23)
- use "dpkg -l | grep nvidia" to find any packages relating to nvidia.  Rows beginning with ""ii" are installed on your system.
- use "sudo apt-get remove" to get rid of all nvidia packages. E.g. "sudo apt-get remove nvidia-graphics-drivers"
- (optional, tongue in cheek) pray to Murphy, or other supernatural being with power over computer issues
- reboot ("sudo shutdown -r now") and hope your problems are solved

It's possible that networking was not in fact needed, if in fact all I needed to do was "apt-get remove" the offending driver(s).

---

