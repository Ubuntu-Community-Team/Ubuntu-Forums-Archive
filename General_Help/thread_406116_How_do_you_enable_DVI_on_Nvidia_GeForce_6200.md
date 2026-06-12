---
title: "How do you enable DVI on Nvidia GeForce 6200?"
date: 2007-04-10
forum: General Help
---

### Post by dwasifar on 2007-04-10
I have a new DVI monitor, I want to use it with my GeForce 6200 card, but there is apparently nothing coming out of the DVI port on the card.  Is there an xorg.conf setting to wake up the DVI port?

---

### Post by jubjubrsx on 2007-04-10
its probably not your video card where the problem lies but its possible.....because most video cards ive seen/used will output mirror images on a db15/dvi port so which ever place you plug your monitor in it should get a signal

since, my monitor has a dvi and a db15 connectors on it, there was a setting i actually had to set in the control panel of the monitor to switch its output.

---

### Post by jimbob on 2007-04-10
Put this statement in the Device section of your xorg.conf file:

        Option      "UseDisplayDevice"  "DFP"
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

 *[SIZE="1"]... when the game is over the king and pawn go in the same bag ...[/SIZE]*

---

### Post by dwasifar on 2007-04-10
That did it, thank you!

---

### Post by Tye on 2007-11-16
G'day,
    I also have a nVidia 6200 and i cannot get anything out of
the dvi port , but i do on the vga port, I tried the solution here and that didn't work.

I thought maybe it was because I had two monitors connected so I tried only the DVI and still no luck. I also cannot choose the twin view option which is what I am after. I have read almost all the dual monitor threads but nothing seems to work, 


cheers

---

### Post by jimbob on 2007-11-16
Here is my xorg.conf file for you to try if you wish.  (Don't forget to save yours first).

---

### Post by Tye on 2007-11-17
Thanks for your help.


       I tried it with the  Option "UseDisplayDevice" "DFP"

     It might be because its a NV44A ( a cheap 6200)

      

  
   Here's my xorg.conf file.

---

### Post by jimbob on 2007-11-18
I see no reason that your DVI port should not work.  Is this a separate board or is it built into the MB? Is the output BIOS selectable if it is a built-in board? Does your board have the two connectors like mine; the DVI plus a 15-pin D-sub?

What kind of monitor are you using? Does it have both types of connectors also?  Have you checked the monitor setup to see if you can select between the two types of input?  Is your DVI cable the proper type?  Could it be defective?

Just some random thoughts.

---

### Post by Tye on 2007-11-25
I too cant figure it out


It is a AGP nVidia 6200 256MB Card
It uses the NV44A Chip ( it's the cheap version )

I can get dual screens in Winblows and a clone screen if I use the Vesa drivers in linux
i have never used  on-board graphics and have upgraded my Graphics card a couple of times

My main Monitor has only the vga connection and my secondary monitor has vga and DVI

I once installed ubuntu using the secondary monitor and DVI port.
it worked fine until I installed the nVidia drivers so I'm positive that it's a driver issue 

I have read in one of TS Elliots threads that there is a way to fix this but the solution didn't work
for me.

It's no really big issue for me, just a quirk that annoys me
that something so simple in winblows is a headache for ubuntu

I am a firm believer that ubuntu is the way of the future for home users
I've been using ubuntu since 4.10 (wasn't that a nightmare lol)

whats really sad is that I've been able to convert zero friends to linux
mainly coz they are to lazy to learn anything new

oh well, I'm upgrading soon anyway.

cheers

---

### Post by jimbob on 2007-11-25
You might try posting the question on Alberto Milone's blog.

[http://albertomilone.com/wordpress/](http://albertomilone.com/wordpress/)

I'm fresh out of ideas, sorry.

---

