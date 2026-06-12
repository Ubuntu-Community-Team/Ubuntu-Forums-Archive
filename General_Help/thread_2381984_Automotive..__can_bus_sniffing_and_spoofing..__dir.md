---
title: "Automotive..  can bus sniffing and spoofing..  direction needed"
date: 2018-01-07
forum: General Help
---

### Post by oddballmotorsports on 2018-01-07
Hello everyone!
so my main project over the winter.  get my chevrolet engine control computer to fire the engine in my hot rod.  basically what I am using is a truck engine from a newer Chevrolet.

  A quick tutorial on how it works when installed from the factory in the vehicle it was intended for.  inside the ignition key tumbler is a set of magnets and resistors.  when the key is turned it sends an analog signal to the body control module.  if the value is correct the body control module sends a digital signal over the can bus to the engine control computer that it is okay to pulse the fuel injectors. 

 From what I have learned is the engine computer inherently knows what its looking for when the body control module sends it's signal.  To me that says it has to be vin based.   since I have access to a running factory truck with this combo as well,  I would like to use an OBD2 -> usb cable and watch the data over the can bus while starting.  I've seen some talk about using socketCAN to do this, but really don't have an idea of what program to get to watch the data.     then I would like to take the starting data,  and try and sort out what exactly the data is during the "handshake" process, and how it possibly correlates to the vin.  with that then program an arduino to send the okay to start signal to the computer in my hotrod.  there are other ways to do this, but are much more expensive.  I'm not 100% sure this is going to work, but could use some suggestions on how to watch the can bus.  thanks folks!

---

### Post by dragonfly41 on 2018-01-07
Found some possible tips here ...

[https://fabiobaltieri.com/2013/07/23/hacking-into-a-vehicle-can-bus-toyothack-and-socketc](https://fabiobaltieri.com/2013/07/23/hacking-into-a-vehicle-can-bus-toyothack-and-socketc)

---

### Post by Autodave on 2018-01-07
If the key for the truck motor has/had a pellet that you can see, it is just a resistor. If so, measure the resistance of the key, cut the wires at the base of the column or at the input to the ECM and splice the resistor that you got from Radio Shack or online somewhere into the harness so that the ECM thinks it is seeing the correct key.

---

### Post by oddballmotorsports on 2018-01-07
I wish it was that easy..  thats passlockII passlockIII is a totally different ballgame.. since its going into a non standard vehicle, with a different security system,  bypassing it at the source (the ecm) vs a key fake out will retain all the factory imobilizers of both the new engine, and the car its going in...

---

### Post by jeremy31 on 2018-01-07
So is this a transponder system?

---

### Post by oddballmotorsports on 2018-01-07
not quite..  its resistors and magnets in the key barrel.  kind of a weird system.  honestly though I feel that what happens before the can bus is unimportant, I will not have the body control module, nor the barrel,  just the engine computer listening on a spoofed can bus line hopefully..  I have two options to make this work, first (easiest but most expensive) is have the engine computer flashed to remove the security, or figure out exactly what the data is and spoof it

---

