---
title: "Jumpy Mouse Glitch"
date: 2006-12-16
forum: General Help
---

### Post by Deviltongue on 2006-12-16
Does anyone else have this problem. they're are surfing the internet or looking through their files or something when all of a sudden their mouse starts jumping all across the screen. how do u get rid of this?

-Deviltongue

                    P.S. I know this is unrelated to the thread but how do u switch to root?

---

### Post by hikaricore on 2006-12-16
> **Deviltongue said:**
> Does anyone else have this problem. they're are surfing the internet or looking through their files or something when all of a sudden their mouse starts jumping all across the screen. how do u get rid of this?

-Deviltongue

                    P.S. I know this is unrelated to the thread but how do u switch to root?


I had that problem with a generic mouse that I found somewhere, I replaced it with a mouse from my girl's system and the problem went away.  Try another mouse if you have one availible to you, or see if you can borrow a friends if they have an extra to spare.  Make sure you reboot after adding the new mouse to make sure everything is working properly.  Mine did this about every 20 minutes to 2hrs, just randomly.

--

You can use a terminal as root by typing:

```
sudo -s
```

or to run a single process as root:

```
sudo processname
```

:)

Hope this helps.

--Aaron

---

### Post by UncleFoo on 2006-12-25
I have the same problem with a microsoft mouse. I have tried a wheel mouse and non-wheel mouse, and it's constant. I'm about to give up on the whole thing, it makes the system pretty much unusable.
 I am going to try a different mouse. I will comment back in a day or 2.

---

### Post by dwasifar on 2006-12-25
> **Deviltongue said:**
> Does anyone else have this problem. they're are surfing the internet or looking through their files or something when all of a sudden their mouse starts jumping all across the screen. how do u get rid of this?

-Deviltongue

                    P.S. I know this is unrelated to the thread but how do u switch to root?

Is it by any chance a wireless mouse?  If so, is there another wireless mouse user close by?  I have two wireless mice on machines sitting right next to each other - a Microsoft and a Logitech - and when they are both in use, the Logitech interferes with the Microsoft in exactly the manner you describe.

To switch to root: 

```
sudo -s
```

---

### Post by notasquirrel on 2006-12-26
Are you sure it is not the surface it's trying to track on?  Try putting a piece of paper under the mouse instead of whatever you have there now.  I've seen the following weird behaviors that were consistent with a certain surface and would happen on nearly any optical mouse I tried (but of course not ball mice, and didn't try laser ones):

-- Randomly the mouse starts drifting in one direction or maybe vibrating back and forth, probably seeing a repetitive pattern that is hard to track and getting confused

-- Mouse suddenly believes it has moved a long way in one direction and flashes all the way to one side of the screen, or in a FPS game causes the player to spin around in a circle eight times really fast

-- Optical mice on some table surfaces will go smoothly in some places and jitter around a lot when over certain small spots on the table.  Has happened to me on three or four different tables.  Supposedly laser mice are supposed to not have this problem.


If the mouse is lurching all the way to the sides of the screen and will go all around some of the edges but won't leave the sides, I'm not sure what causes that but it is not optical tracking issues.  I've not seen that happen since the good old win95 / dos days, when the mouse drivers weren't quite set up right, but then again I haven't been using linux that whole time.

If the mouse wants to return to a certain spot and you have a really hard time getting it to move away from there, like sometimes you can get it away for a second but it lurches back, I've had that happen from my art tablet.  The pen fell out of its holder and was sitting on the tablet, and was sending a mouse event whenever the table jiggled or vibrated and sent the pen moving.  (Spent a good hour unplugging my mouse from usb, swearing at it, and putting it back in for that one!)

---

### Post by MarkusThielmann on 2007-02-22
I'm having the same problem. I just sucks :-)

Microsoft IntelliMouse 1.3A PS/2 Compatible

---

### Post by UncleFoo on 2007-03-17
I bought a new mouse (Logitech optical) and the problem went away.

---

### Post by CocoAUS on 2007-03-17
My problems is that my mouse likes to do random double-clicking when I only single-click, and that, for instance, when I grab a window or an icon and move it, if I got too fast (you know, average speed), it will let go of the icon or window and grab whatever's under the mouse at that point.  Thing is, my mouse is perfectly find under Windows.  And I never had that problem using Breezy or Dapper, and only rather recently using Edgy.  Anyone know what might be going on?

---

### Post by jkost30 on 2007-05-10
I have exactly the same problem!
my mouse jumps around the screen and clicks randomly everything
sometimes disappears and appears again when i move the wheel
then it starts moving horizontally and then everything returns to normal... :)

this weird behavior starts without doing something special...let's say surfing
the net and it lasts about half a minute...

At first i thought it was hardware problem...probably a memory error or a faulty
video card but now i see that many people face it...

My mouse is a BTC wireless but i'm pretty sure that it isn't interference! 
before i switch to Ubundu everything were fine with my mouse...

---

### Post by karlgg on 2008-01-14
> **notasquirrel said:**
> 
If the mouse wants to return to a certain spot and you have a really hard time getting it to move away from there, like sometimes you can get it away for a second but it lurches back, I've had that happen from my art tablet.  The pen fell out of its holder and was sitting on the tablet, and was sending a mouse event whenever the table jiggled or vibrated and sent the pen moving.  (Spent a good hour unplugging my mouse from usb, swearing at it, and putting it back in for that one!)

Thank goodness I hit this thread, after several unsuccessful searches.  I was having the "won't go anywhere/keeps going back" problem, and it was making me crazy.  I haven't used that box in a while, that I ran the Live disc on - I forgot it still had a tablet plugged in!

Moved the mouse-puck so it wasn't on the surface, and magically everything's okay.  :lolflag:

---

