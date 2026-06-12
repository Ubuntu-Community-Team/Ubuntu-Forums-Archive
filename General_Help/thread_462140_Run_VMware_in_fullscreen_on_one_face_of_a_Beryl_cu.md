---
title: "Run VMware in fullscreen on one face of a Beryl cube"
date: 2007-06-02
forum: General Help
---

### Post by srunni on 2007-06-02
Hi,

Is there any way to run VMware Server in fullscreen mode on one face of a Beryl cube? I can get the virtual machine to go full screen, but I can't switch desktops while in this mode. Does anyone know how I can make it so that Ctrl+Alt+[mouse click] will not get translated to the virtual machine, but instead get picked up by Beryl?

Thanks in advance for the help!

---

### Post by Rhubarb on 2007-06-02
While I can't confirm this now, you should just be able to press Ctrl + Alt (to release your mouse cursor from your vmware session), then press Ctrl + Alt + mouse drag to move the Beryl cube around.

---

### Post by srunni on 2007-06-03
> **Rhubarb said:**
> While I can't confirm this now, you should just be able to press Ctrl + Alt (to release your mouse cursor from your vmware session), then press Ctrl + Alt + mouse drag to move the Beryl cube around.

The problem with that idea is that Ctrl+Alt will cause VMware to exit fullscreen, while I want it to stay in fullscreen while the cube rotates.

---

### Post by statictonic on 2007-06-03
The closest you can get to doing this with vmware is using the quickswitch mode and having all the toolbars disabled.  It will leave a small gray border around everything unfortunately.

---

### Post by veloce on 2007-06-03
Another idea (if you're stuck):

I don't use vmware's console to run vms full screen, rather, I use gnome-rdp.  That is, I rdp to the vm across the host only network.  

Gnome rdp may work with beryl better than vmware console.

---

### Post by gerscht on 2007-06-03
@veloce

That sounds like a great idea, I'll have to try this

---

### Post by srunni on 2007-06-03
I tried out the quickswitch mode, and it works great. This picture isn't mine, but it looks pretty much like what my setup is: [http://www.daniel15.com/blog/wp-content/uploads/2006/09/vmware-2.jpg](http://www.daniel15.com/blog/wp-content/uploads/2006/09/vmware-2.jpg). The only thing is that if you want to rotate the cube, you have to hold Ctrl+Alt and then click on the gray border - you can't just click anywhere in the VM. I'll have to try the RDP method too, if it's possible that it's faster than the VMware Console login.

---

### Post by midtown on 2007-07-04
> **statictonic said:**
> The closest you can get to doing this with vmware is using the quickswitch mode and having all the toolbars disabled.  It will leave a small gray border around everything unfortunately.

Thanks, that actually works quite well! The tiny border is no biggie at all.

---

