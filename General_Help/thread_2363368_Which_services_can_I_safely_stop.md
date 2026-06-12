---
title: "Which services can I safely stop?"
date: 2017-06-09
forum: General Help
---

### Post by csdgbas on 2017-06-09
I realise that the answer will be "it depends" :) but even a general idea, or a "DON'T TOUCH missilelaunch.service, YOU WILL DESTROY EVERYTHING!" indication about services I definitely cannot stop would help.  The list of running services is at [http://paste.ubuntu.com/24814470/](http://paste.ubuntu.com/24814470/)

---

### Post by &amp;KyT$0P# on 2017-06-09
What functionality do you need?

---

### Post by csdgbas on 2017-06-10
> **halogen2 said:**
> What functionality do you need?

Just the ability to turn the computer on, log on and out, and turn it off again.  I'll add whatever else I want as I require it.

---

### Post by Autodave on 2017-06-10
I prefer to go to Settings -> Session & Startup -> Application Autostart. From there, you can disable things a lot more safely. For instance, Bluetooth manager: probably not needed unless you are running wireless mouse or keyboard. "Print queue applet is another. If you don't use a screen saver, another.

---

### Post by missmoondog on 2017-06-10
i used to look for answers to this question, but never really found what impressed me as far as speeding up my systems, so i never turned anything off except printing, and even now i don't think i have that disabled.

never really seemed to be as noticeable of a difference when running linux as there is when running windows!

---

### Post by &amp;KyT$0P# on 2017-06-10
[LIST]
[*]avahi-daemon.service can be safely disabled.  dbus-org.freedesktop.Avahi.service looks related and can probably be disabled as well.
[*]If you don't use a VPN, it's probably safe to disable openvpn.service
[*]php7.0-fpm.service can probably be safely disabled
[*]If your computer doesn't need to run an rsync server for backups or whatever, rsync.service can probably be disabled
[*]If you use straight iptables for your firewall, you don't need ufw.service
[*]If you don't want automatic security updates, you can disable unattended-upgrades.service (but this might make your system less secure)
[/LIST]

I'm not sure whether you'll get problems from disabling the snapd services.


There are a few services I don't know what they are.  Research before deciding about these.
[LIST]
[*]click-system-hooks.service
[*]dns-clean.service
[*]ondemand.service
[*]repowerd.service
[*]urfkill.service
[/LIST]


As for the rest, disabling could break your system.  So I don't recommend it. :)

---

### Post by csdgbas on 2017-06-10
Thanks, h2.  My research had already failed to find anything about the second list, but I didn't know what the ones in your first list did either.  At some point, given the length of the list and the constant rebooting to find out whether disabling something had broken anything, I gave up on experimentation and decided to ask the experts.  You did not disappoint :)

---

### Post by &amp;KyT$0P# on 2017-06-10
You're welcome.

---

### Post by VMC on 2017-06-11
> **csdgbas said:**
> I realise that the answer will be "it depends" :) but even a general idea, or a "DON'T TOUCH missilelaunch.service, YOU WILL DESTROY EVERYTHING!" indication about services I definitely cannot stop would help.  The list of running services is at [http://paste.ubuntu.com/24814470/](http://paste.ubuntu.com/24814470/)

Read this [cleanup document]("https://www.linux.com/learn/cleaning-your-linux-startup-process").

---

