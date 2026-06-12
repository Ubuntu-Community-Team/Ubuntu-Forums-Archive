---
title: "Boot black screen with a message"
date: 2016-05-06
forum: General Help
---

### Post by paulo_ferreira2 on 2016-05-06
Hello, i just upgraded from Ubuntu 15.10 to 16.04.
Everything was alright until i got a 100% usage of cpu i searched and i found that noveau drivers maybe was causing this, so i changed to proprietary drivers.
Now i can't boot into my desktop, if i boot in the normal way after the purple screen saying "Ubuntu" i get this message: "/dev/sda8: clean, 241391/4235264 files, 7230305/16920576 blocks" in a black screen. 
Then i tried to boot with recovery mode, this way i can reach the login screen but i can't login, i write my password and then i return to the login screen again. How can i solve this?[COLOR=#111111][FONT=Consolas]

[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-05-06
paulo_ferreira2; Hello ;

Let's see what it is going to take to get you a graphic's driver installed.
At the login screen key combo ctl+alt+F1 will yield a console interface. Log in here with your credentials.
Once in console, execute:
```

lspci -k | grep -EA2 'VGA|3D' | nc termbin.com 9999

```
which will xfer to the pastebin site what the graphics hardware is . 
The result is a URL back in terminal, pass that link back here . We then match the hardware to a driver to install.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by paulo_ferreira2 on 2016-05-06
[Http://termbin.com/aoqs](Http://termbin.com/aoqs)

---

### Post by Bashing-om on 2016-05-06
paulo_ferreira2l Well ..

What we now know, you are running hybrid graphics, and Nvidia recommends the 361 version driver for your card:
Intel takes care of it's self .
[http://www.nvidia.com/download/driverResults.aspx/101423/en-us](http://www.nvidia.com/download/driverResults.aspx/101423/en-us)
So next is to see what the X layer  logs relate :
```

cat /var/log/Xorg.0.log | nc termbin.com 9999

```
let's see if the Nvidia driver got built .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by paulo_ferreira2 on 2016-05-06
[http://termbin.com/w7c9](http://termbin.com/w7c9)
I changed from noveau to 361 drivers in the drivers menu.

---

### Post by Bashing-om on 2016-05-06
paulo_ferreira2; Hey;

The driver builds and it is the recommended driver version.

However;
> 
22.562] (WW) NVIDIA(0): Unable to get display device for DPI computation.

22.664] (WW) Warning, couldn't open module x11glvnd

Begs the question of what monitor are you using; a TV by some chance ?

What is in the driver config file ?
```

cat /etc/X11/Xorg.conf | nc termbin.com 9999

```

[INDENT][INDENT]still in the dark
[/INDENT][/INDENT]

---

### Post by paulo_ferreira2 on 2016-05-06
I am using my laptop screen.
[http://termbin.com/p45dv](http://termbin.com/p45dv)

---

### Post by Bashing-om on 2016-05-06
paulo_ferreira2; Well ..

I see nothing wrong there either.

Let's try and start the GUI from that console.
What results :
```

systemctl isolate graphical.target

```
any errors reported back in the terminal ?

Maybe take a look at what the GUI log relates ?
```

cat .xsession-errors | nc termbin.com 9999

```

[INDENT][INDENT]still in the dark
[/INDENT][/INDENT]

---

### Post by paulo_ferreira2 on 2016-05-06
[http://termbin.com/ev43](http://termbin.com/ev43)
I got no errors by running the first command but it got stuck on the ubuntu splash screen.

---

### Post by Bashing-om on 2016-05-06
paulo_ferreira2; ouch .


Curious and curiouser .
> 
cannot connect to brltty at :0

when you installed the 361 driver, have you rebooted the system ?
And what distribution is this, and what is the Desktop that you are using ?

still in the dark ->
[INDENT][INDENT][INDENT]still can not get to the desk top
[/INDENT][/INDENT][/INDENT]

---

### Post by paulo_ferreira2 on 2016-05-06
When i installed the 361 driver i rebooted and then this happened. This is Ubuntu 16.04 unity desktop.
[COLOR=#000000]*[I]cannot connect to brltty at :0*
Can you tell me what does it mean?[/I][/COLOR]

---

### Post by Bashing-om on 2016-05-07
paulo_ferreira2; Welp;

That means that there is no means of communications with your display ( :0) once the graphic's driver is loaded. As to why, no idea yet.
I have not run unity for several releases - so I have but limited experience . However, let us see what we can learn:
What do these logs relate ?
```

cat /var/log/lightdm/lightdm.log
cat /var/log/lightdm/x-0-greeter.log

```

[INDENT][INDENT]in the process of learning
[/INDENT][/INDENT]

---

### Post by mc4man on 2016-05-07
Try taking a look at /var/log/gpu-manager.log when trying to boot to nvidia (just go to a tty, log in, cat and or copy the log. The log will be meaningless if booting to Intel drivers

---

