---
title: "Beagle/BEST help"
date: 2005-06-26
forum: General Help
---

### Post by stray on 2005-06-26
OK. I've followed the [Installing Beagle](http://www.beaglewiki.org/Ubuntu_Installation) instructions, I've started *beagled* from the command line, but I can't find a simple text file in my home directory.

When I run a test search for "adblock" (I'm trying to find a file called *adblock.txt*), I get this error:
> The query for adblock failed with error:
System.Net.Sockets.SocketException: System call failed in [0x00063] System.Net.Sockets.Socket:Connect (System.Net.EndPoint remote_end) in <0x00021> Beagle.Util.UnixClient:Connect (Mono.Posix.UnixEndPoint remoteEndPoint) in <0x00036> Beagle.Util.UnixClient:Connect (System.String path) in <0x00020> Beagle.Util.UnixClient:.ctor (System.String path) in <0x00028> Beagle.Client:SendRequest (Beagle.RequestMessage request) in <0x00010> Beagle.Client:SendAsync (Beagle.RequestMessage request) in <0x000c7> Beagle.RequestMessage:SendAsync () in <0x00142> Best.BestWindow:Search (System.String searchString)

Does anyone know what this might be?

Also, I installed the Beagle Extension for Firefox; do I need to re-compile it from source? If so, how? I've never compiled from cvs before and I'm kind of nervous about it.

---

### Post by burlap on 2005-06-27
It takes time to index files. 
What do ```
beagle-index-info
``` and ```
beagle-status
``` show? 


You can also run beagled in a terminal ```
beagled --fg --debug
``` and take a lookt at first lines of the output when beagle is starting backends (are there any warnings or errors?)

I don't think you need to recompile beagle after installing firefox extension.

---

### Post by arunsub on 2005-06-27
I tried Beagle and I had lots of problem installing it. I then switched to Collective Cortex. It's pretty easy to install and index files. It works pretty fast.
[http://www.collectivecortex.com/](http://www.collectivecortex.com/) -- If you want to give it a try. One thing to remember, It's still in Beta, but pretty stable for Beta.

---

### Post by burlap on 2005-06-27
I run beagle and except for some major issues (see for example [this](http://ubuntuforums.org/showthread.php?t=44434) and [this](http://ubuntuforums.org/showthread.php?t=44008) ) it is ok for me. ;)

[quote=arunsub]I then switched to Collective Cortex. [/quote]This looks like proprietary, closed source software. And one day maybe you'll have to pay for it also. 
Well, I have nothing against proprietary as such (I admit: I use adobe reader, xpdf rendering on my LCD screen doesn't work well), but I'd prefer to help developing Beagle and other useful open source tools... (My only help is filing bugs, but you know the quote...)

---

### Post by stray on 2005-06-27
from beagle-index-info:
> ** (/usr/lib/beagle/Info.exe:24628): WARNING **: _wapi_connect: Need to translate 2 [No such file or directory] into winsock error
Could not connect to the daemon.
robert@tomservo:~$ beagled
Beagle Daemon exited with errors.  See ~/.beagle/Log/current-Beagle for more details.
from ~/.beagle/Log/current-Beagle:
> 05-06-27 13.34.38.64 24641 Beagle INFO: Starting Beagle Daemon (version 0.0.11.1)
05-06-27 13.34.38.67 24641 Beagle DEBUG: Command Line: /usr/lib/beagle/BeagleDaemon.exe --bg
05-06-27 13.34.38.71 24641 Beagle FATAL: Could not set extended attributes on a file in your home directory.  See [http://www.beaglewiki.org/Enabling_Extended_Attributes](http://www.beaglewiki.org/Enabling_Extended_Attributes) for more information.

from that wiki web page:
> For Reiser3 and ext2 filesystems, the default kernel config does not enable the attributes. For ext2 filesystems, the kernel option for attributes is CONFIG_EXT2_FS_XATTR. For ext3, it's CONFIG_EXT3_FS_XATTR.

Ok, so I guess I have to reconfig my kernel. I've never done this and I'm VERY nervous about doing so. is there a really good HOWTO on this? Also, if I do reconfigure my kernel, will I have to do this extra reconfiguration every time the update applet tells me there's a new kernel out?

---

### Post by burlap on 2005-06-27
CHECK THIS BEFORE YOU RECONFIGURE YOUR KERNEL! 

Look for relevant entry (like CONFIG_EXT3_FS_XATTR) in /boot/config-2.6.10-xxxx. If it says yes, it is ok. Just follow the instructions to remount your home dir. 

(I use 2.6.10-5-686 from ubuntu repositories and it has xattr enabled, so you may consider running this one (or other appropriate for your CPU). So I presume that default may be also ok). 

If you want to reconfigure kernel anyway: good luck and a lot o patience.  :grin:

---

### Post by stray on 2005-06-27
DOH! I had tried to add the user_xattr thing-o to my fstab file as me. I added it as root and whammo, Beagle seems to be indexing. Will add to this post if more problems arise, or if things go poorly.

---

### Post by niels2005 on 2005-07-02
hi,
I installed Beagle and run beagled --fg --debug,
I did not get any error messages but somehow beagle seems to be stuck at this point:
DEBUG: Starting task Crawling ~/.evolution to find summary changes
DEBUG: Finished task Crawling ~/.evolution to find summary changes in ,01s
DEBUG: Starting task Crawling ~/.evolution to find summary changes
DEBUG: Finished task Crawling ~/.evolution to find summary changes in ,01s
DEBUG: Helper Size: VmRSS=22,5 MB, size=2,32, 33,0%
DEBUG: Helper Size: VmRSS=22,5 MB, size=2,32, 33,1%
DEBUG: Helper Size: VmRSS=22,5 MB, size=2,32, 33,1%
DEBUG: Starting task Crawling ~/.evolution to find summary changes
DEBUG: Finished task Crawling ~/.evolution to find summary changes in ,01s

how can I solve this problem ?
beagle-index-info
revealed that zero files have been indexed
please
niels

---

