---
title: "problem with wireless mouse"
date: 2023-04-17
forum: General Help
---

### Post by jgw on 2023-04-17
I have been having a problem with my mouse.  Sometimes it works great and then it doesn't.  I have no idea what is going on.  For instance, right now its working just fine but, five minutes ago it wasn't.  I use logitech mice and keyboards.  The logitech receivers are plugged into usb connectors.  There are four connecting receivers at the end of each 3 ft usb cable.  Solarr which tells me which receiver connects with what logitech wireless device.  I do not have the same problem with my wireless logitech keyboard.  When it goes bad sometimes it freezes everything up (not really all that often but it happens).  I am 15 feet away from the logitech receivers.

I think I must be doing something wrong but can't figure out what that might be.  I also have a logitech m570 wireless trackball.  Right now solarr tells me its covered but its not moving at all (not connected although solarr things it is).  A different mouse 
won't currently work but will if I move it closer to the receivers (bay about 2 feet it will.  The trackball will connect if I get up and take it over to the receivers and then it may or may not start to work.  All this is a mystery.  My regular mouse just stopped moving so I moved it forward about 2 feet and now it works but only 2 feet forward.

Thoughts?

---

### Post by aljames2 on 2023-04-17
I have never used the Logitech solaar usb receiver so I&#8217;m not sure if there is an issue with that unit itself, especially if there is any special firmware involved with it.  But, from experience using regular USB mice or keyboards on my ubuntu desktops, I have found that proximity is important.  I am using a logitech wireless mouse right now, and it works fine as long as I have the USB plugged in to the top or front of my case, but if I move it to the back of my case under my desk then the mouse gets flaky. Since most all my systems now are Linux, when I buy a mouse or keyboard I look for wires.  Sorry, probably not much help.

---

### Post by jgw on 2023-04-17
Thanks for the reply!

Couple of things.  First, solarr is just a program that checks for any receivers and then tells just which devices are connected and working.  Not a big deal but of interest.  Logitech receivers are supposed to work up to 30 feet.  Sometimes that's actually true.  I have actually, on occasion, gotten 30 ft away and it actually worked (kinda).  I prefer Logitech because it has something like solar so I know what is doing what.  

I wonder if there is some kind of thing that might increase the strength of the logitech receiver (just thought I would add this)

---

### Post by dragonfly41 on 2023-04-17
My Bluetooth Manager GUI shows connection signal strengths.  Might help to troubleshoot.

---

### Post by jgw on 2023-04-17
Thanks for the reply!

I don't thinki my mouse is bluetooth but I can probably download it and give that a try.

---

### Post by mIk3_08 on 2023-04-17
Try logging out or restart the system when every time you start your system and you encounter the USB devices wont work.
Then run the command below in your terminal:
```
lsusb
```
to check if your system just reads all the connected USB devices in your system. Regards and cheers

---

### Post by jgw on 2023-04-18
Thank you for the reply...

I am familiar with lsusb.

I have noticed, however, that mice care about the surface they are working on.  The best is absolutely flat and gets worse without that.

---

### Post by him610 on 2023-04-18
Logitech wireless mice use 2.4 GHz frequency band. I have heard that microwave ovens also use the 2.4 GHz band. Some wireless networks use the 2.4 GHz frequency band.
Maybe some other device is interfering (RFI) with the operation your mouse. I use Logitech wireless mice/keyboards on several machines without any issues, at least, none that I have noticed.
Make sure batteries are fresh, and properly installed.

Added: Underneath is a link to a Logitech white paper that discusses wireless peripherals. It has everything in it you ever wanted to know.

[https://www.logitech.com/images/pdf/emea_business/2.4ghz_white_paper.pdf]("https://www.logitech.com/images/pdf/emea_business/2.4ghz_white_paper.pdf")

---

### Post by jgw on 2023-04-19
Thank you for the replies.........

I thought I had written and sent this reply but it went up in smoke.  Anyway, I have found that a good amount of the problems I have been having have to do with the surface I use to move the mouse on.  I now know that a mouse works best on a flat surface.  A mouse pad is probably the best surface although I am currently using a piece of smooth wood I bought at goodwill.  

I also note that the mouse needs to be a bit higher than the height of the receiver connected to the computer.  I am sitting approximately 15 feet away from my computer.  All that being said I am having no problem with my mouse.  If I try and use my mouse sitting on the plastic of my chair arm my mouse just goes away.  Surface, height, and location need to be right.  If I stand up, go over the computer and try and use the mouse on my chest its a disaster.  Its also interesting to me that my wireless keyboard, connected with a receiver connected to my keyboard, doesn't seem to have all the problems I have experienced with a keyboard.  Perhaps its a bluetooth keyboard, I have no idea how to tell if it is or not.  I don't think so because of the usb receivers which, I think, are not bluetooth and my keyboard needs that to work.  

Its a bit embarrassing.  I have been playing with, and programming computers (not much of that anymore) for about 60 years.  I have taken wireless thing for granted for a long time.  I guess its time I get that one right.

---

### Post by #&amp;thj^% on 2023-04-19
> **jgw said:**
>  The logitech receivers are plugged into usb connectors.  There are four connecting receivers at the end of each 3 ft usb cable.  Solarr which tells me which receiver connects with what logitech wireless device.  I do not have the same problem with my wireless logitech keyboard.  When it goes bad sometimes it freezes everything up (not really all that often but it happens).  I am 15 feet away from the logitech receivers.

@jgw I just happened on your thread here: I use only "one" receiver for both my Keyboard and Mouse with no problems and they are both logitech:
```
D 046d:c52b Logitech, Inc. Unifying Receiver

``` 
Mouse is>>Logitech M705 Keyboard is>>Logitech K400.
I had similar issues as you show 3 yrs ago, Now i use just one receiver, and no more problems. (At times I also use Solarr to pair and unpair)
Your mouse may have dust or dirt in there.

---

### Post by jgw on 2023-04-19
I have a keyboard, 2 mice and a trackman.  I also have 4 recievers.  I did this just to see if I could.  Now I will move back to just the keyboard and a mouse.  Hopefully I might be able to do that with just one.

---

### Post by jgw on 2023-05-12
I will mark this as solved

---

### Post by ajgreeny on 2023-05-13
> **jgw said:**
> I will mark this as solved
So what was the solution, or did you just give up searching?

---

