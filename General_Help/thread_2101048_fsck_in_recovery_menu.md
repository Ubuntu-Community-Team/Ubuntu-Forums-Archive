---
title: "fsck in recovery menu"
date: 2013-01-03
forum: General Help
---

### Post by wolfgentleman on 2013-01-03
I have a problem with my cursor in non root accounts so I got on the kubuntu IRC and was told to run a disk check, I could not get my live cd to do it so I used the recovery mode fsck it spit one line out and just sat there the rest of the night (10+ hours). In the morning I hit CTRL+C and it brought me to the login. What do I do?

EDIT:

I figured out it was a device lockup, I am able to use numpad to move cursor. I tried a different mouse and it locked up too. Why would my mice be locking up?

---

### Post by slickymaster on 2013-01-03
Try booting into recovery mode - from recovery menu - root prompt and run fsck 
```
fsck /dev/sda1
```

If that doesn't work you could be facing a hard disk failure. If so try the [Ultimate Boot CD]("http://www.ultimatebootcd.com/"), it has the tools from the main HDD manufacturers and you can test the drive at a very low level.

---

### Post by wolfgentleman on 2013-01-03
It said it was clean... however I have yet to figure out what is going on, also I learned that the live CD has the same problem. My cursor did not start locking up until after I closed EVE Online in wine. Now the only thing that works is the root account. The live CD does not have root access, so that is why the cursor does not work. I am lost at why any non root account has issues with a locked up cursor. Could it be a hardware problem?

---

### Post by wolfgentleman on 2013-01-03
I am able to use the numpad to navigate, so it is a device lockup.

---

### Post by wolfgentleman on 2013-01-03
I just tried: [http://ubuntuforums.org/showpost.php?p=3003669&postcount=32](http://ubuntuforums.org/showpost.php?p=3003669&postcount=32) with no luck.

---

### Post by wolfgentleman on 2013-01-03
MY ROOT ACCOUNT JUST STOPPED WORKING! This time I was not using wine. I have to use my numpad for all accounts now! I need an answer PLEASE!

---

### Post by overdrank on 2013-01-03
Hi and welcome, please do not bump your thread so quickly. Once a day (24 hr) is polite.

---

### Post by wolfgentleman on 2013-01-03
ok. I am getting very frustrated. I cannot use any device specifically made to move the cursor. The only thing I am able to use to move the mouse is my numpad.

---

### Post by slickymaster on 2013-01-04
It may well be a shot in the dark, but try to run this:
```
synclient TouchpadOff=0
```

Edit: I am assuming that you're talking about a Touchpad and not a USB or PS/2 mouse.

---

### Post by fdrake on 2013-01-04
are you using an usb mouse or a regular one?

---

### Post by wolfgentleman on 2013-01-04
I don't have a touch pad, I'm on a tower PC. I use USB mice. My keyboard is PS2 though. Should I try a PS2 mouse?

---

### Post by wolfgentleman on 2013-01-04
Just tried PS2 mouse, it works. Why would USB mice not be working?

---

### Post by fdrake on 2013-01-04
> **wolfgentleman said:**
> Just tried PS2 mouse, it works. Why would USB mice not be working?

some USB mouse do not work well , We have found many bugs around them. can You post here the type or mouse and model

---

### Post by wolfgentleman on 2013-01-04
It was working fine then just stopped working.

[LIST=1]
[*]Logitech M310
[*]Generic brand-less Optical Mouse
[/LIST]

---

### Post by fdrake on 2013-01-04
plug the usb mouse and run
```

lsusb
lsusb -v -s $(lsusb | grep -i mouse | cut -d " " -f 2)
uname -a

```
paste the output.

---

### Post by wolfgentleman on 2013-01-05
attached them as text files.

---

### Post by wolfgentleman on 2013-01-05
All of the sudden my mouse started working! Why would USB mice work at random???

---

### Post by fdrake on 2013-01-05
> **wolfgentleman said:**
> All of the sudden my mouse started working! Why would USB mice work at random???

I am trying to find anythign interesting about your mouse model but nothign conctrete yet... Some ppl are affected some aren't...(on the same system)
Linux Mint seems to hadle it better then everyone, 

Does it make a difference if you boot with the usb mouse plugged or you blugged after when you have booted and logged in? What about after a standby/ hibernathion section(or locked screen)? I suspect this is due to the way the driver is loaded and unloaded into the kernel..

---

### Post by wolfgentleman on 2013-01-05
it doesn't matter how it is plugged in. Hotplug, plug before boot, after session change, after hibernation. It works at random. It stopped working again a few hours ago. I am having to use a crappy PS2 mouse... It's better than the numpad.

---

### Post by wolfgentleman on 2013-01-08
bump

---

### Post by wolfgentleman on 2013-01-09
bump

---

### Post by wolfgentleman on 2013-01-12
bump

---

### Post by wolfgentleman on 2013-01-13
bump

---

### Post by wolfgentleman on 2013-01-14
bump

---

### Post by wolfgentleman on 2013-01-15
bump

---

### Post by wolfgentleman on 2013-01-15
I'm beginning to think that this will never be solved.

---

### Post by wolfgentleman on 2013-01-16
bump

---

### Post by fdrake on 2013-01-16
@wolfgentleman

I suggest you to create a new thread sayin gthat you have an issue with your usb mouse (attach in you post the error logs you had attached here)

People do not like to read a thread with a lot of posts (it takes too much time to read and understand the issue).

---

