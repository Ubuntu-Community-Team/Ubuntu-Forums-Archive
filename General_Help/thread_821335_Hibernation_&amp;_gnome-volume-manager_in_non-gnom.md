---
title: "Hibernation &amp; gnome-volume-manager in non-gnome environment"
date: 2008-06-07
forum: General Help
---

### Post by Krank on 2008-06-07
OK, so I'm putting together a really lightweight HTPC system from parts I happen to have lying around. I really don't have the cash to shell out for new hardware, so I'm more or less stuck with what I got: a 1.5 ghz AMD, 512 mb's of RAM and an old GeForce FX5500. It's not much, I know, and I dunno if it'll handle any advanced stuff - HD etc.

Aaaaanyways, the box is currently working - a simple Ubuntu install with XBMC on top, a few xmodmap scriptie stuff to handle my very nonstandard IR-USB remote...

However, I've hit a few snags:

1. Hibernate. It works on a clean install from the shipped Ubuntu Hardy CD. When I've aptitude upgrade'd the system, it doesn't. Somewhere in those 129 updates is the problem, and I got no idea where. I can go into hibernation well enough, but not restore - it gets stuck on the "kinit: trying to resome from /dev/disk/by-uuid/d25-and-then-some-more-numbers" prompt. Not a really major issue, but it'd be nice to have the feature, you know?

2. Gnome looks nice, but it's horribly bloated - at least for the purposes of a HTPC. I really just need x.org and XBMC, since XBMC can be run as a Xsession... However, there's this one feature I just can't live without: Gnome-volume-manager. I'd very much like to be able to hotplug USB drives and keys, and gnome-volume-manager seems toe only solution here. However, I've been unable to start it in blackbox or any other lightweight non-gnome environment. All the guides and howtos for other non-ubuntu systems refer to running gnome-volume-manager in a terminal, but that command does not exist - and the /usr/lib/gnome-volume-manager/gnome-volume-manager , normally autorun in the gnome system, seems to do absolutely nothing, then exit.



So:

[b]1. Anyone experience the same kind of locked-up hibernation restore procedure I have? And what did you do to fix it?[b]

and...

**2. Any ideas on how to make automounting work without using any of the major window managers?**


I'd be very greateful for even a second of your time and the slightest pointer in the right direction. I am by no means a newb in Linux, I just need a pointer or two to get me going in the right direction...

---

### Post by Phobbes on 2008-11-21
I just put up [this blog post]("http://airwav.es/2008/11/21/volume-management-without-nautilus/") describing how to set up gnome-volume-manager to work without nautilus.

Hopefully it will be helpful, if you haven't fixed this problem yet.

-spencer

---

