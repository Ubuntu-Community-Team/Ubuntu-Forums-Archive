---
title: "broken dependencies after upgrade to breezy"
date: 2005-10-17
forum: General Help
---

### Post by dsethuraman on 2005-10-17
Hi all
i upgraded from Horay to Breezy and have run into 'broken dependencies'. the error message during the upgrade is as below. It also killed my xserver but i fixed it with the reconfigure xserver-xorg command.. I have also tried synaptic etc, but it too returns the same errors. Any help would be much appreciated

Running newaliases
 * Starting Postfix Mail Transport Agent...                                     postfix/postfix-script: fatal: the Postfix mail system is already running
                                                                         [fail]
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mutt:
 mutt depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mutt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing lsb-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-graphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-cxx:
 lsb-cxx depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-cxx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core; however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
 lsb depends on lsb-cxx; however:
  Package lsb-cxx is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postfix
 mailx
 mutt
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by eivind on 2005-10-17
Unless you need to send mail locally from your machine, that is: If you don't use internet mail or your ISP's mail servers, you can probably safely remove postfix. This is what you do (from a terminal, mind you):

sudo apt-get remove postfix

And then, to give apt-get a chance to do its part and fix the remaining packages, you can do 

sudo apt-get -u dist-upgrade

The -u option shows you which packages will be upgraded (if any), so you can abort if you don't want to do the upgrade.


This is a very basic answer, and not authoritative, but it may help.

Cheers,

Eivind

---

