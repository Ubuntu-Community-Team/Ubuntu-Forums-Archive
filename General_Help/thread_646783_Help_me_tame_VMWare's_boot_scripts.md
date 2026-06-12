---
title: "Help me tame VMWare's boot scripts"
date: 2007-12-21
forum: General Help
---

### Post by vek on 2007-12-21
Hi there. I'm currently running ubuntu 7.10 on a real partition on one of my disks (I'm using it right now, in fact), and often boot to it... But I also use that same partition via VMWare (which I am doing now) for most of my development.

I can muddle through it (each time I switch from virtual to real, things need changing, configs need altering)... but in an attempt to step up from newbie to non-newbie about these things, I'm trying to learn more about the system, perhaps save myself a bit of headaches here.

I'm hoping someone knows what VMWare is doing to the system everytime it starts.  For example, when I shut the system down from virtual mode, and reboot the machine for real,  (non-vmware), the vmware guest services tools seems to do some file copying and linking...

It links or copies my xorg.conf from somewhere to somewhere, so that its a different xorg.conf.  It does some other switcharounds too, I guess with networking and input devices and so on.  It seems to be trying real hard, but of course, it doesn't work all that well.  Perhaps its backing up the 'old' xorg.conf and helpfully trying to switch it out, or something.   Try as I might, I can't figure out where its copying it from, or where the script that its running is doing it - I essentially have three different configs (virtualized, non-virtual single screen, and non-virtual dual screen) and would prefer to have more control over which one runs when.

So currently whenever I reboot for real, I have to first boot up, then go into console mode since X wont start, and while it has a panic attack flickering on and off over and over, I have to edit/copy my backup configs over the current xorg.conf.  And of course, that makes it work.  But then when I try to go back into a virtualized environment, I have to do the reverse again each time...

---

