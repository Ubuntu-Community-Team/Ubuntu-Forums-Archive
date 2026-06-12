---
title: "XRDP Odd Behavior Connects just fine but cant see active program windows"
date: 2014-05-02
forum: General Help
---

### Post by ghostcoredevelopme on 2014-05-02
Hello all

I am having an odd issue here with XRDP and xubuntu

I can connect just fine to my desktop computer via xrdp even from windows.

but what happens is what I thought was starting a new session is in fact a display issue.

when i connect it "Looks" like a new default XFCE environment but I then realized it wasn't it was in fact my current session but the remote wasn't showing apps like my running virtualbox my terminal etc this was confirmed even more by trying to launch a prog remotely and seeing it on the local display perfectly fine but not via the remote display.

any ideas on this?

System: Xubuntu 64 14.04 AMD Based
WM: XFCE

---

### Post by Toz on 2014-05-02
How are you sure that you are using the same session? xrdp, by default, creates a new remote connection every time you connect on a different port resulting in a new session. There is a bug report for that [here]("https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/1194937").

What I do as a workaround, is edit the /etc/xrdp/xrdp.ini file and make a copy of the xrdp1 entry, the only change being that I change "port=-1" to "port=xxxx", where xxxx is the port that I currently connected to (this can be seen in the connection dialog). On subsequent reconnects, I connect to the same session. Note that if you restart xrdp or reboot, you may get a new port, and you'll have to edit that entry again.

---

### Post by ghostcoredevelopme on 2014-05-02
How do I know...

I already stated that 

"[COLOR=#000000]this was confirmed even more by trying to launch a prog remotely and seeing it on the local display perfectly fine but not via the remote display."[/COLOR]

[COLOR=#000000]the system i am accessing is about ummmmmm 1 foot away from me thus the local display is quite visible 

logged in to target system locally 

access via xrdp

attempt usage

rdp display does not draw active windows or show in menu bar

local display does show active windows (including those launched via xrdp)

so that tells me im accessing the current running session.

I dont think that bug currently applies to me as i rebuilt xrdp from source in order to get it running.

Im not a pro by any means but im leaning in the direction of composit graphics XRDP doesnt support 32 bit color depth and any WM using a composit backend seems to get dropped into a fallback mode. to me these seem like limitations.

also its obvious xrdp at least in it's current state is more problematic then it's worth.

think I need an alternative.

the whole goal was to get xrdp going so I could connect via windows rdp client from say a school computer while doing labs etc because we cant just toss VNC on what ever school system im at.

but im thinking im gonna need a better solution and one not so limited ...honestly with all the crap xrdp has been giving me....and others it seems way not worth it for a broken rdp client running at 24bit (if your lucky) color depth and no composit (nitpicking i know)

that being said... whats another alternative setup

Note figured id try a couple of other things well just one....knoppix xrdp works flawlessly i can only guess its due to being a older version of xrdp and working with a lightweight WM.

could this be a buntu issue? mint had the same issues [/COLOR]

---

