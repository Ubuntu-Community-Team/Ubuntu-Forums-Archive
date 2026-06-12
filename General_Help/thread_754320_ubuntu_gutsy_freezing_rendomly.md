---
title: "ubuntu gutsy freezing rendomly"
date: 2008-04-13
forum: General Help
---

### Post by contactpraveen2001 on 2008-04-13
hi 
I have amd atholon 3200+ with msi (RS480m2-il) motherboard with ati redon 200 graphics(onboard)
the problem is that my ubuntu get freeze randomly, the screen become white some time it has lines also, no keyboard detection no mouse detection, nothing works the only solution is to restart the pc . It is more like ubuntu get crash. I am not getting what is the problem. I installed restricted driver which ubuntu prompt me to install. I think it's opengl. Here is my xorg.conf file

---

### Post by diablo75 on 2008-04-13
If you have compiz enabled, you can try disabling it:

System>Preferences>Appearence>Effects (tab)

Then select None from the list if it's not already selected...

If it locks up again, can you try hitting CTRL-ALT-Backspace to see if it kills your X session and takes you back to the login screen?

---

### Post by contactpraveen2001 on 2008-04-14
well the problem is not because of Compiz. when it get freeze keyboard and mouse both doesn't work. Alt+Ctrl+Backspace also does not work. The only solution after that is hardware system restart.

---

### Post by diablo75 on 2008-04-15
Open your case up and check to see if there is a lot of dust built up inside.  Dust in large quantities can short circuitry out and cause a lot of mysterious problems to happen.  It can also cause your CPU to overheat, if your heatsink/fan is clogged.  If it's not dusty, make sure that your fans are all spinning when the computer is on.  If you built the computer yourself, you might want to remove the heatsink from the CPU and see if you need to reapply some thermal grease to the CPU die so as to maximize heat transfer to the heatsink.

Also, if you have an Ubuntu Install CD, I would recommend you use it to conduct a memory test, to ensure that it's not faulty.

Good luck!

---

### Post by contactpraveen2001 on 2008-04-15
Thanks for your reply.
i try the things which you suggest already. My rem is also working perfectly i test it. I thing problem is due to my ATI graphics. I install fgrlx driver. I also tryed the latest ATI open source driver  but the problem is still same.

---

### Post by diablo75 on 2008-04-15
Have you checked to see if your BIOS is out of date?  You should visit the website of the computer/motherboard manufacture, look up the model number and compare the version number or release date of the bios they have online for your model and see if it is newer.

How many PCI expansion cards do you have in the computer?  You might try opening the case, pulling out as much hardware as you can (or disconnecting) until you're down to the bare minimum to get the system running (hard drive only, no floppy connected, no CD-Rom connected, as few PCI cards as possible, and one stick of ram if it's at least 256 MB.  Run the system like this for a little while with as little hardware in use as possible).  If the system seems to act more stable at this point, it could indicate a problem with either an individual component you had just removed, or the power supply.

There is a possibility your power supply is either failing, or is not producing enough watts to provide the system with as much energy as is needed at a steady rate.  Disconnecting hardware as described above will also help determine if this might be causing your problems.  Let us know what you find.

---

