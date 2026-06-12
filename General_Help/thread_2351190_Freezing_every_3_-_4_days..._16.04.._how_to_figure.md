---
title: "Freezing every 3 - 4 days... 16.04.. how to figure out what's wrong?"
date: 2017-01-31
forum: General Help
---

### Post by robphelan on 2017-01-31
So, I've been running a headless NAS for the past 2 + years without an issue. But over the past month, my NAS has been randomly freezing up - I can't connect via VNC. It will work great for 3  to 4 days.. then suddenly I won't be able to connect - either from my main PC or via Plex.

I can still hear the fans running, so I don't think it has powered down.. I can fix it by holding the power button down to turn it off.. then turn it back on again. At that point, I can access via VNC.. then I need to re-mount my drives so that they'll be visible on the network.

i'm relatively religious about applying updates as they come along...

Are there any log files I can check? if so, where would I find them and what am I looking for?

thanks in advance,
rp.

---

### Post by DuckHook on 2017-02-01
Welcome to the forums, robphelan.

A few observations and recommendations:

[LIST=1]
[*]It is unusual to run a GUI on a server in Ubuntu, and even more unusual to then run it headless.
[*]Nor is it a good idea to "pull the plug" on running machine and especially on a server. Modern servers may hold a lot of cached writes in RAM. Pulling the plug could corrupt important data.
[*]The next time you get such a freeze-up, try plugging in a monitor and keyboard to see if things really are borked or if it's just your VNC that has crashed.
[*]Due to the this recent history, keep a spare keyboard plugged in and at least you can do a controlled shutdown using the REISUB process. Explanations and instructions [here]("http://www.howtogeek.com/119127").
[*]Install openssh-server in the NAS and at least try to SSH into your unresponsive machine to shut it down elegantly. SSH explanations and instructions [here]("https://help.ubuntu.com/lts/serverguide/openssh-server.html") and [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring").
[*]Examine your logs to see what problems have been recorded. Especially the various syslogs.
[/LIST]
On the strategic level, it is not a good idea to operate a NAS in the fashion that you have been. Anything that acts as a server should be as simple as possible, and this principle is compromised as soon as you add a GUI. It is even more compromised when you add the further complexity of a remote desktop and then run it headless. This makes for a very brittle system.

The drawbacks with this sort of unnecessary complexity are very evident in your latest problem. As it stands, we can't tell if the problem is a crashing remote desktop app, a crashing X session or a crashing OS. Of the three, it's only the last that is serious. The other two are superfluous and their presence only needlessly cloud any attempt at diagnosis.

Let's see what the results are of the detective work I've listed above.

---

### Post by dragonfly41 on 2017-02-01
I know that GUI's on servers are frowned upon and can be a channel for hackers.
But to solve your problem I would try installing webmin on your server (sudo apt-get install webmin) and use its powerful features to inspect your server.
webmin runs on port 10000.
You might then consider uninstalling webmin after its use as a diagnostic tool.

---

