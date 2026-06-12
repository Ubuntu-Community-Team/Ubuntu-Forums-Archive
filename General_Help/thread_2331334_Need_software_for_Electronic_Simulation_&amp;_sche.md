---
title: "Need software for Electronic Simulation &amp; schematic editing"
date: 2016-07-20
forum: General Help
---

### Post by liammcgillivray32 on 2016-07-20
I need help finding the right program to use for sketching electronic schematics and doing analog circuit simulations.  So far I've mostly used LTSpice through WINE, although recently I've been trying a web-based program called EasyEDA.  I'm still more comfortable with LTSpice.  I also tried (but did not like) Oregano, and gschem (gEDA Schematic.  I use Fritzing for PCB making, but it doesn't have circuit simulation.
I honestly don't want anything with a big learning curve, but something intuitive relatively "plug-and-play". I'll share my experience with these programs so far.  I don't want to have to learn too much that doesn't have to do with the electronic circuit itself.

LTSpice is alright but it has stupidly weird keyboard shortcuts, and it has no obvious way to scroll around the schematic.  What I like that has kept me using it is that doing simulations on it is rather painless.  It's more difficult than it should be to find documentation on stuff as simple as "How do I enter the capacitance value in microfarads?".

EasyEDA is a little less simple to get a simulation running.  The first time I tried the simulation it failed because some capacitor which appeared to be connected wasn't actually connected.  Unfortunately, the simulation didn't appear as accurate as LTSpice.  It also has a strange time limit for transient analysis.  However, the AC analysis (frequency response graph) was more plug-and-play than I expected.
I like it that it gives default values to components right when they're placed (so it won't tell me "No value of resistor 4" and I won't struggle to figure out how to set it.  I also like it that when a component is connected, it will move the wire if I drag the component.
I would prefer to have a program installed locally on my computer.

Oregano was awfully buggy, and not so intuitive to navigate.  I had to remake a schematic because the file of the old one got bugged-up.  It doesn't even have documentation.  Forget it!

Gschem was actually the first that I ever tried, but I have occasionally looked back at it.  But it's not a particularly smooth GUI, and setting the value of a resistor is not slightly straight-forward.  I couldn't manage to ever get the circuit simulation to work.

Here are my requirements for the program that I want;
[LIST]
[*]Easy to do a simulation with minimal set-up after making the circuit.  Not too likely to say "simulation failed" for some stupid bug-related reason. 
[*]Doesn't have stupid bugs to get in the way of the process and make the simulation fail, or give me headaches. 
[*]Keyboard shortcuts that aren't terribly weird.  Ctrl+Z should be undo by default.  It would be nice to also have shortcuts for drawing wires, rotating/inverting parts, and placing basic parts such as resistors.  Middle-click or right-click to scroll around. 
[*]A GUI that isn't painful to navigate. 
[*]Setting basic values of parts (such as resistance of a resistor, capacitance of a capacitor, maybe even voltage drop of a diode) should be straightforward. 
[*]Parts that default to realistic behaviour, rather than ideal behaviour.  One exception to this is voltage source, which I prefer ideal behaviour.  I don't mind if it has both (labeled) ideal & realistic varieties of parts such as op-amps. 
[*]It should have documentation. 
[/LIST]

I like making bass/guitar effects circuits (pedals) as a hobby.  This is much of what I'm interested in doing.  I like to see exactly what a circuit would do to a waveform.

Thank you to anyone willing to help me.

---

