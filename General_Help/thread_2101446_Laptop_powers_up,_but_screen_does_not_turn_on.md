---
title: "Laptop powers up, but screen does not turn on"
date: 2013-01-04
forum: General Help
---

### Post by meh_phistopheles on 2013-01-04
I have an interesting problem. Basically, as the title says, my laptop powers up and boots to the desktop, but the monitor does not turn on at all. My laptop is a Dell Latitude D820.

What happened was my computer kept crashing as I was playing a game, so I held the power button down to turn the computer off on three separate occasions. The first two resets were fine, but after the third one, the monitor never came back on.

My computer doesn't exactly boot up perfectly anymore either. If I turn the computer on, it will get hung up after 5 seconds in this weird spot it's never been hung up at before. If I close the lid and open it back up though, that continues the boot up process.

One thing to note is I have an Nvidia graphics card with third party drivers installed. I suspect that may be part of the problem. Also, I am familiar enough with the command line to be able to open a virtual terminal and type in commands. That's how I figured out the computer still boots to the desktop, by switching to a virtual terminal and going through the prompts I can't see to type the shutdown command. If you so try to give me a command line solution though, please make sure you list all the prompts, since I won't be able to see them.

Thanks!

---

### Post by takuie on 2013-01-04
Sounds to me like a driver issue.  

Can you see anything on the monitor at all, like POST or anything like that?
Is your system a dual boot? 
What version of Ubuntu are you running? 

 Need more data.  Try plugging an external monitor to your laptop, check bios make sure something there isn't set to shut off the monitor.

That's where I would start.

---

### Post by jvano on 2013-01-04
Wen you start up the laptop , the screen is completely dark or you see the DELL logo.

Maybe the inverter of the LCD or the LCD itself is broken.

Try to conect a external monitor to the rear VGA shocket on your laptop to verify that the computer boot and the video adapter is ok. 

Last thing , On Dell laptops ther is a key stroke combination to switch between internal and external (vga) monitor , hold FN and Push F8 .

Take a llok to the user manual -->  [http://www.google.es/url?sa=t&rct=j&q=dell%20d620%20special%20keys&source=web&cd=3&ved=0CEYQFjAC&url=http%3A%2F%2Fdata.technimax.cz%2Fattach%2Fartilky%2Fdelld620manual.pdf&ei=cD7nUIraLYaShgfIjIGoBg&usg=AFQjCNGteq3HfshsGDX5vC4ZOupmEzvpXg&bvm=bv.1355534169,d.ZG4&cad=rja]("http://www.google.es/url?sa=t&rct=j&q=dell%20d620%20special%20keys&source=web&cd=3&ved=0CEYQFjAC&url=http%3A%2F%2Fdata.technimax.cz%2Fattach%2Fartilky%2Fdelld620manual.pdf&ei=cD7nUIraLYaShgfIjIGoBg&usg=AFQjCNGteq3HfshsGDX5vC4ZOupmEzvpXg&bvm=bv.1355534169,d.ZG4&cad=rja")

---

### Post by meh_phistopheles on 2013-01-04
I'm on my phone, so quoting is difficult. To answer both your questions though, I see absolutely nothing on the monitor when I turn the computer on. No Dell logo, nor a BIOS if I tap f2 the whole time. The only indication I get is the LED indicator by the keyboard. Also, I am on Xubuntu 12.10, and I am not dual-booting. 

I will have to give the dual monitor thing a try. I can't do it immediately though, or any time in the foreseeable future for that matter, because I don't have a monitor lying around anywhere. I did declare my computer as dead for then past month, but decided to ask about it here just to see.

---

