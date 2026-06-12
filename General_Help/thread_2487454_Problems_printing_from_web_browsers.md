---
title: "Problems printing from web browsers"
date: 2023-06-05
forum: General Help
---

### Post by jet-bundle on 2023-06-05
I have a new-ish Dell XPS13 Plus running Lubuntu 22.04 which has a strange problem printing from web browsers.

There are three browsers installed (Firefox 113.0.2, Opera 99.0.4788.47 and Chromium 113.0.5672.126) and one printer (Canon LBP7110Cw). If I want to print directly on paper, I have to use Chromium because both Firefox and Opera have only one destination shown in the print menu (Save to PDF) and don't list the Canon printer at all.

There is also second problem, perhaps related to the first, but perhaps not. It is that when printing a page such as OpenStreetMap to PDF from either Chromium or Opera I obtain a file of around 400kB, whereas doing the same from Firefox I obtain a 4MB file with the map itself rendered as a somewhat fuzzy image although the header and footer are printed cleanly as text.

I wonder if anyone might be able to suggest some settings I might look at in order to fix these problems?

(I should also mention that I had to reinstall Firefox as the original version installed with the OS crashed when attempting to print. Both the original and reinstalled versions were snap packages.)

---

### Post by tech211fog on 2023-06-05
Have you done an update of the printer or the browser recently? That might be a good place to start. If not, you could also try re-installing one of the browsers, and see if that helps you out.

---

### Post by jet-bundle on 2023-06-06
The update history is simple. I installed Lubuntu in a separate partition (the machine is just a few weeks old, and came with Ubuntu pre-loaded). Then, amongst other things, I installed the Canon printer, followed by Chromium and Opera. Afterwards I reinstalled Firefox because the original version (110.0) crashed when attempting to print.

I have now deleted and reinstalled Firefox, so that it's now 114.0, but after that it still didn't show the Canon printer. I then deleted and reinstalled the printer; still Firefox (and Opera) don't show it, whereas Chromium does, and I can also print from other software such as LibreOffice, Evince, GIMP, ... .

As an aside: on another, slightly older, Dell XPS13, I carried out a similar installation routine using the same printer and printer-driver but without installing the two extra browsers. On that other machine, Firefox shows the Canon printer as a possible print destination. I also have an HP desktop machine, with both Firefox and Chromium installed, and again both browsers can see the Canon printer. 

So it's just a problem on this new XPS13 Plus, in that neither Firefox nor Opera can see the Canon printer, whereas Chromium and the other software packages can.

(I think the fuzzy pdf produced by Firefox is a separate problem, as it also appears on the other two machines. I'll investigate that elsewhere.) 

Any more suggestions on how I might proceed would be gratefully received.

---

### Post by jet-bundle on 2023-06-11
I've made some progress. I believe that Firefox and Operas are being denied permission to access CUPS, whereas Chromium appears not to have this problem. I'd be grateful for suggestions on how to resolve this.

I've come to this conclusion because by Dell XPS 13 Plus has two separate installations of Lubuntu 22.04, with the second copy having only ba minimal set of extra software, and with shared home folders in a separate partition. If I boot the second copy, I see that Firefox is able to print to the Canon printer without any problem. I also see the following:
 ```
sudo dmesg | grep -i cups
[    5.267890] audit: type=1400 audit(1686489651.112:41): apparmor="DENIED" operation="capable" class="cap" profile="/usr/sbin/cupsd" pid=913 comm="cupsd" capability=12  capname="net_admin"
```
and this doesn't changed after printing from Firefox. On the other hand, if I boot the main installation, I see initially
```

[    5.147354] audit: type=1400 audit(1686511703.996:33): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap-update-ns.cups" pid=1084 comm="apparmor_parser"
[    5.150679] audit: type=1400 audit(1686511704.000:38): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.cups.cupsaccept" pid=1093 comm="apparmor_parser"
[    5.150686] audit: type=1400 audit(1686511704.000:39): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.cups.cupsdisable" pid=1096 comm="apparmor_parser"
[    5.150689] audit: type=1400 audit(1686511704.000:40): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.cups.cancel" pid=1091 comm="apparmor_parser"
[    5.150692] audit: type=1400 audit(1686511704.000:41): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.cups.accept" pid=1090 comm="apparmor_parser"
[    5.150694] audit: type=1400 audit(1686511704.000:42): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.cups.cups-browsed" pid=1092 comm="apparmor_parser"

```
and then, after attempting to print from Firefox,
```

[   73.586393] audit: type=1400 audit(1686511772.860:105): apparmor="DENIED" operation="connect" class="file" profile="snap.firefox.firefox" name="/run/cups/cups.sock" pid=2213 comm=4267494F5468727E506F6F6C202331 requested_mask="wr" denied_mask="wr" fsuid=1000 ouid=0
[   73.586414] audit: type=1400 audit(1686511772.860:106): apparmor="DENIED" operation="connect" class="file" profile="snap.firefox.firefox" name="/run/cups/cups.sock" pid=2213 comm=4267494F5468727E506F6F6C202331 requested_mask="wr" denied_mask="wr" fsuid=1000 ouid=0
[   73.586442] audit: type=1400 audit(1686511772.860:107): apparmor="DENIED" operation="connect" class="file" profile="snap.firefox.firefox" name="/run/cups/cups.sock" pid=2213 comm=4267494F5468727E506F6F6C202331 requested_mask="wr" denied_mask="wr" fsuid=1000 ouid=0
[   73.586711] audit: type=1400 audit(1686511772.860:108): apparmor="DENIED" operation="connect" class="file" profile="snap.firefox.firefox" name="/run/cups/cups.sock" pid=2213 comm="firefox" requested_mask="wr" denied_mask="wr" fsuid=1000 ouid=0

```

So I guess I'm looking for advice on how to tell apparmor that Firefox and Opera are OK?

---

### Post by jet-bundle on 2023-06-13
I have now been able to confirm the cause of the problem, and to resolve it, so I'll mark this thread as SOLVED.

The problem was in the apparmor profile [COLOR=#ff0000]snap.firefox.firefox[/COLOR], which is in [COLOR=#ff0000]/var/lib/snapd/apparmor/profiles[/COLOR]  I compared the two copies of this file in my two installations of 22.04, and discovered that the profile in my main installation missed out the following block:
```
# Allow communicating with the cups server for printing and configuration.

#include <abstractions/cups-client>
/{,var/}run/cups/printcap r,

# Allow receiving all DBus signal notifications from the daemon (see
# notifier/dbus.c in cups sources)
dbus (receive)
    bus=system
    path=/org/cups/cupsd/Notifier
    interface=org.cups.cupsd.Notifier
    peer=(label="{unconfined,/usr/sbin/cupsd,cupsd}"),
```
Copying the profile from the backup installation to the main installation, and therefore restoring the missing block to the profile, has allowed printing to my Canon printer from Firefox in the main installation.

---

