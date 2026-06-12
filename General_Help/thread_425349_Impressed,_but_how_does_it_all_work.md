---
title: "Impressed, but how does it all work?"
date: 2007-04-27
forum: General Help
---

### Post by matt_garman on 2007-04-27
I've been using Linux exclusively for almost a decade now.  Started with Slackware, then Debian then Gentoo.

After being unable to get sleep and hibernate to work reliably on my Thinkpad T43 with Gentoo, I thought I'd give Ubuntu 7.04 a try.

Wow!  Very impressed.  Everything, so far, "just works".  Even the "hard" things, like wireless and sleep/hibernate.  I plugged in my girlfriend's iPod, and it was automatically detected!

My question is, ***how*** does it all work?  Are there GNOME daemons running that check for things like iPod connections?  Say I opted for a lightweight window manager like IceWM, *without* GNOME, would I be back to hand-configuring everything?  Does the installer just have excellent hardware detection that sets up everything correctly?

As you can see from my Linux history, I've always used the "non-newbie" distros, and that's intentional, since I like the "hands-on" and learning opportunities provided by them (especially gentoo, no better way to get your hands dirty).  Unfortunately, as I get older, I have less and less time to spend tinkering with things just to make them work.  That's why I've come to Ubuntu.

But I'd still like to know a little more about what's going on "under the hood", so to speak.

Thanks for a great distro!
Matt

---

### Post by xoros on 2007-04-27
You might want to read books on how operating systems work in general.

Plus this gives kind of general overview:
[http://computer.howstuffworks.com/question246.htm](http://computer.howstuffworks.com/question246.htm)

---

### Post by Tomosaur on 2007-04-27
While there are <desktop environment>-based daemons listening for stuff, yes, you shouldn't worry - if you use the other environments available to you (namely kubuntu-desktop, xubuntu-desktop, or ubuntu-desktop) via the package manager, you should enjoy the same ease of use.

However, there are daemons running which will detect stuff like that regardless of which environment you use, and the kernel is also compiled with support for this stuff.

On top of that, many of the packages have been modified (Usually the ones with 'ubuntu' somewhere in the title) to ensure smooth operation within the Ubuntu system. These same packages may not work correctly on other distributions, and the 'vanilla' versions of these packages may not provide the same functionality as the ubuntu ones do. There is actually a bit of resentment within other Linux communities because Ubuntu does this kind of thing, but the results speak for themselves.

Ubuntu also installs a fair amount of bloat, which is why even the 'lightweight' versions of Ubuntu (Xubuntu, for example) have higher system requirements than lightweight versions of other distributions. It is assumed that most users will have fairly modern computers, and thus the bloat doesn't have a noticeable impact, but we do get people complaining that Ubuntu is a 'slow' Linux. I personally wipe a fair amount of bloat out of my Ubuntu install when I upgrade versions, because there's a lot of stuff running which you probably don't need - but it does help to make Ubuntu 'just work'.

---

### Post by RedSquirrel on 2007-04-27
*gnome-volume-manager* is a pretty big component in terms of seeing things mounted transparently. You can use this without running GNOME. I run Fluxbox and I personally don't use *gnome-volume-manager* but a few searches will tell you all about it.

PS - I believe you can get your hands even dirtier with [LFS]("http://www.linuxfromscratch.org/"). ;)

---

### Post by matt_garman on 2007-04-27
> **Tomosaur said:**
> While there are <desktop environment>-based daemons listening for stuff, yes, you shouldn't worry - if you use the other environments available to you (namely kubuntu-desktop, xubuntu-desktop, or ubuntu-desktop) via the package manager, you should enjoy the same ease of use.

Hmm, but those are all complete *desktop environments*, right?  What if I just want, Fluxbox or IceWM or Enlightenment as my Window Manager, but no desktop environment.  Will I lose all the "magic"?

> **Tomosaur said:**
> However, there are daemons running which will detect stuff like that regardless of which environment you use, and the kernel is also compiled with support for this stuff.

Ubuntu also installs a fair amount of bloat, which is why even the 'lightweight' versions of Ubuntu (Xubuntu, for example) have higher system requirements than lightweight versions of other distributions. It is assumed that most users will have fairly modern computers, and thus the bloat doesn't have a noticeable impact, but we do get people complaining that Ubuntu is a 'slow' Linux. I personally wipe a fair amount of bloat out of my Ubuntu install when I upgrade versions, because there's a lot of stuff running which you probably don't need - but it does help to make Ubuntu 'just work'.

I see.  I guess the question I really wanted to ask, then, is all the bloat necessary for the ease-of-use?  I mean, my hardware is fortunately fast enough to run Ubuntu without any noticeable performance effects... but, (1) I have this compulsion to constantly tweak things and (2) I like that smug feeling that I've optimized all the bloat away.  :)

So maybe I should ask more specific questions, such as:[list][*]What controls the wireless network?  Is it just wpa_supplicant running under the covers?
[*]What about all the ACPI bindings, such as lid-closing, the volume buttons, screen brightness, etc
[*]How about sound?  Is it ESD or the gnome-equivalent or just ALSA doing the mixing?
[*]Is the sleep/hibernate functionality achieved through the original kernel suspend interface, or swsusp2, etc?
[*]I was really impressed that my laptop automatically switched between wireless and wired networking when I'd dock/undock it.  Is this using, e.g. ifplugd or whatever it's called?[/list]

A lot of this just stems from the difficulty I had getting suspend to work reliably under gentoo.  E.g., does Ubuntu just have the "magic" suspend2.conf file that works always?  Or was the correct configuration determined during installation?  And if the latter is true, is someone maintaining a giant collection of working profiles or something?

> **Tomosaur said:**
> On top of that, many of the packages have been modified (Usually the ones with 'ubuntu' somewhere in the title) to ensure smooth operation within the Ubuntu system. These same packages may not work correctly on other distributions, and the 'vanilla' versions of these packages may not provide the same functionality as the ubuntu ones do. There is actually a bit of resentment within other Linux communities because Ubuntu does this kind of thing, but the results speak for themselves.

It's open source isn't it?  :)  IMO, that's the whole point of open source: make it as easy as possible for someone to enhance/fix/change/integrate the way something works (or doesn't work).  And really good modifications should make it back into the original source anyway.  But I digress!

I'm really just awed... I mean, virtually every piece of hardware I've ever used with Linux I've had to do some hand configuration.

Thanks!
Matt

---

### Post by xoros on 2007-04-27
> **matt_garman said:**
> I see.  I guess the question I really wanted to ask, then, is all the bloat necessary for the ease-of-use?  I mean, my hardware is fortunately fast enough to run Ubuntu without any noticeable performance effects... but, (1) I have this compulsion to constantly tweak things and (2) I like that smug feeling that I've optimized all the bloat away.  :)


It would be nice to see a hardware manfacturer(s) create a STANDARD set of equipment with a STANDARD linux os in which everything would work SPECIFIC to it, ALONE !!

To me that would be the end-all of the linux desktop problems with all its bloat/bugs.  JMHO

Maybe this already exists ?

---

### Post by Darwin Award Winner on 2007-07-16
> **matt_garman said:**
> So maybe I should ask more specific questions, such as:[list][*]What controls the wireless network?  Is it just wpa_supplicant running under the covers?
[*]What about all the ACPI bindings, such as lid-closing, the volume buttons, screen brightness, etc
[*]How about sound?  Is it ESD or the gnome-equivalent or just ALSA doing the mixing?
[*]Is the sleep/hibernate functionality achieved through the original kernel suspend interface, or swsusp2, etc?
[*]I was really impressed that my laptop automatically switched between wireless and wired networking when I'd dock/undock it.  Is this using, e.g. ifplugd or whatever it's called?[/list]

A lot of this just stems from the difficulty I had getting suspend to work reliably under gentoo.  E.g., does Ubuntu just have the "magic" suspend2.conf file that works always?  Or was the correct configuration determined during installation?  And if the latter is true, is someone maintaining a giant collection of working profiles or something?


[list][*]ACPI: Look in /etc/acpi/events for the bindings and in /etc/acpi for the scripts that they execute. Many of the scripts there have a feature to execute custom scripts before or after. This feature allowed me to fix a problem by simply creating a new script in the right place rather than editing an existing one (which would then be overwritten upon each update).
[*]Sound mixing, etc.: I believe that the installer performs some hardware detection. If it detects a sound card without a working hardware mixer, it enables dmix. GNOME uses ESD on top of this, and KDE uses arts, as usual. There's a cli utility called asoundconf to add or remove common options from /etc/asound.conf.
[*]Sleep/Hibernate: Take a look in /usr/lib/hal/scripts/linux/. Basically, the scripts for suspend/hibernate go through a list of known suspend utilities, all of which, I believe, ultimately make use of swsusp2.
[*]Network autoconfiguration: Ubuntu 7.04 now comes with NetworkManager by default. It uses wpa_supplicant under the hood to connect to wireless networks, and it connects to wired networks by simple DHCP.[/list]

---

