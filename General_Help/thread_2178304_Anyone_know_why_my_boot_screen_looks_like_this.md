---
title: "Anyone know why my boot screen looks like this?"
date: 2013-10-02
forum: General Help
---

### Post by ddubbz1979 on 2013-10-02
[IMG][[IMG]http://s21.postimg.org/3seltgbvn/20131002_182852.jpg[/IMG]]("http://postimg.org/image/3seltgbvn/")[/IMG]

Runs off left side of screen with a 2inch black vertical bar left on the right side.  Can't read all the options so good thing I know where they are.  I did the original install of 13.04 on another monitor then switched to this one.  Looked fine on the first one.  Not sure if that's the problem but thought it worth mentioning for troubleshooting.  I would like to correct it because its driving me nuts with my OCD about perfection lol.  Thanks in advance for any help or input.

---

### Post by oldos2er on 2013-10-02
Have you tried adjusting your monitor settings?

---

### Post by ddubbz1979 on 2013-10-02
Wasn't sure about that cause everything displays ok once loaded.

Edited to note the Dell 19" I have is set to 1440 x 900 16:10

---

### Post by pqwoerituytrueiwoq on 2013-10-02
i know you can set the resolution in /etc/default/grub

---

### Post by 1clue on 2013-10-02
Are you using the old-style monitor connector, or DVI, or hdmi?  I'm guessing that you're using the old style analog monitor.

---

### Post by ddubbz1979 on 2013-10-03
> **1clue said:**
> Are you using the old-style monitor connector, or DVI, or hdmi?  I'm guessing that you're using the old style analog monitor.
yes its the analog style.  Came with the monitor.

---

### Post by ddubbz1979 on 2013-10-03
[COLOR=#000000]sudo gedit /etc/default/grub?

Edited to add when I did this it gave me [/COLOR]GRUB_GFXMODE=640x480

---

### Post by ddubbz1979 on 2013-10-04
Looks like more of a position problem than a resolution problem but I suppose reso could be the culprit.  Anyone recommend what resolution to change it to in grub?  I tried the position settings in the monitor menu from the front panel and its so off I couldn't even get close.

---

### Post by 1clue on 2013-10-04
If you have a DVI port or an HDMI port on both the computer and the monitor, you might get everything solved by just switching to a digital-only cable.  Digital screens just don't get this sort of thing.  They also have much clearer pictures than analog.

---

### Post by nerdtron on 2013-10-05
When I get a picture like this on my screen the first thing I do is press the "Auto Adjust" of the monitor. :)

---

### Post by Donut50 on 2013-10-08
have you tried grub customizer?
you can download it from the software centre and you can also configure the grub resolution.

---

### Post by heir4c on 2013-10-08
> **nerdtron said:**
> When I get a picture like this on my screen the first thing I do is press the "Auto Adjust" of the monitor. :)

That is the right answer for this problem. Look on your monitor and find a button with "auto". Just push in the button.
No Grub configuration need.

---

### Post by ddubbz1979 on 2013-10-09
> **nerdtron said:**
> When I get a picture like this on my screen the first thing I do is press the "Auto Adjust" of the monitor. :)


didn't work for me.  first thing I tried

---

### Post by ddubbz1979 on 2013-10-09
> **Donut50 said:**
> have you tried grub customizer?
you can download it from the software centre and you can also configure the grub resolution.
any idea of what reso to try?

---

### Post by ddubbz1979 on 2013-10-09
> **1clue said:**
> If you have a DVI port or an HDMI port on both the computer and the monitor, you might get everything solved by just switching to a digital-only cable.  Digital screens just don't get this sort of thing.  They also have much clearer pictures than analog.

hdmi out on the box, but no in on the monitor unfortunately.

---

### Post by 1clue on 2013-10-09
I know this probably isn't really all that welcome an idea, but modern flat screens are really cheap right now, and they take up a lot less room on your desk.  If your video card is digital (which it almost certainly is, given the HDMI) then I seriously doubt your problem could exist on a modern LCD.  And your monitor will probably outlast your computer anyway, so you can use it on the next one.

---

### Post by 1clue on 2013-10-09
Actually try this:  If you have a TV with HDMI on it, then try plugging your computer into your TV.

Another test:  Try finding any other computer monitor and see if it works normally.  This tells you if the problem is with the video card or with the monitor.

---

### Post by ddubbz1979 on 2013-10-09
> **1clue said:**
> I know this probably isn't really all that welcome an idea, but modern flat screens are really cheap right now, and they take up a lot less room on your desk.  If your video card is digital (which it almost certainly is, given the HDMI) then I seriously doubt your problem could exist on a modern LCD.  And your monitor will probably outlast your computer anyway, so you can use it on the next one.

my monitor is a flat screen lcd.  19" Dell actually.  Probably only 3-4 years old at most.   I see another input next to the computer cable connector, but its not hdmi.  Really not sure what it is.  Looks like a bunch of square pins fit in it actually.  I've only ever used standard computer cables over the years cause I've just always got one laying around, or they come with the system I bought at the time.  Never considered hdmi.  Maybe its a DVI that I'm using now.  When I change inputs on the monitor it says analog though.

---

### Post by ddubbz1979 on 2013-10-09
> **1clue said:**
> Actually try this:  If you have a TV with HDMI on it, then try plugging your computer into your TV.

Another test:  Try finding any other computer monitor and see if it works normally.  This tells you if the problem is with the video card or with the monitor.

I installed Ubuntu on this system using a 15" dell lcd monitor and it was fine.  haven't checked it since though.  but it did not show the boot screen all jacked up initially after installation.  It's also wiggling or jumping a little until boot completes.

---

### Post by 1clue on 2013-10-09
The jiggle is related to boot?  That means more that it's in the computer end.  Try powering down and then re-seat your video card.

Or, possibly hook the monitor up to another computer and see if it works fine there.

If the pins of your mystery port are lined up in a grid of 3 rows that line up perfectly square, then it's probably DVI.  DVI is usually a white plastic surrounded by a metal shield. It has a flat pin on one end that runs parallel to the long axis of the connector, right in the middle.  It's more square than the old-fashioned D-sub connector which is 3 rows offset from each other.

DVI would be a good connector too, but the old-fashioned monitor port is surely analog.

I guess what I'm trying to get at is that your computer starts out with digital information, and if you have an LCD then it has to end up with a digital signal since each pixel has specific data attached to it.

The sort of offset you're looking at here is typically a problem with an analog signal, which means (I think) that you're using an analog component somewhere in the mix.

---

