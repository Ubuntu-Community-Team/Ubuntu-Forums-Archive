---
title: "Flash crashes!!"
date: 2007-06-02
forum: General Help
---

### Post by NiGHTS7041 on 2007-06-02
Ok, so for some reason I am unable to use youtube or any other thing on the internet that involves flash. Before I am even able to load a video, it just crashes my browser. I use both Firefox and Opera and both of them are unable to view flash. If I restart my computer about 4 times, sometimes I am able to watch flash applications. 

I use Feisty. Anybody know what the problem could be?

---

### Post by NiGHTS7041 on 2007-06-02
bump

---

### Post by natman on 2007-06-03
Hey,
I have the eact same problem, firefox just quits once any bit of flash pops up. I found a help out, about increasing the color depth to 24, this worked for a few sessions butim back to square one now. I have a tread opened up also if anyone wants to reply to help.
If you find a solution please tell me thanks

---

### Post by Silenus on 2007-06-03
Do you have the latest version of flash installed? I have noticed myspace will lock up and crash on firefox if you are uploading photos, I found that Opera, is the best work around, as I have not found a better way to fix it yet.

---

### Post by NiGHTS7041 on 2007-06-03
I do have the latest version of flash installed and even when I use Opera, it crashes as well.

---

### Post by steveneddy on 2007-06-05
Maybe an answer here:

I first made sure that I using the **flashplugin-nonfree** that is available in Synaptic and then followed advice from [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox") that addressed t**he sound issue in Firefox causing the crash and not actually Flash**.

It tell you how to **install alsa-oss** and how to get Firefox to use it correctly.

I had sound already but did it anyway. This along with another hint did it for me.

The third hint is from [this post]("http://ubuntuforums.org/showthread.php?t=428979&highlight=firefox+crash+flash&page=4") that deals with adding a line to the /usr/bin/firefox file.

Here is a copy of that post:

[HTML]1. Open the firefox file...

    Ubuntu users: sudo gedit /usr/bin/firefox

    Kubuntu users: sudo kate /usr/bin/firefox

2. Add the following line as last but one line of the file:

    export XLIB_SKIP_ARGB_VISUALS=1

3. Restart Mozilla Firefox [/HTML]

Adding the line in the firefox bin file and changing the Firefox default sound app to alsa-oss helped me.

I was crashing ALL THE TIME - usually after 3-4 videos. I just did that and went to YouTube and watched almost 30 minutes of video with no crash. I started them in the middle, closed the tab while playing and started a new video in the moddle of one that was already playing. I opened three tabs and played video in all three tabs with no crash.

I did also open firefox in terminal to see what the error code was when it crashed, but like I said, no crashes.

1. Use the correct driver
2. Download alsa-oss and tell Firefox to use it.
3.Add the line in /usr/bin/firefox


Hope this helps.

-SE

---

### Post by NiGHTS7041 on 2007-06-05
Wow, that seems like it would solve my problems but now I have another one! I type in the gedit command and when the new window opens up it displays nothing. It doesn't respond and after ten minutes I have to force quit it. I have reset my computer 3 times and nothing, it still doesn't work. What could be the problem?

---

### Post by steveneddy on 2007-06-05
I am ham back to having troubles with this setup myself - again.

there doesn't seem to any clear fix besides buggy software from Adobe.

I have been on this for almost nine hours looking and trying every option. I tried each option individually and in many different combinations and still no permanent success.

Still searching though.

---

### Post by RippedWallet.com on 2007-06-05
i had this same problem once.....but my friend fixed it =P

---

### Post by devicerandom on 2007-06-14
Tried. Does not work for me. Also other suggestions (depth=24 bit, Composite off) do not work

I'm using Kubuntu Feisty (x86) with Firefox. Flash videos and other heavy Flash content freezes my browser. Video card is an ATI X300SE, managed by the OSS ati drivers.

Any new hint about finding the root of this problem?

---

### Post by flankker on 2007-06-15
hey everyone, they just released an updated version of flash (in beta form) and i can tell u it has solved the problem for me. keep in mind that there will be bugs as it is a beta at this stage.

anyway, get it from here: [http://blogs.adobe.com/penguin.swf/2007/06/fullscreen_beta.html](http://blogs.adobe.com/penguin.swf/2007/06/fullscreen_beta.html)

---

### Post by daverich on 2007-06-27
I've seen on the net that this is a bug with the plugin and dual core systems.

I'm wondering is it possible to force firefox/flash onto one cpu?

Kind regards

Dave Rich

---

