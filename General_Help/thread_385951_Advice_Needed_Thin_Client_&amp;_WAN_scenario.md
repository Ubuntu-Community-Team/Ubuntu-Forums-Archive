---
title: "Advice Needed: Thin Client &amp; WAN scenario"
date: 2007-03-16
forum: General Help
---

### Post by Sternfan on 2007-03-16
Looking for advice on Thin Client (or Hybrid Client).  Any comments welcome.

Scenario...

PCs - Low end PC = 500mhz/256mb ram.  Average PC = 1gz/256mb ram.  These will continue to be upgraded as time allows...

Concurrent Users (avg/max):  North = 20/30  Central = 20/30.  South = 15/20.  Some users occasionally roam (a user based at South may logon to a PC at North for instance).

APPS:  vast majority of users will use OpenOffice and Email.

Three locations: North, Central and South. 

WAN speeds: Connecting North & Central = full T-1 (1.44mb).  Connection between South & Central = 1/2 T-1 (768mb).

LAN speeds: all sites = switched, GB to servers and 100mb to clients.  Internet is based out of Central = full T-1.

Goal: One terminal server at Central (not purchased yet - assume it meets speed/space needs).  I want centralized backups, etc.  There will also be a new email/groupware server at Central.

Printers are spread out - multiple IP printers and shared local printers.  Users need to print to multiple different printers as needed.

My questions:  Does this seem feasible?  Is the bandwidth between the locations enough?  In investigating thin clients, I ran across "Hybid Clients" - where a lot of the computing takes place on the remote client (local apps), instead of everything on the server - saving on bandwidth usage.  I like this idea, but cannot find much information on it - any book recommendations etc?  Also, the issue of shared printing with thin clients confuses me - would a hybrid client solve this?  There would be an OS there to install and share the printer (seems easier to me).  LTSP 5 appears to have just come out (no docs yet) - anyone have any comment on it?  What was your experience with it?

Thanks,
Sternfan

---

### Post by waltrothfuss on 2007-04-01
Seems like it is being worked on.  More info at:

'http://dtrask.wordpress.com/2006/11/15/my-report-from-uds-mountain-view/

under the section headings, Fat Client and Local Apps.

---

