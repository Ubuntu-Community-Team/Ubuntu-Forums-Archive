---
title: "Where can I get hplip-plugin for ARM architecture?"
date: 2015-05-28
forum: General Help
---

### Post by xiyu on 2015-05-28
According to the website [http://hplipopensource.com/hplip-web/release_notes.html](http://hplipopensource.com/hplip-web/release_notes.html),
**HPLIP 3.15.4 - This release has the following changes:**
Significant Changes:
```
- HPLIP Plugin support for ARMv6,ARMv7 and aarch64 architectures
```
Here comes the problem, where can I get the Plugin for ARM?
Thanks.

---

### Post by Bucky Ball on 2015-05-29
What device and OS are you using?

---

### Post by xiyu on 2015-05-29
I'm using ubuntu14.04 LTS, i386 machine.

---

### Post by Bucky Ball on 2015-05-29
It is not already in the Software centre? You're wanting HP-Lip for ARM but you're using an i386 computer? What is the device you are wanting this for and what OS will you be running on that, thanks, NOT the machine you're currently typing your posts on (unless it is the ARM device that you're wanting help with, which it's not by the sounds of it). :-k

---

### Post by xiyu on 2015-05-29
Sorry for confusing you. It's my fault, I didn't make it clear enough. 
1. [COLOR=#000000]It is not already in the Software centre?
[/COLOR] Yep. [http://hplipopensource.com]("http://hplipopensource.com/") only gives me the source code of HPLIP-3.15.4. According to that website, the hplip-plugin is not open source. So I guess there might be a binary hplip-plugin somewhere which has already been compiled for supporting ARM. But where is it? Or may my understanding be incorrect?

2. [COLOR=#000000]You're wanting HP-Lip for ARM but you're using an i386 computer?
[/COLOR] My reply confused you, sorry for that. Actually, I want to use hplip on ARM by CROSS-COMPILING. AFAIK, some printer requires hplip-plugin for printing support or scaning support. My target machine is ARM while the build machine is a PC based on i386 architecture.

3. [COLOR=#000000]What is the device you are wanting this for and what OS will you be running on that?
[/COLOR] Target Device: ARM
 OS on Target Device: Linux, kernel version: 2.6.35.7

Again, I'm really sorry for my bad English and vague statements.
Best regards.

---

### Post by Bucky Ball on 2015-05-29
All good. Again, though, not very specific. Linux and the kernel version? That kernel is old. 14.04 is currently on 3.13 (are you talking about 12.04???) so I can only imagine you are intending to install an old version of Ubuntu or another distro altogether.

You again give no details of what the target device is apart from 'arm'. That is not a device, that is the processor it is using. So, no idea of the device (only that it has an 'ARM' processor) and no idea of the distro you are intending to use (only that it runs the 2.6.35-7 kernel). Be specific, please.

All I can really say on the information you have provided is that if you are using a distro that uses Synpatic Package Manager (or possibly others) HPLip will be in the repositories. It is on my Odroid running a spin of Lubuntu 14.04. Why not get the device, install whatever it is you're going to install and look in the package manager before making plans to compile manually. If you are compiling manually because the kernel you're intending to use is so old it is no longer supported through the regular channels, I suggest you use a recent and supported kernel instead.

Please clearly state which flavour of Ubuntu you are intending to install and what the device is you are going to install it on (make/model, not processor architecture). If you're not intending to use Ubuntu then I will move this thread to the appropriate forum area. Thanks.

Good luck. ;)

---

### Post by xiyu on 2015-05-29
I appreciate very much for your help. Whereas, I'm very eager to let you know what situation I'm dealing with. For the last time , please let me depict it more specific for the last chance. May this will not make you disappointed...
Some situations are not extremely important so it is not necessary to concern about.
I got a ARM development board which runs Linux system with kernel version 2.6.35.7. In order to make my printer work on it, it is clearly unavoidable to use cross-compiling chain tools to compile the tarball hplip-3.15.2(the version I used earlier). I've tested some HP DeskJet Printers and they showed good performance. Even though the kernel might be old, it seems that hplip works well on it. I've also tested a laser printer named HP LaserJet 1005, failed. Eventually I found that  some HP LaserJet Printers require hplip-plugin which is a binary program and closed-source to support printing. Fortunately, the latest version hplip-3.15.4 released with notes:
[COLOR=#000000][FONT=Arial]**Significant Changes:**
```
- HPLIP Plugin support for ARMv6,ARMv7 and aarch64 architecturess
```
From now, I'm confused. Since this hplip-plugin for ARM is not opensource, and also not shipped with the tarball of hplip-3.15.4. Is there any possibility that this plugin exists as also a binary program in somewhere else? Frustrating.
You have did a lot of favor to me. Thanks very much, my friend.[/FONT][/COLOR];)

---

### Post by sotiris2 on 2015-05-29
Did you check [this](http://hplipopensource.com/node/309)? Do you have a hp-setup in your target machine after you install hplip?

---

### Post by xiyu on 2015-05-29
Yes, I did. But that refers to the situation where hplip installed on PC rather than embedded system based on ARM. I do have a hp-setup and hp-plugin shell script in my target machine. The key problem is that the development ARM board doesn't have a screen so that GUI won't work here. Hmm, It seems difficult.
But you did give me a thought. Did you mean all I need to do is to connect my ARM board to the Internet then issue _hp-setup_ to the terminal of ARM board which will  install the hplip-plugin for ARM architecture automatically? Is that possible to install the hplip-plugin through command-line rather than GUI?
Lot's of questions, sorry for that 'cause I'm a newbie. ;)

---

### Post by sotiris2 on 2015-05-29
As hp-setup's man page says -i option will run the setup in interactive (cli) mode. You can test it in your pc (as i did) that ```
hp-setup -i
``` needs no GUI. It does need you to be able to see responses to the console. 

I can't guarantee you that it will work but I do not see any other option. I don't see the actual plugin available to download anywhere. man hp-setup says it tries to auto-determine the correct ppd file to use. So if there is an arm plugin for your printer (I do get the feeling that there is not ONE plugin for all printers) it should probably download it.

---

