---
title: "Something is very wrong..."
date: 2007-09-03
forum: General Help
---

### Post by bean77 on 2007-09-03
Yesterday my computer worked fine.  Today my keyboard stopped working.  After changing out about 4 pairs of batteries (all brand new) and testing it with my DH's laptop, I know it's not a keyboard problem.  I plugged it back in and it worked fine.  Go figure.

Then while opening up Thunderbird, my system froze up the "checking host" or whatever it does when you first open u p your email.  No keyboard, no mouse, no movement. 

Restart again and my monitor no longer works.  PLEASE HELP!

---

### Post by laidback on 2007-09-03
You wouldn't be running via a KVM switch would you? If so try without it.

---

### Post by bean77 on 2007-09-03
> **laidback said:**
> You wouldn't be running via a KVM switch would you? If so try without it.

Nope.  I have a Labtec wireless mouse and keyboard and a Westinghouse monitor.  Why would it stop working all of a sudden?  So strange!

---

### Post by bean77 on 2007-09-03
I thought it could have been a motherboard issue since I've already had to have it sent back to the manufacturer for repair but it was a different issue altogether.  However, if it WAS the motherboard, wouldn't my monitor still work since it is plugged into a video card?

---

### Post by laidback on 2007-09-03
I tend to agree. I had hoped for the KVM so that you could avoid any mobo possibities.
Must agree with video card conclusion. Question is what is common to them all?

Does the system boot as far as you can hear?
Have you a regular keyboard and mouse as well? I'd be tempted to replace the wireless ones just for now.
If you have a Live CD of Ubuntu try to run that with regular mouse and keyboard. It's going to be a process of elimination I reckon. Get back to basics and rebuild ( function not PC or system ) step by step through all possibilities.
I feel for you as I too have built my own PC and had a problem with the screen which I cured by replacing the onboard video card. Real nuisance before I got it sorted and rebuilt my confidence.

Keep at it.

---

### Post by laidback on 2007-09-03
After a little thought this is what I'd do.
Switch to regular keyboard if possible. (and mouse)
Switch to onboard graphics if available (take out video card)
Try to access BIOS at bootup.
If you cannot see that then you have got a mobo problem since either (or both) keyboard and video are down.
Continue on, checking at every stage, try the Live Ubuntu CD (or any other distro), if that works then I'd conclude it's the install that's wrong.

---

### Post by bean77 on 2007-09-03
> **laidback said:**
> I tend to agree. I had hoped for the KVM so that you could avoid any mobo possibities.
Must agree with video card conclusion. Question is what is common to them all?

Does the system boot as far as you can hear?
Have you a regular keyboard and mouse as well? I'd be tempted to replace the wireless ones just for now.
If you have a Live CD of Ubuntu try to run that with regular mouse and keyboard. It's going to be a process of elimination I reckon. Get back to basics and rebuild ( function not PC or system ) step by step through all possibilities.
I feel for you as I too have built my own PC and had a problem with the screen which I cured by replacing the onboard video card. Real nuisance before I got it sorted and rebuilt my confidence.

Keep at it.

So frustrating!  I have never been able to get my monitor to work while plugged into the onboard video so it's nothing new that it doesn't work today.  It's like my monitor isn't even plugged in.  Could something have been knocked loose within my conputer?  

Unfortunately I don't have a regular keyboard but I do have a regular mouse.  What should I do about the monitor?  I tried to boot from the Ubuntu CD but it doesn't help if I can't see anything.

I'm so mad at myself for not buying a computer off the shelf.

---

### Post by bean77 on 2007-09-03
> **laidback said:**
> After a little thought this is what I'd do.
Switch to regular keyboard if possible. (and mouse)
Switch to onboard graphics if available (take out video card)
Try to access BIOS at bootup.
If you cannot see that then you have got a mobo problem since either (or both) keyboard and video are down.
Continue on, checking at every stage, try the Live Ubuntu CD (or any other distro), if that works then I'd conclude it's the install that's wrong.


I didn't realize I had to remove the video card to get the onboard to work.  DUH!  I'll try that right now.

Could it really be possible that the install is wrong-it's been working fine for quite a while now?

---

### Post by bean77 on 2007-09-03
OK, removed the video card and plugged into the onboard video.  System boots up and keyboard works fine.  I can get into BIOS.  Don't know what to do there however!

Tried to get to Gnome and the computer tells me there is no Xserver or something.

GAH!

---

### Post by bean77 on 2007-09-03
tried this:

```
sudo dpkg-reonfigure xserver-xorg
```

I think I'm doing something wrong though.  With my video card installed it would be nVidia but with the onboard it would be VIA, I believe.  Still not working.  After "startx" I get "fatal IO error 104"

Please help before I go back to Windows!

---

### Post by bean77 on 2007-09-03
I'm back on my computer.  I think the only way I got back was by going through the xserver reconfigure.  However, I selected "nv" instead of "nvidia".  I don't have as many choices in screen resolution and I am guessing I should go back and change it but I am scared it won't work again and my DH will kill me for being on the damn computer for this long!

---

### Post by laidback on 2007-09-04
OK so you have made progress. All is not lost by any means. Your mobo seems OK.
It would appear that your video now works (onboard) and that you have a mouse and keyboard.
I'm no expert with the command line so tend to go back to something I can understand, which in this case is the Ubuntu Live CD and a fresh install. I'd be tempted to reinstall your video card and get into the BIOS again. I suspect that it automatically detects the card but you can view it's choice on one of the screens. When I put my card in I disabled the onboard card within the bios, it might be belt and braces but I'm happier if I know that it's definitely turned off. In your case I'd install the card, switch on and see if I can enter bios. Now Exit bios without saving and repeat the exercise. This time switch off the onboard video, save bios settings on exit. Seems long winded but I like to see that I can repeat an exercise before I commit it.
Put Live Ubuntu CD drive and boot from that. Does it work, can you switch screen resolutions from the desktop (System>preferences>screen resolutions), don't be surprised if the list with live CD is not quite what you expect. I use 1280x1024 but it wasn't available via Live CD but was once I installed. Play around and get confidence. I suggest you don't use your wireless keyboard and mouse, yet.

If all goes well reinstall. Now you may have some data that you wish to keep. If so you'll need to get at it from the live CD stage and copy if off onto something, memory stick! I cannot remember whether your hdd will be mounted by default from the Live CD, if so all is easy if not you'll need to mount it. Look in Computer (Places>Computer)
I keep a quick note on a pad beside the pc so that I record what I did at each stage, nothing too detailed, but it helps when something goes wrong.

Gradually rebuild your system. When it comes to the mouse and keyboard I'd do one at a time, and leave a day or two between the switch overs.

You will not regret having built your own pc, I know it seems a bad decision right now but further down the line you'll be really glad you know and understand your own system. 

Ubuntu is really great, well worth the effort. Keep at it you will win through.

---

### Post by laidback on 2007-09-04
Unfortunately I'm going to be away for a few days now, I'll try to find time to view this thread once more before I leave. I shall be very disappointed if you give up.

Kindest Regards

---

### Post by bean77 on 2007-09-04
OK, everything works-I just need to figure out the nvidia thing.  Thank you for all of your help!

---

### Post by laidback on 2007-09-04
I'm just packing up to go and am having a quick look at the forum before I depart. So pleased to read your latest post, I can go away with a warm feeling that you have made significant progress and will continue with Ubuntu. I'm very pleased.

Perhaps you would be kind enough to post at the weekend to let me know how you have faired over the next few days.

Kindest Regards
Laidback

---

### Post by bean77 on 2007-09-05
It's not going well...read [here]("http://ubuntuforums.org/showthread.php?t=543970")

---

