---
title: "vino-server stopped working after 14.04 upgrade"
date: 2014-04-21
forum: General Help
---

### Post by toypilot on 2014-04-21
Hi all, 

I have just upgraded to 14.04 and and can no longer connect to my server over vnc.

This was all working correctly prior to upgrade on 13.10

Remote sharing was turned off when I went in to check

The error that I get is from REALVNC saying that the encryption level does not match and that I will need to select a lower encryption or upgrade REALVNC. I have upgraded REALVNC with no joy.

I get the same result after turning off the firewall on the machine.

I have to say, remote access breaks on nearly every ubuntu upgrade I have ever done, so I have used X11VNC in the past, but that broke when Unity came in.

Any help would be appreciated.

TP

---

### Post by mjuhasz on 2014-04-21
Vino is the vnc server used for remote desktop access in Ubuntu. The default setting to require encryption was changed from false to true, however Vino does not support some common encryption methods, like the one RealVNC is trying to use.

For the time being the only solution is the disable encryption for vino:

[FONT=Courier New]gsettings set org.gnome.Vino require-encryption false[/FONT]

This is the relevant [bug report]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/1281250").

---

### Post by toypilot on 2014-04-21
Thanks for that.

---

### Post by rompelstilchen on 2014-06-26
wow thanks for the solution, after rdp bug solved, vnc now is not working, lol what a piece of junk.

---

