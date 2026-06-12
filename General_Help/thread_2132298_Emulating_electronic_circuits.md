---
title: "Emulating electronic circuits"
date: 2013-04-04
forum: General Help
---

### Post by grey1beard on 2013-04-04
I have recently built a piece of electronic hardware from the design here *[http://www.scribd.com/doc/88327081/Scope-Art](http://www.scribd.com/doc/88327081/Scope-Art)* for my daughter. This means she now has possesion of my oscilloscope :(

It occurs to me that it might be possible to emulate this via a clever piece of software, the circuit that is, as I know software scopes are available. The circuit has four oscillators, capable of either square wave or sawtooth, and a couple of phase changers and adders.

What I have in mind is being able to 'draw' boxes emulating different components, hook them together to create oscillators etc, then add in the rest by the same process, and finally output the resulting signals to a software scope.

I've tried searching for suitable software, but all I've found is either very basic, aimed at educational reqirements,or too advanced, aimed at professional designers for manufacturing.

Any thoughts or suggestions ? I'm currently using Ubuntu 12.04 LTS.

EDIT I suspect I should be using the word'simulation' rather than 'emulation' as I'll be looking for analog behaviour

John

---

### Post by ibjsb4 on 2013-04-04
> I've tried searching for suitable software, but all I've found is either  very basic, aimed at educational requirements,or too advanced, aimed at  professional designers for manufacturing.

That was my findings back in 09 when I played with some.  You know its possible to turn a computer into a scope and maybe get yours back :)

---

### Post by grey1beard on 2013-04-04
I fear that getting my scope back is only the first step. I suspect more projects will be following, so being able to simulate them rather than spending my pension on components might be preferable.
Never mind the solder on the new carpet ;)
John

---

### Post by grahammechanical on 2013-04-04
Perhaps you can list the applications that you have examined and rejected as unsuitable. That way we do not waste our time recommending stuff that you have already rejected.

---

### Post by HermanAB on 2013-04-04
You should look at Eagle.  It is a good tool for circuits and PCBs.

---

### Post by grey1beard on 2013-04-04
Hi Herman - I think,maybe wrong, that Eagle is for layouts->pcb's ?
I'm at the stage where I have built the hardware and am now looking to produce a software version of it,. 
This will then enable me to try alternative designs and see the results before commiting to hardware.
This last step may become unneccesary(sp?) if the software scope can produce the traces she's looking for. 
(Please see the article in the op link for info.)

Hi Grahammechanical - I would be happy to do so if my old brain could remember where I've been !
Another point is that I tend to 'reject' stuff if the overview doesn't contain the sort of facility I'm looking for, so I'd be content to go back on someone else's recommendation. That's why I've posted both the original link and a very brief description of what is involved.
Regards
John

---

### Post by mJayk on 2013-04-04
Haya,

I teach a physics class at uni and we use, what sounds like the exact same software you need.  Draw a box give it a component type and values (resistor, op amp w/e) link them up with lines (wires) click go and you get your output.

Ill be in tomorrow so I'll grab the name of it.

M

---

### Post by grey1beard on 2013-04-04
Hi M, sounds good. Waiting with great hopes.
Regards
John

---

### Post by conradin on 2013-04-04
I used to have a program that would monitor the sound card for input, and make the sound card into a o-scope. but I don't recall what it was called. Its limitation was audible frq.

A lot of my friends use gEDA, the repos have a program named oscilloscope, and maybe ngspice will have wht you need. 
Im a multisim user, which would do what you want, but isnt linux... as far as i know, they might have a version now, I have no idea.

---

### Post by grey1beard on 2013-04-04
Hi Conradin, and thanks for the heads up re multisim. I'll take a look. 
Regards
John

---

### Post by grey1beard on 2013-04-04
Just found and installed Qucs, so I'll try that out as a starting point and copy the hardware that I've just built.
If I run into a 'no go' area, I'll be able to spell out the gap that I'm facing in what I'm trying to do with a little more detail.

John

---

### Post by grey1beard on 2013-04-04
I've spent an hour drawing out a section of the circuit mentioned in the op using Qulp, and found a couple of problems.
The drawing part of the software is fine, setting out an analog circuit of a modulated audio oscillator using two op amps plus resistors,capacitors, and a control pot, and then realised there seems to be no way to connect a voltage onto the op amp. 
There is also no way to vary the pot as an output control, but that's a minor issue at the moment.
Crucially, I can find no way in the help files to examine the o/p of the oscillator. 
Perhaps I've started with something too complex in order to learn how to use the software, but I forsee major problems ahead with this one :(

John

---

