---
title: "VMWare and TwinView"
date: 2007-04-19
forum: General Help
---

### Post by nami on 2007-04-19
Hi,

I have TwinView working on my setup and have installed VMWare.  When I start VMWare in full screen mode, it only fills the first screen on the host desktop and the second screen goes blank.  How do I get it to use both screens so when a window is opened within a guess OS it fills the single monitor when maximized depending on which monitor that window is on.

However VMWare Server should fill both screens when in fullscreen mode.

Can this be done?

---

### Post by zythum on 2007-04-19
When you load VMWARE, even in full scree, the windows will fill only the area of the Window's display. Ex Your ubuntu got a resolution of 2560*1024, your vmware windows got 640x480, event if you do a full screen, you will only have 640*480. The rest will be black

---

### Post by nami on 2007-04-19
ic

so how would i get vmware to load guest operating systems at 2560x1024 so vmware uses both the monitors?

---

### Post by beerorkid on 2007-04-19
from [here]("http://www.vmware.com/community/thread.jspa?messageID=509899&#509899")
> Server does not have a high performance virtual video card. Server was designed for non-interactive server OS'. So you're porobably not going to get much beyond standard 4:3 ratios.

but, don't let that get you down.  there is always a way to tweak it ;)

from [here]("http://www.vmware.com/community/thread.jspa?threadID=61838&tstart=30")
> With the VM powered off, try adding the following lines to the .vmx file for the virtual machine

svga.maxWidth = "1280"
svga.maxHeight = "800" 
of course you would want to change that to the resolution you are looking for.

if that does not work you can hack the windows registry via this [KB article.]("http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=1003")

Let us know if it works, or which way was better.

---

### Post by nami on 2007-04-19
Thanks for the info!

I'll try that asap and will let you know how I get on. :KS

---

### Post by nami on 2007-04-19
Excellent!

The following worked:

svga.maxWidth = "2560"
svga.maxHeight = "1024"

However, when I maximize a window, for example a browser within the guest operating system, it maximizes across both monitors, when it should only maximize on the monitor the program is currently on, similar to how the windows behave in twinview for ubuntu.

Can that be done?

---

### Post by beerorkid on 2007-04-19
cool glad that worked.  Thanks for replying.

I doubt that it would work the way you want inside the VM.  It has no clue it has two monitors, it thinks it is one uber awesome wide screen.  Just my thoughts on it though.

Would be cool if you could make a VM think it had two screens though.  For my earlier post I just searched the VMware forums for dual screen and did not find much on it cept for the ones I posted.

---

### Post by nami on 2007-04-19
I thought I might be pushing it a bit :lolflag: 

No worries, thanks for all the help, very much appreciated.

---

