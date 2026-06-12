---
title: "always fixing bugs: why does Linux/Ubutu have high CPU crap?"
date: 2013-02-15
forum: General Help
---

### Post by sidewalkcynic on 2013-02-15
It does not seem to matter, what I do, or other people as well, as evident when I Google search for the app that the CPU monitor lists as the culprit using up a lot of the CPU. When I find the culprit and look up how to diconect it, it seems like another culprit application is then installed during the update.

And besides it seems like Internet browsing is always slow because of the video modules on a web page - is there a way to make sure video does not automatically start when I go to a page? It would seem to me that web designers would not put video on pages if it were to hang-up the MicroSoft browser CPU like it does with Ubuntu.

Is the solution gained by contributing better to Connacal???

---

### Post by snowpine on 2013-02-15
The first half of your question is much too vague---I'd need to know (at minimum) what kind of CPU you have and what the offending apps are, before I'd even venture to answer.

The second half is easy---you can use Firefox add ons such as Flash Block: [https://addons.mozilla.org/en-US/firefox/addon/flashblock/](https://addons.mozilla.org/en-US/firefox/addon/flashblock/)

---

### Post by sidewalkcynic on 2013-02-15
Thanks for the firefox solution

my CPU is Intel® Atom™ CPU N270 @ 1.60GHz × 2 

probably too old - right?

---

### Post by Bufeu on 2013-02-15
> **sidewalkcynic said:**
> Thanks for the firefox solution

my CPU is Intel® Atom™ CPU N270 @ 1.60GHz × 2 

probably too old - right?
Yea. Upgrade your hardware... or buy a new machine.

---

### Post by sidewalkcynic on 2013-02-15
The latest problem is called a Plugin-Container; and I bet that it has something to do with the updates that were downloaded this morning.

---

### Post by snowpine on 2013-02-15
Atom 270 is pretty weak (it's designed more for power savings than performance). I personally would not run Ubuntu with Unity desktop on an Atom machine, for better performance you can try a [lightweight desktop such as Xfce or LXDE]("http://www.psychocats.net/ubuntu/xfce").

---

### Post by Bufeu on 2013-02-15
> **sidewalkcynic said:**
> The latest problem is called a Plugin-Container; and I bet that it has something to do with the updates that were downloaded this morning.
From [http://support.mozilla.org/en-US/kb/What%20is%20plugin-container#os=linux&browser=fx18]("http://support.mozilla.org/en-US/kb/What%20is%20plugin-container#os=linux&browser=fx18"):
"**What is *plugincontainer*?**
Each plugin are loaded separately from Firefox in a *plugin-container* process, allowing the main Firefox process  to stay open if a plugin crashes. There are as many *plugin-container* processes as plugins launched since the Firefox session startup."

---

### Post by philinux on 2013-02-15
> **sidewalkcynic said:**
> Thanks for the firefox solution

my CPU is Intel® Atom™ CPU N270 @ 1.60GHz × 2 

probably too old - right?

I would suggest you install gnome-panel. Reboot and choose classic gnome session.

---

### Post by philinux on 2013-02-15
> **sidewalkcynic said:**
> Thanks for the firefox solution

my CPU is Intel® Atom™ CPU N270 @ 1.60GHz × 2 

probably too old - right?

I would suggest you install gnome-panel. Reboot and choose classic gnome session.  Without effects.

---

