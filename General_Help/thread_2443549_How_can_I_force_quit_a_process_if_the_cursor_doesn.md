---
title: "How can I force quit a process if the cursor doesn't work?"
date: 2020-05-17
forum: General Help
---

### Post by anotherChris on 2020-05-17
Recently, Microsoft's O365 "Teams" website and also Microsoft's Live website for Hotmail have been making my computer freeze.  I'm accessing them with Firefox on Lubuntu 20.04.  The cursor will either stop moving, or if it moves, it won't let me click on anything.  So, I can't open the terminal to use "xkill".   Is there anything to do other than hard re-start?

(P.S.  I need to use the MSFT products for work, so please don't suggest stopping using them.)

---

### Post by Holger_Gehrke on 2020-05-17
If your machine has 4 GB or less of RAM, it's probable Firefox is using so much memory that the machine is using swap heavily. If you have swap on a mechanical drive you might actually be able to hear it 'threshing'. If that's it, than it's not frozen, just running **very** slowly with things that normally take a fraction of a second taking minutes. Hit ctrl-alt-F3 to switch to the third virtual terminal (depending on the version and flavour of Ubuntu the first two might be in use; this switch is normally very quick but can take a long time under these circumstances). The screen will change to a white on black text mode display asking for your username. After entering that it will ask for your password; like with using 'sudo' in a terminal you will get no indication that it's reading your input but it does. If you successfully log in, you'll get a shell and can simply enter 'sudo pkill -9 firefox' which should end Firefox. Use Ctrl-Alt-F7 to return to the GUI, after a moment it should return to a usable state.

If that's not the problem, you can at least try to minimize the damage by using the [Magic SysRequest]("https://en.wikipedia.org/wiki/Magic_SysRq_key") key combination (REISUB). This does something a lot more like a controlled shutdown and reduces the risk of breaking file systems and files.

Holger

---

### Post by anotherChris on 2020-05-17
> **Holger_Gehrke said:**
> If your machine has 4 GB or less of RAM, it's probable Firefox is using so much memory that the machine is using swap heavily. 

That's possible.  I have a circa 2009 laptop with Celeron processor.  Not sure how much RAM, but very possibly less than 4GB.  However, I was running 17.10 with Chromium prior to 20.04 and never had issues like this unless I had, like, 8+ tabs of YouTube open.

> **Holger_Gehrke said:**
> If you have swap on a mechanical drive you might actually be able to hear it 'threshing'. 

Hmmm... Does that sound anything like a fan?  I often hear what I think is the fan going into a high speed.

> **Holger_Gehrke said:**
> If that's it, than it's not frozen, just running **very** slowly with things that normally take a fraction of a second taking minutes. 

Could be.  I just had everything freeze when I tried to use Google Maps, and I left it and cleaned up the kitchen.  It was still not working when I came back.  Cursor would jump around the screen a long time after I used the mouse pad, but no clicking made anything respond.

> **Holger_Gehrke said:**
> Hit ctrl-alt-F3 to switch to the third virtual terminal (depending on the version and flavour of Ubuntu the first two might be in use; this switch is normally very quick but can take a long time under these circumstances). The screen will change to a white on black text mode display asking for your username. After entering that it will ask for your password; like with using 'sudo' in a terminal you will get no indication that it's reading your input but it does. If you successfully log in, you'll get a shell and can simply enter 'sudo pkill -9 firefox' which should end Firefox. Use Ctrl-Alt-F7 to return to the GUI, after a moment it should return to a usable state.

Thank you.  For some reason, these commands don't work on my laptop.  But I discovered through experimentation that Ctrl+Fn+Alt+F2 (but not Ctrl+Alt+F2) will take me into that terminal-like black screen text mode, and Ctrl+Fn+Alt+F1 will take me back to the GUI.

> **Holger_Gehrke said:**
> If that's not the problem, you can at least try to minimize the damage by using the [Magic SysRequest]("https://en.wikipedia.org/wiki/Magic_SysRq_key") key combination (REISUB). This does something a lot more like a controlled shutdown and reduces the risk of breaking file systems and files.

That's very good to know.  Just got to write these things down in a notebook now....

Thank you.

---

### Post by CatKiller on 2020-05-17
> **anotherChris said:**
> Could be.  I just had everything freeze when I tried to use Google Maps, and I left it and cleaned up the kitchen.  It was still not working when I came back.  Cursor would jump around the screen a long time after I used the mouse pad, but no clicking made anything respond.

That does sound like an out-of-memory situation to me.

> That's very good to know.  Just got to write these things down in a notebook now....

Some people use the mnemonic that it's BUSIER backwards, and others use Raising Elephants Is So Utterly Boring.

Another tool that's useful is to set up SSH access to your machine; then you can SSH from another computer or a phone to give it a poke when something goes awry.

---

### Post by Holger_Gehrke on 2020-05-17
> **anotherChris said:**
> 
Hmmm... Does that sound anything like a fan?  I often hear what I think is the fan going into a high speed.

No, you should be able to hear lots of rapid movements of the read-write-head; sounds more like rapid clicking (at least on very old HDs). The fan-like noise is probably really the fan.
> **anotherChris said:**
> 
Thank you.  For some reason, these commands don't work on my laptop.  But I discovered through experimentation that Ctrl+Fn+Alt+F2 (but not Ctrl+Alt+F2) will take me into that terminal-like black screen text mode, and Ctrl+Fn+Alt+F1 will take me back to the GUI.
Oh, one of those keyboards. My laptop used to do that too, but on that one there's an option in the BIOS / Firmware Setup to set the keyboard to traditional function keys without using the fn-key and hardware control functions with the fn-key. Also you might get better results with 'sudo pkill **-f** -9 firefox'. Without the '-f' it's killing the one process that has 'firefox' as it's name, but Firefox runs multiple processes (the extensions run in a separate process and all the pages/tabs are split between multiple content processes). Killing the coordinating master process should make all the others terminate too, but this doesn't seem to be happening on your machine. With the '-f' pkill looks for processes by command instead of by name and should get them all ... If that still doesn't work, you can enter 'sudo reboot now' into the virtual console. This is a bit safer than SysReq+REISUB

One thing I did back when I had just 4 GB in my laptop was to limit the number of content-processes in Firefox ('Settings'->'General'->'Performance'->'Number of content processes') to two instead of four (might be set to 8 now, at least that seems to be the default). This will not stop it completely but should make it less frequent. Also the add-ons / extensions you use can have a serious impact on memory use. Switching from 'Adblock plus' to 'uBlock Origin' was one of the things which helped me a lot.

Holger

---

### Post by anotherChris on 2020-05-17
> **Holger_Gehrke said:**
> One thing I did back when I had just 4 GB in my laptop was to limit the number of content-processes in Firefox ('Settings'->'General'->'Performance'->'Number of content processes') to two instead of four (might be set to 8 now, at least that seems to be the default). This will not stop it completely but should make it less frequent. Also the add-ons / extensions you use can have a serious impact on memory use. Switching from 'Adblock plus' to 'uBlock Origin' was one of the things which helped me a lot.

Yes, I have uBlock Origin.  I think it actually improved performance with YouTube, although to be honest YouTube seems to be getting slower.  It was slow after initial install, then uBlock Origin seemed to improve it a bit, but then slower and slower...  Anyway, I've just changed the content processes to 2.  As you said, they were set to 8.  Will see how this affects things.... Thanks.

---

### Post by ActionParsnip on 2020-05-18
Pressing CTRL + ALT + T will start a terminal and you can manipulate processes there

---

### Post by anotherChris on 2020-05-18
> **Holger_Gehrke said:**
> One thing I did back when I had just 4 GB in my laptop was to limit the number of content-processes in Firefox ('Settings'->'General'->'Performance'->'Number of content processes') to two instead of four (might be set to 8 now, at least that seems to be the default). This will not stop it completely but should make it less frequent. Also the add-ons / extensions you use can have a serious impact on memory use. Switching from 'Adblock plus' to 'uBlock Origin' was one of the things which helped me a lot.

Holger

I set it to 2 today, and I didn't have any problems while using Microsoft O365 Teams website.  I got through work without having to re-start.  Maybe it was just a coincidence, but maybe you solved it!  For now, I will keep FireFox with 2 content-processes and see how things go.  Thanks.

---

### Post by anotherChris on 2020-05-18
> **ActionParsnip said:**
> Pressing CTRL + ALT + T will start a terminal and you can manipulate processes there

Now, see, I didn't even know that, but it works on my computer!  Thanks!

---

