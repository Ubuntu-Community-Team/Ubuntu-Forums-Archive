---
title: "Serial Port P5B"
date: 2007-06-19
forum: General Help
---

### Post by lank23 on 2007-06-19
Hello

I am trying to use my built in serial port to program a microchip using a jdm style programmer "PIC-PG2C" from Olimex, and Pikdev / Piklab software.  No matter what I do I can not get the serial port to communicate with the programmer.

Is there some way to test the serial port?

mother board = P5B
Ubuntu = 7.04 + updates

lank23

---

### Post by dr_dirk on 2007-06-22
I also have a P5B and I'm trying to use the onboard serial port for the first time.  I'm trying to get an external modem to work, but it is as if nothing were plugged in.  Have you ever had devices working on the serial port before in Ubuntu?  I'm also running 7.04 with all current updates.  Is it possible that for some reason Ubuntu doesn't like the serial port on P5B's, or is that a ridiculous notion?

---

### Post by lank23 on 2007-06-22
Well this is the second piece of hardware that I have tried on the port, but both do the same thing.

First I tried  a old serial port IRMAN, but no luck even though all of the need drivers did load and seemed to be working.  Finally I gave up on this unit thinking is was broken.

Second is the pic programmer that I know works just fine on a dell 4500 machine.  But it will not work on my Ubuntu machine.

I think that the correct drivers are loaded and the serial port is configured correct, but there is never any data sent out the port.

I am to the point of loading a Windoze version on a old hard drive to see what happens.

---

### Post by dr_dirk on 2007-06-23
I see.  I wasn't aware that the serial port might need configuring in order to work correctly.  Where might I look to learn how to configure the port, or to see if it in fact needs configuring?

---

### Post by lank23 on 2007-06-23
Google "linux serial port" this will get you started.  Then check out "setserial" program, this make life easy.

lank23

---

### Post by lank23 on 2007-06-30
Well the saga continued.  I installed windoze xp on a drive and got it booted, but the serial port would still not work.  Gave up on the serial port in the mother board and got me a cheap pci serial port card from tigerdirect, and now I have a working serial port.  I guess the mother board serial port is broken, now to get windoze off my machine before I get a virus...lol.

---

### Post by Kowalski_GT-R on 2007-07-19
I'm experimenting problems with serial port too.

I did a search about "setserial"

Basically Xubuntu 7.04 won't let me use my 9pin mouse.

How do I use the terminal using keyboard only?

---

### Post by dragonwings on 2007-07-19
im using a 15 pin serial modem with ubuntu 7.04  on  /dev/ttyso
and had no trouble at all .

may be you could get a serial to usb adpter cord
as i did for my mates macbook using  /dev/ttyso

---

### Post by Kowalski_GT-R on 2007-07-19
my bad, I meant 15 pin mouse.

Strangely enough I cannot open threads from my Mac@work, so I "hijacked" this thread...

my case is an old p/i P55 t2 p4 Mobo: no USB

and still no serial for me......

is there something I can check from the terminal? how do I access the terminal without mouse?(tried Tab key, no joy)

---

### Post by Shinoda on 2007-11-02
> **Kowalski_GT-R said:**
> I'm experimenting problems with serial port too.

I did a search about "setserial"

Basically Xubuntu 7.04 won't let me use my 9pin mouse.
See if [this]("http://ubuntuforums.org/showthread.php?t=202972#post1176847") helps.
> **Kowalski_GT-R said:**
> How do I use the terminal using keyboard only?
By default Ctrl+Esc is supposed to bring up the Applications menu in Xubuntu, but at least for me it works arbitrarily. In alternative you can always run [FONT=Courier New]xfce4-terminal[/FONT] through Alt+F2 or use a CLI (Ctrl+Alt+{F1|F2|...}; [Ctrl+]Alt+F7 returns you to the GUI).

---

