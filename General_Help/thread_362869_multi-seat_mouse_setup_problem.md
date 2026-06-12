---
title: "multi-seat mouse setup problem"
date: 2007-02-16
forum: General Help
---

### Post by cooperuf on 2007-02-16
I`m trying to setup a multi-seat system with 3 seats, my hardware is
1.5GHz Celeron
512Mb Ram
1xPS/2 Mouse
1xPS/2 Keyboard
2xUSB Mice
2xUSb Keyboard

1xIntel i810 VGA onboard
2xRadeon 7000 VGA PCI

The 1st X-server starts and the correct PS/2 Mouse and Keyboard attach to the onboard VGA display and work correctly.
When the 2nd X-server starts, again the correct USB mouse and keyboard attach to the correct PCI VGA Display and functions correctly, but the 1st X-server mouse and keyboard stops responding visibly to movement and keypresses,  a cat of the /dev/input/(mouseX/eventx) show the events are still being generated.
When the 3rd X-server starts its mouse/keyboard functions correctly, again the mouse/Keyboard for the 2nd X-servers appears to be unresponsive.

When the 3rd X-server is killed, the 2nd X-servers Mouse/Keyboard functions as normal but, the 1st X-server Mouse/keyboard still appear not to function, until the 2nd X-server is killed, when the 1st X-server then mouse/Keyboard functions as normal.

I have tried with Breezy and X-org 6.8.2, Dapper with 6.9 and Edgy with 7.1 and with all of then the result is the same, only the last X-server to start has a responsive mouse and keyboard.

Currently my xorg.conf device sections are using the evdev driver and /dev/input/eventX devices, i have tried a mixture of the following all with the same result.

	Drivers		kbd mouse evdev
	Devices		/dev/input/eventX /dev/input/mouseX

All i`m trying to achieve is a host with 3 X-Displays with 3 mice, the rest of the OS/Programs are irrelevent as the X-display are only there to display graphical infomation generated on a seperate host. keyboard configuration is not required, it is only included to test the set up, as the final displays will be driven by only touchscreens and no mice. Yes, when the touchscreens are used in place of the mice the same result again, only the last X-server has its touchscreen functioning. 

Attached are my 3 xorg.conf and Xorg.X.log for each of the servers.

Referances that i have used:

	[http://en.wikibooks.org/wiki/Multiterminal_with_evdev](http://en.wikibooks.org/wiki/Multiterminal_with_evdev)
	[http://www.the-rickerts.de/mr/multiseat.html](http://www.the-rickerts.de/mr/multiseat.html)
	[http://83.211.124.203/multiseat.html](http://83.211.124.203/multiseat.html)
	[http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html)   6-head multi-seat
	[http://gentoo-wiki.com/HOWTO_Multiseat_X](http://gentoo-wiki.com/HOWTO_Multiseat_X)
	[http://blog.chris.tylers.info/index.php?/archives/14-Multiseat-X-Under-X11R6.97.0.html#extended](http://blog.chris.tylers.info/index.php?/archives/14-Multiseat-X-Under-X11R6.97.0.html#extended) Multiseat
	[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)
	[http://cs.senecac.on.ca/~ctyler/ruby/](http://cs.senecac.on.ca/~ctyler/ruby/)    3-head multi-seat


As far as i can tell i have setup my systems the same as all of the above, all with the same result

If anyone can help, or point me in the right direction i`d appreciate it.

---

