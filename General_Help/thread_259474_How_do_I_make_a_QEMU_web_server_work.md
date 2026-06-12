---
title: "How do I make a QEMU web server work?"
date: 2006-09-17
forum: General Help
---

### Post by scratched on 2006-09-17
Last night I set up a Windows XP Pro image in QEMU. I installed IIS and when I open up IE and type in localhost it takes me to the website placeholder so I know it works (at least inside the VM).

What do I need to do to get the VM to act as a real web server?

I installed VDE but I'm not sure how that works or if that's even what I need. All I know is that there is no man page for VDE.

---

### Post by PriceChild on 2006-09-17
Well if you've got your Xp seeing itself as a webserver... all you have to do is ensure your virtual machine's networking settings to assign a different ip to that of the host.

Then navigate to the ip of the virtual machine in a webbrowser

---

### Post by scratched on 2006-09-17
I figured I needed to do something to that effect.

How do I go about doing that though?

Is there a command line program that can do it? Like I said, I installed the VDE package from apt, but I don't know how to use it, or if that's even what I *should* be using.

---

