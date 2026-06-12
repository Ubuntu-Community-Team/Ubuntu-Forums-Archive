---
title: "Whither 6.06.2 DESKTOP?"
date: 2008-02-04
forum: General Help
---

### Post by danfluidmind on 2008-02-04
I've downloaded 6.06.2 server edition just fine. But when I try to download Desktop edition, I get the 6.06.1 file, even though the link is on the 6.06.2 download page. Does anyone know what's going on there? Is the desktop 6.06.2 version just not ready yet? Is there not going to be a 6.06.2 for desktop? Either way, it would be helpful to put something on the download page explaining why 6.06.1 is still there for desktop.

Thanks
--Dan

---

### Post by justin whitaker on 2008-02-04
> **danfluidmind said:**
> I've downloaded 6.06.2 server edition just fine. But when I try to download Desktop edition, I get the 6.06.1 file, even though the link is on the 6.06.2 download page. Does anyone know what's going on there? Is the desktop 6.06.2 version just not ready yet? Is there not going to be a 6.06.2 for desktop? Either way, it would be helpful to put something on the download page explaining why 6.06.1 is still there for desktop.

Thanks
--Dan

Most of the fixes were on the server side. LTS drops for the desktop when Hardy releases, since that is the new LTS (ex-Kubuntu). 

You can install the server version, and install the Ubuntu-Desktop...et voila, 6.06.2.  :)

---

### Post by danfluidmind on 2008-02-04
> **justin whitaker said:**
> You can install the server version, and install the Ubuntu-Desktop...et voila, 6.06.2.  :)

Thanks. I tried that on a Dell Edge server and it whacked it out. Now I get no video at all after it boots, and I can't even get to a console with CTRL-ALT-F1. Very odd. I wanted to try reinstalling right from a 6.06.2 desktop CD. Oh well.

Thanks for the reply
--Dan

---

### Post by justin whitaker on 2008-02-04
> **danfluidmind said:**
> Thanks. I tried that on a Dell Edge server and it whacked it out. Not I get no video at all after it boots, and I can't even get to a console with CTRL-ALT-F1. Very odd. I wanted to try reinstalling right from a 6.06.2 desktop CD. Oh well.

Thanks for the reply
--Dan

That's really weird. Can you load safe mode, or log in via console?

---

### Post by danfluidmind on 2008-02-04
> **justin whitaker said:**
> That's really weird. Can you load safe mode, or log in via console?

It won't let me get to the console. CTRL-ALT-F1 does nothing. I just booted into safe mode and it booted fine to a console login screen. I checked xorg.conf and the highest resolution in there was 1025x768, which is correct (that's all this Compaq KVU device will handle). So it "should" be okay. But when I boot normally, after the booting up process, the screen goes blank and everything seems to lock up. I can't get to virtual terminals. And I can't even ping the machine.

So I got rid of the S13gmd link in /etc/rc2.d so that it doesn't boot into X and I'm okay for now. But I'd like to find out what's going on.

Thanks
--Dan

---

