---
title: "Windows in Qemu"
date: 2006-10-07
forum: General Help
---

### Post by alecjw on 2006-10-07
I've just installed Qemu which I want to run Windoze on. I have a windoze installation on /dev/hda1 if it helps.
How do I do this?

---

### Post by SendDerek on 2006-10-19
There are a few really cool tutorials on getting Windows to work under Ubuntu with QEMU + KQEMU.

Here:
[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

And Here:
[http://www.ubuntuforums.org/showthread.php?t=39513&highlight=qemu+windows+vmware](http://www.ubuntuforums.org/showthread.php?t=39513&highlight=qemu+windows+vmware)

All of the information you should need to get it setup should be in there.  If I can do it, you can do it.

However, I would just like to make one thing clear, you're not going to be able to boot your existing windows partition using qemu.  Maybe if you make a full image out of hda1... so, windowsxp.img.  I can't confirm or deny that though.

---

### Post by aktiwers on 2006-10-19
Why not use Vmware? I found it to be *much *faster than Qemu.

---

### Post by SendDerek on 2006-10-19
Doesn't Vmware cost money?

Qemu gets the job done free, but I agree... my experience thus far is that it does have a tendancy to crawl a little bit.

Edit:  Oh... I guess Vmware is free!

It says so right at the top of the product page! [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)
"Experience Server Virtualization -- Free!"

---

### Post by aktiwers on 2006-10-19
Yes Vmware is free now! :)

---

### Post by alecjw on 2006-10-20
VMware is free as in free beer. I like free as in freedom, no matter how slow it is. I got it working using that 2nd Howto you suggested. Windows XP was waaaaaay to slow - it took it 3 hours to get halfway through the *copying essential files*. I didn't have the patience to wait for it to get to the installation. I borrowed a 98SE disk from a friend, made an image of it with dd ad booted from that - it worked perfectley. I can't find any differences between 98SE and XP, so I'm fine with it. Thanks for helping me guys!

---

