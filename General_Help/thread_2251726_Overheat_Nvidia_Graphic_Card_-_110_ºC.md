---
title: "Overheat Nvidia Graphic Card - 110 ºC"
date: 2014-11-06
forum: General Help
---

### Post by magamig on 2014-11-06
My nvidia GPU when I am playing games, in **very low settings and capped FPS (25 FPS)** it reaches an extraordinary **110º degrees Celsius.** And of course the computer shuts down. 

I use the nvidia binary driver from "Aditional Drivers" v331.89 (proprietary, tested).

My computer specs:
- nvidia geforce gt 620
- kingston ssd now v300 (128 gb)
- intel core 2 quad 2.3 GHz
- 4gb RAM
- HDD of 320 Gb for storage

---

### Post by tgalati4 on 2014-11-06
I presume this is a desktop computer.  Is this a discrete video card that plugs into a slot?  Check the fan.  If it is not spinning (due to dust) that would account for the heat.

Use compressed air to clean the computer out.  I have seen a graphics card's heat sink come loose.  Sometimes the plastic screws holding them down crack.  How old is this system?

---

### Post by magamig on 2014-11-06
> **tgalati4 said:**
> I presume this is a desktop computer.  Is this a discrete video card that plugs into a slot?  Check the fan.  If it is not spinning (due to dust) that would account for the heat.

Use compressed air to clean the computer out.  I have seen a graphics card's heat sink come loose.  Sometimes the plastic screws holding them down crack.  How old is this system?

This is a Desktop.
I have already cleaned the Graphic Card from the little dust it had.
I can also confirm that it is spinning. So I think this is a problem with the driver...
The heatsink is completely fixed can't even move it from the place it is.

The system itself is 5/6 years old, but the graphic card is only 1.5 years old. And the SSD has less than a year.

---

### Post by phidia on 2014-11-06
As you pointed out that is an extraordinary temp particularly for a desktop. I would be looking for other things that could produce that kind of heat.
Is the case fan working for instance-is something else malfunctioning like a ram module. Looking at the logfiles from the forced shutdown might tell us something. 
If you believe it must be the driver then you could try a driver direct from [Nvidia]("http://www.nvidia.com/Download/index.aspx?lang=en-us") to see if that makes a difference.

---

### Post by Pilot6 on 2014-11-06
This often happens, when you use noname graphics cards. It can't be fixed by software.
You can only replace the heatsink or the whole card. I had same problem with noname GT420. I replaced it with ASUS GT420 and got maximum 45 degrees.
New card had a lager heatsink.

---

### Post by tgalati4 on 2014-11-06
Sometimes the heat sink paste is not correctly applied or is worn out.  It would be worth removing the heat sink, carefully cleaning the GPU, applying a decent heat paste (like Arctic Silver) and reinstall the heat sink.  Try the open driver (nv or nouveau) and see what the temperatures are.  I doubt that the proprietary driver would cause overheating--usually it is the other way around--the open driver doesn't have access to power-saving features (like dynamic clocking) to reduce temperatures.  

I would not rule out a power supply problem.  At 5 or 6 years old, the power supply could be dropping voltage (12VDC specifically) causing more current to drive the graphics card and higher temperatures.

---

### Post by pqwoerituytrueiwoq on 2014-11-06
i don't think a gt 620 with a correctly installed cooler can get anywhere near that temperature unless your ambient temps are insane
does it feel like it is putting out heat? you would feel it easily near the back of the chip without touching the board if it is really that hot

as for what gbalati4 said about the PSU, grab a multimeter and hook it up to the yellow and black pins on a molex plug and set it to dc voltage and see what it shows you under load (use the black pin next to the yellow one)

---

