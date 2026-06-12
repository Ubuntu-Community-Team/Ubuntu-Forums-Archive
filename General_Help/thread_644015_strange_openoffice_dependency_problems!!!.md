---
title: "strange openoffice dependency problems!!!"
date: 2007-12-18
forum: General Help
---

### Post by x3roconf on 2007-12-18
I'm running ubuntu 7.10 q6600@2,4ghz 2gb ram gf 8800GT

subprocess post-installation script returned error exit status 49
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.3.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 1:2.3.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-impress; however:
  Package openoffice.org-impress is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
 openoffice.org depends on openoffice.org-math; however:
  Package openoffice.org-math is not configured yet.
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
 openoffice.org depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gtk depends on openoffice.org-style-human; however:
  Package openoffice.org-style-human is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-common
 openoffice.org-style-human
 python-uno
 openoffice.org-writer
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gtk
 openoffice.org-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by prince_niceguy on 2007-12-21
I am also facing the same problem.... not sure how to solve this...

---

### Post by forestpixie on 2007-12-21
what are you trying to do - install it?

---

### Post by prince_niceguy on 2007-12-21
I was just trying to upgrade my system after doing apt-get update.

Searched on the net and it seems there is some issue in debian sources too. This might have ended up in ubuntu too.

---

### Post by forestpixie on 2007-12-21
did you remove the ubuntu version and replace it with the openoffice version - I got a vague recollection of the same thing - and that's what I had done previously

if you did I THINK you need to remove openoffice and install ubuntu-desktop to get it back to a state that will upgrade

---

### Post by prince_niceguy on 2007-12-21
I tried doing it already, uninstall ttf-opensymbol and uninstall open-office and reinstall the same, but it does not resolve the issue. not sure where the problem is... seems ttf-opensymbol is not able to generate some font cache or something

---

### Post by forestpixie on 2007-12-21
did you try installing ubuntu-desktop or just oo

---

### Post by prince_niceguy on 2007-12-21
i tried installing ubuntu-desktop. as on uninstall of oo., ubuntu-desktop was automatically removed.

---

### Post by forestpixie on 2007-12-21
don't really know then tbh - I got round by doing as I'd said

is it possible to do an install instead of upgrade?

---

### Post by prince_niceguy on 2007-12-21
OK here is the brief summary of what has happened.

I recently got a new T60 laptop. I installed gutsy on that and it gave me icon to instlal 146 updates, so I typed the command

sudo apt-get upgrade

After that i got this oo error as ttf-opensymbol was not getting configured and hence the dependencies were not getting satisfied.

So, I uninstalled oo, opensymbol and it automatically removed ubuntu-desktop.

After that I issued the command

sudo apt-get install ubuntu-desktop.

But still the error comes up.

---

### Post by forestpixie on 2007-12-21
oh misunderstood that then

when you uninstalled what did you uninstall - when I did it I used synaptic - searched for openoffice and removed all of them,

 I then installed from the oo deb instead of the ubuntu version - since then I've pinned oowrite etc as I don't want the ubuntu version, but any other updates I've accepted

---

### Post by prince_niceguy on 2007-12-21
is there some advantage in using the oo version over ubuntu?

---

### Post by prince_niceguy on 2007-12-21
Not sure how but now the problem is resolved. It installed opensymbol correctly and all the chain dependency was satisfied.

thanks for you inputs

---

