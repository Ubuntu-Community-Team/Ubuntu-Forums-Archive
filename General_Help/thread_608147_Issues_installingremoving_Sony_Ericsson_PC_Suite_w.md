---
title: "Issues installing/removing Sony Ericsson PC Suite with Wine"
date: 2007-11-09
forum: General Help
---

### Post by rainwalker on 2007-11-09
I installed Wine 0.9.46 through Synaptic on Gutsy so that I could use Sony Ericsson's PC Suite software with my new W580i, but I can't seem to get the program to work.
First, it said it couldn't find a .dll, so I copied it from a Windows comp over to the Wine directory and tried again.
Now when I run the .exe it doesn't ask any setup questions that it did before I copied the .dll over, and even when the progress bar reaches full, it starts going backwards. Once it's gone, it just reappears full and then empties again.
I tried uninstalling everything in Wine, but "Sony Ericsson Device Data" and "Sony Ericsson Drivers" are always there (even after a complete romoval.

Has anyone been able to get this software to work? 
If not, can anyone recommend a course of action? I'm thinking about uninstalling and reinstalling Wine and trying it all over again.

---

### Post by scorp123 on 2007-11-09
> **rainwalker said:**
> I installed Wine 0.9.46 through Synaptic on Gutsy so that I could use Sony Ericsson's PC Suite software with my new W580i.  Why do you need that software? Most mobile phones can be used directly on Linux, e.g. it's possible to upload and download music and pictures via Bluetooth or USB cable, and usually it's also possible to use these phones as modem if you need or want to (I sometimes use my Sharp 770SH in such a way).

Besides -- AFAIK: WINE only offers a sort of API-Layer so that simple Windows applications and a few games can run. It does not offer any form of virtualisation of hardware and it also has no knowledge about your hardware. Installing device drivers under WINE is therefore pointless because due to WINE's limitations it will most likely never work. Don't get me wrong .... WINE is absolutely useful for some things .... but not for this. So if you really insist on using the SonyEricsson software you would have to use a fully virtualised Windows installtion running inside e.g. VMware or VirtualBox.

---

### Post by rainwalker on 2007-11-09
Ah...that's what I thought.

My phone does connect, but since I don't have a memory stick for it the phone just mounts as a blank drive.
I was hoping this software would give me access to the phone's built-in memory, but I tried it on our actual Windows computer anyway and it doesn't.

Thank you :)

---

### Post by scorp123 on 2007-11-10
> **rainwalker said:**
>  I was hoping this software would give me access to the phone's built-in memory  For my Sharp 770SH I use "obexftp" for this ... I haven't yet found a nice looking GUI tool for this, so right now this command line tool is the only way for me to do this, but it's OK .... It gets the job done and that's all that counts. The only Sony Ericsson I have here is an old T610i so I don't know how comparable that one is to your phone, but I assume that once you connect your phone to your computer (either via USB cable or Bluetooth) it should be possible to talk to it via the "OBEX" protocol (search for "obex" in Synaptic ... there are various frontends and tools; some are even user-friendly :) ) and access the phone's memory.

---

### Post by rainwalker on 2007-11-10
Thanks, I'll check it out  :)

---

