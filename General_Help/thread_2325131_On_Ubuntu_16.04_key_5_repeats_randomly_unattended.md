---
title: "On Ubuntu 16.04 key 5 repeats randomly unattended"
date: 2016-05-19
forum: General Help
---

### Post by pastim on 2016-05-19
I have a fresh (i.e. not an ugrade but a new installation) 16.04 ubuntu system, with a Logitech wireless keyboard and mouse (MK700/710).  When the system is unattended, key 5 will suddenly start repeating over whatever is on display.  This can be on a document, spreadsheet, banking application, and so on.  This happens randomly, sometimes many times a day, sometimes not all.

This is seriously worrying.  I have already had to restore some data from backups.

I am not alone.  Others have reported similar on askubuntu (with other logitech keyboards), and in bug report at [https://bugs.launchpad.net/bugs/1580732](https://bugs.launchpad.net/bugs/1580732)

I'm not getting much help with this, either in ways of finding out what it can be, or in trying changes.  It has been suggested that I upgrade the kernel to 4.5 or 4.6.  I'm not sure if that is sensible or safe on xenial LTS.

On 14.04 it was fine.  I don't see how it can be the keyboard itself, but if there is a way to test I'll happily do so.

---

### Post by leifjohn on 2016-05-26
I have been having the same problem! Ubuntu 15.10, Logitech wireless keyboard K800. I will turn off the keyboard and mouse at the end of the day, come back the next morning to find that the monitor never went to sleep - click inside a text box, URL address bar etc and 5's start showing up as if the '5' key were being held down, even though the keyboard is still off. I have to make sure I do not have any editor or text area in focus when I leave at the end of the day, otherwise there is a good chance I will get back in the morning with a frozen computer because it tried to enter in billions of 5's all night long. This is really starting to annoy the hell out of me.

---

### Post by Jumbs on 2016-05-27
Same here. 

There is a bug report with a mild patch.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1580732](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1580732)

---

### Post by pastim on 2016-06-09
There is a possible kernel patch - see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1579190](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1579190) 

The more people who try it the better.

---

### Post by Trapper on 2016-06-09
> **pastim said:**
> There is a possible kernel patch - see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1579190](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1579190) 

The more people who try it the better.

Right. I have been using the patched kernel for 3 days now and have had zero 555555's incidents. It's still too early to consider it to be a successful patch but so far so good. We need everyone we can, that experiences this 55555's problem, to test this patch for a week or two.

---

### Post by pastim on 2016-06-14
> **Trapper said:**
> Right. I have been using the patched kernel for 3 days now and have had zero 555555's incidents. It's still too early to consider it to be a successful patch but so far so good. We need everyone we can, that experiences this 55555's problem, to test this patch for a week or two.
The patched kernel has been shown to work for all who have used it.  It will released in due course.  Keep watching the bug report at [https://bugs.launchpad.net/ubuntu/+s...x/+bug/1579190]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1579190")[COLOR=#000000]    to see when it is available*.*[/COLOR]

---

### Post by Trapper on 2016-06-15
> **pastim said:**
> The patched kernel has been shown to work for all who have used it.  It will released in due course.  Keep watching the bug report at [https://bugs.launchpad.net/ubuntu/+s...x/+bug/1579190]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1579190")[COLOR=#000000]    to see when it is available*.*[/COLOR]

Great! Thanks for the info! Patched kernel is still working well for me too. I am monitoring the launchpad link.

---

### Post by pastim on 2016-06-29
There is now a proposed version of the kernel which can be installed for testing.   Please test if you can.  If we don't, the fix may not get into the next (or indeed any) release.

See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1579190](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1579190) for details.  I have included the steps I took to install the proposed kernel.

---

### Post by pastim on 2016-07-15
The fix is now in the latest linux kernel. On my version of xenial that's 4.4.0-31-generic #50-Ubuntu.  Versions have been released for older Ubuntu versions.:KS

---

