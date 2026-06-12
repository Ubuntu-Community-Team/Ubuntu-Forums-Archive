---
title: "File manager(s) stop responding for long periods of time"
date: 2017-11-11
forum: General Help
---

### Post by Andre_R._Gagne on 2017-11-11
Hi all
   The problem I am about to describe has long been a bane of mine when it comes to using Ubuntu and it's variants and trying to browse mounted network shares (mounted as cifs in the fstab file).

   The issue goes like this: When I reboot the system, I have fstab mount several 1 and 2 TB hard drive "shares" from various other servers on my local LAN. The mounting process proceeds as expected, and once I'm logged in and looking at my desktop, the shares are shown as separate icons. so far, so good...

   When I first double-click on one of these share icons, the first folder view normally then opens almost immediately, and, baring a bit of time for the system to read a listing of the share's directory contents, a full view of the share's content soon appears within the file manager's (Thunar, etc.) window. Again, nothing "out of the ordinary" here.

   However, at some point (usually not too long after first accessing the share) the file manager(s) window will become unresponsive ("comatose" is what I have come to call the state that the file manager enters), no longer responding to mouse clicks or keyboard activity of any kind (I can't access the file manager window's menu bar, nor can I select any of the displayed icons by a simple left-click on it). This state will last a *very* long time (10 minutes plus) , until eventually the file manager begins to respond once again.

   This situation does not happen in response to anything I do consistently (that is, I am not noticing this ONLY when I perform a specific task using said file manager(s)...); it seems to happen whenever the file manager is open on a shared resource that has been mounted in the fstab file. Also, the shares are NOT only Windows-based drives...; I have other Linux-based systems whose drives I am sharing this way as well, and the problem is consistent for all of my shared drives! 

   The interesting this is that, when I mount these shared drives using a right-click on the desktop to select "Create URL Link" (I am using XFCE4 as my DE, by the way) then the file manager window that "opens" on that share will NOT experience this problem, EVER! Thus, if I try to mount my shared drives "automatically" at startup (ie. the fstab way), I will experience unacceptable slowdown(s) due to poor file manager responsiveness, but if I only mount these shared resources "on the fly"  then the slowdown with the file manager(s) does not occur!

   What am I missing here? When I use fstab mounting of these shares, those mounted drives act like local HD's, which is ideally what I want! And when it works properly, I LOVE having these drives mounted on one machine all the time! But this seems to perform poorly in practice, and I am very disappointed.

   So I'm just wondering - am I doing something wrong? Or is this just "the nature of the beast" (ie. you can't mount all of these network drives and NOT expect the system to "bog down" because of it)? 

   I experience absolutely ZERO PROBLEMS when I access files off of these shared drives (which vary from large video files to music, etc.), so I can't imagine that the network "in general" simply can't keep up with the demand. And it doesn't seem to matter whether or not I have mounted one share or three shares in the fstab file; the problem is still the same. Eventually, the file manager I'm using will simply become "comatose" and stop responding for a very long time whenever I'm accessing one of these shares. And, strangely enough, while the one file manager window is not responding to mouse clicks, etc., NONE of the other open file manager windows (if others happen to be open at the time) will respond either! They all appear to be in the same "boat" so-to-speak.

   Can anyone out there shed some light on what's going on here? Am I just "nuts" trying to have these drives mounted all of the time?

Do I just have to live with mounting each shared drive I need "by hand" after bootup? Is there a better way to accomplish what I'm trying to do?

   Thanks in advance for any and all suggestions...

---

