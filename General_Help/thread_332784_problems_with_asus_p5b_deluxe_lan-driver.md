---
title: "problems with asus p5b deluxe lan-driver"
date: 2007-01-06
forum: General Help
---

### Post by jak0b on 2007-01-06
hi every one i have a homemade pc with a ASUS p5b deluxe motherboard with two gigabit lan ports...
i tried to install ubuntu edgy... it started up fine and everything... but when i tried to go on the internet it didn't work.. i think its because the drivers arent installed... så i insert my support cd ... find the file... but cant really understand what it is saying...(my english isnt good, and im kinda new to linux),
i think it uses sk98lin drivers.... or something... it is a marvell port

IS there anyone with the same problem? have you solved it? is there a step by step guide somewhere... (tried googleing it... but no luck - properly my english

OFFTOPIC:
Yes I know this is a repost... it's because i didnt get much help in the networking session...
 - am i the only one having problems with login in with windows?

---

### Post by Tenicus on 2007-01-06
I have a P5B as well.
No drivers are needed, that isnt the problem.  

Go to System, Administration, Networking
Its at the top of the screen.  What do you see?

---

### Post by jak0b on 2007-01-06
> **Tenicus said:**
> I have a P5B as well.
No drivers are needed, that isnt the problem.  

Go to System, Administration, Networking
Its at the top of the screen.  What do you see?

i see "wired connection" and "modem connection" (dunno if thats what it is called - i translated it) but only "wired connetion" is marked for selection...

if i choose properties (?) it shows me my ip adress and that other stuff (dunno how to translate that)

stupid language barrier :)

---

### Post by Tenicus on 2007-01-06
And "enable this connection" is checked?

---

### Post by tommcd on 2007-01-07
Tenicus,
Did ubuntu install easily on the Asus p5b? Is the chipset (intel P965 / ICH8R ) supported in Edgy now? I had read previously that the ICH8R southbridge was not suported by the linux kernel yet.

---

### Post by jak0b on 2007-01-07
> **Tenicus said:**
> And "enable this connection" is checked?

yes...
when i installed i had to manually configure my internet connection... and during the installation it downloaded something... so i dont see why it doesnt work now?'
how did you get yours to work?

---

### Post by Tenicus on 2007-01-07
> **tommcd said:**
> Tenicus,
Did ubuntu install easily on the Asus p5b? Is the chipset (intel P965 / ICH8R ) supported in Edgy now? I had read previously that the ICH8R southbridge was not suported by the linux kernel yet.

I had absolutely no problems installing.

---

### Post by joopajoo on 2007-01-08
So you didnt install any drivers for the lan and it worked right away?
In my ADSL box the network light isn't on for for the lan connection?
And how do I install my internet connection manually?

---

### Post by jak0b on 2007-01-09
I think i figured it out... :D !!!
First i thought there was something with Edgy... so i changed it to LinuxMint Bea - it is build on ubuntu... but the same problem :(... then i noticed an icon in the upperright corner of the screen where it said that there was no connection...

**-= so i changed the port my lan-cabel was inserted to =-** - there are to ports on the back... i had it in the one above and changed it to the one below
and then it said that i had a connection and now im writing from in "Bea"

Dunno if it is the same with edgy... it should be...
HOPE IT HELPS

---

### Post by sdumper on 2007-03-30
I still cant get mine to work can someone walk me through it im going nuts and im a linux noob

---

### Post by dbmnk on 2007-04-01
bumping in here with same problem, on an asus p5b-e motherboard, though. it only has one ethernet port, so I carnt just jump ports.

I've installed ubuntu 6.10, and it doesn't even display my ethernet device in the networking menu.

I've tried the trick described by dkamen:

[I]cd /home/user/[linux drivers from asus]
cd src
sudo make
sudo make install
sudo modprobe atl1[/I]

without any luck

my router is a siemens speedstream, no leds ignited where the ethernetcabel is plugged in, nor on pc.

there is a rather confusing description on how to compile/install/patch the drivers into the kernel, but that's beyond my capabilities

---

