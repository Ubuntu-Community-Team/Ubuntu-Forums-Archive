---
title: "reset all settings"
date: 2007-05-12
forum: General Help
---

### Post by duch11 on 2007-05-12
hi are there a way to reset all my network settings 
maybe with a sudo command or something i would be realy glad if u can help me
i cant connect to anything wireless or lan.. nothing i cant even change network settings..
i just wanna start over with the network part without reinstalling ubuntu..
:D

---

### Post by jimbob on 2007-05-12
What version of Ubuntu are you using?  Does your wired network connection work at all?

What have you done so far?

I guess apt-get remove --purge network-manager might be a start.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by duch11 on 2007-05-12
well im using feisty fawn.. :D
and i cant remember what i did.. 
so i what does that command exactly do..
AND.. how do i use the command.. (i have bad experiences with commands)
:D

---

### Post by jimbob on 2007-05-12
First tell us some more about your computer, your system hardware and available network connections.  Sounds like you might have wireless capability.

Are you connecting through a modem?  Is it ethernet, DSL, what?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by duch11 on 2007-05-12
well im connected to a 2 mbit dsl connection..
the internet has been working for a long time on ubuntu.. 
but now it doesnt work..
i have been traveling a lot with my computer.. and yes a have a wireless connection..
i have 1 wireless connection called "WLAN" at my school, 1 called "default" at my mates house and 1 called 
"holms net" at home
the net used to work at school dont know at home.. but it didnt work at my mates house..

well..

i have also tried to connect to the internet by wire at my school.. (have worked before now it doesnt work)

and i have also tried to connect to my own switch (doesnt work) :'(

but arent there a way to go back to "default settings" in the connection area..

or just reinstall everything related to connections and network..

---

### Post by jimbob on 2007-05-13
Try what I suggested in my first post.

sudo apt-get remove --purge network-manager net-tools

Then re-boot your system and re-install them again.  Hopefully everything will have to be set up again for your networks.

sudo apt-get install network-manager net-tools

That's all I can think of other than a re-install of Ubuntu, sorry.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

