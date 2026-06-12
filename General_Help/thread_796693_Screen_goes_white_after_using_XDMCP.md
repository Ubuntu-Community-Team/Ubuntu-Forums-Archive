---
title: "Screen goes white after using XDMCP"
date: 2008-05-16
forum: General Help
---

### Post by kevinatkins on 2008-05-16
Hi,

My main PC is running Ubuntu 8.04, using an nVidia graphics adaptor. Quite often, I like to log in to my server running Debian, for which I use XDMCP. If I have desktop effects enabled on the Ubuntu box, when I log back out of my server, instead of dropping back to a locked session / password prompt on the Ubuntu box, I just get a white screen. I have to restart X to restore operation.

It's not a real problem - I just tend to run with desktop effects disabled - but I'm wondering if anyone has experienced similar, and if so, whether you've been able to solve it?

Cheers.

---

### Post by Vorl the Magnificent on 2008-12-05
I have a similar issue w. the white screen and XDMCP, but I don't think mine is Nvidia-related.  I can't really figure out what's going on.  Here's the setup:


I have three PCs on my home network, all running *buntu distros.  They are:

JENOVA -- Dell Dimension 3000 with integrated graphics (intel?) running Ubuntu 8.10 at 1024x768 resolution;

WARMECH -- Lenovo Thinkpad X61 with integrated graphics (intel?) running Ubuntu 8.04 at 1024x768 resolution; and

KAINAZZO -- Compaq Evo D500 with its old, sad, oem Nvidia Vanta graphics card.  This box runs Xubuntu 8.10 at 1024x768 resolution.  KAINAZZO is headless, & is presently accessed only by SSH & XDMCP.


Here are three scenarios:

(1) I'm logged into JENOVA, and can do two secondary logins and login on KAINAZZO and WARMECH via XDMCP.  No problems here -- I just switch between sessions on all three machines using Ctrl+Alt+F(7-9).  All is well.

(2) I start up WARMECH, and without logging in to WARMECH, I start an XDMCP session and log into JENOVA.  No problems here -- WARMECH works effectively as a dedicated terminal for JENOVA.

(3) I'm logged into WARMECH, and decide to open a secondary login and log into KAINAZZO via XDMCP.  Dandy fine.  No problems -- I just switch from WARMECH to KAINAZZO using Ctrl+Alt+F(7-8 [or whatever]).

Ah!  But...

(4) If I'm logged into WARMECH and I open a second login and attempt to login to JENOVA via XDMCP, JENOVA's login screen pops up fine... but once I've logged in, it throws up a solid white screen with JENOVA's regular mouse cursor.  The machine truly is logged in, b/c (a) the mouse cursor changes shape by context (e.g., if I've blindly opened some app, the cursor will give me resize cursors when I approach the edge of the (invisible) app behind the white screen, and (b) when I blindly access a gnome terminal and reboot, it works.  Also, if I do Ctrl+Alt+Backspace, it kills X, and drops me to my original WARMECH terminal.  The desktop appears to be working, b/c when I kill X or blindly reboot JENOVA, the white disappears for a split second and reveals JENOVA's desktop background image before dropping me to WARMECH.

If, in (4) above, I've logged into KAINAZZO and JENOVA from WARMECH via XDMCP, the KAINAZZO session and the local WARMECH session display fine -- it's just the JENOVA session that's hosed.


PROBLEM SUMMARY:

If I login to WARMECH, do a secondary login, and then login to JENOVA via XDMCP, I get a white screen.  WARMECH as dedicated terminal to JENOVA does fine.

Help? :grin:

---

### Post by Vorl the Magnificent on 2008-12-06
"Knock, knock."

"Who's there?"

"Bump."

"Bump who?"

"Well, actually, it's not a person... I'm bumping this thread."

Bump.

---

### Post by helpdeskdan on 2009-10-09
A note for others: 

I had desktop effects disabled, but still had the white screen.  Upon further investigation, I found compiz was still running, even though desktop effects were disabled.  Simply killing the process restored the desktop.  

To fix this, I logged into that account locally, enabled desktop effects, then disabled then again.  This seemed to permanently fixed the problem.

---

