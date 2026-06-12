---
title: "Serial Port data push to program"
date: 2022-05-25
forum: General Help
---

### Post by kp1187 on 2022-05-25
Hi everyone. New to the forums and a little better then beginner with Ubuntu. At my work, we have been using Windows based PC's on the production floor for label printing and connection to our fixtures. We have been having issues with them and are looking to switch to Ubuntu for use instead. One of our sister plants already uses Ubuntu based PC's successfully. All our PC's connect to the fixture via serial port. However, their fixtures use a different PLC then we use and they can use the data coming in straight in the program we run. Our PLC's don't do that. The data I have coming in is garbage. I've confirmed that the serial port has the correct settings in Ubuntu and that's as far as I can get. I've tried using Minicom and one other program but neither one can see the data or manipulate it as we need.

We use IBM CMS, the java version. Maybe I haven't been doing the correct search terms to find what I'm looking for. Or I should have just come here sooner and ask the Guru's. The program we use on Windows to take the serial port data and send it to Windows is called CPS Plus. It takes the incoming data and sends it to Windows as keystrokes. It allows us to choose ASCII, Hex or Dec for how the data is presented as well as filtering options. And that's what I'm looking for on the Ubuntu/Linux side. Does anyone have any suggestions?

Example:
PLC sends "111"
CPS filters "111" and replaces it with "40000{13}" then passes it to Windows.

The PLC's we use can't currently send the carriage return either. They are supposedly able to but our build guys and programmers haven't been able to figure it out. Any suggestions or pointers would be greatly helpful as we would really prefer to switch over to Ubuntu, or even another Distro, if we can get this to work. we have over 40 PC's on the floor.

Thank you in advance.

---

### Post by The Cog on 2022-05-25
The first thing I'd look at is what kind of "garbage" you are receiving. The usual reason for serial data looking like "garbage" is that you have the line speed (or number of stop bits, or parity) wrong.
Particularly, if half the characters look right suspect parity. Of course, it really helps if you know what the incoming data should look like. But it is worth trying different speed, stop-bits and parity settings. You are likely to have to write your own replacement for CPS, for which you will need to know exactly how CPS processes the data.

---

### Post by grahammechanical on 2022-05-25
Hi,

This is a user forum. Some of us have years of experience as administrators of Linux systems. A lot of us are like myself. We have years of experience as home users. You are using technical terms that are unfamiliar to ordinary Ubuntu users. You may even be referring to specialized equipment that only users of that equipment would know what you are talking about.

Please satisfy my curiosity. What is a PLC? And what is a CPS? And What is a fixture?

Regards

---

### Post by HermanAB on 2022-05-26
Howdy,

You should install a program called Cutecom to debug your serial port communications.

It is a graphical utility and works very well.

Cheers,

Herman

---

### Post by dragonfly41 on 2022-05-26
I'm guessing from a quick search that this is some industrial process control system .. "production floor" ..

[https://www.researchgate.net/figure/Architecture-of-the-control-portion-of-a-CPS-P1-P2-Pn-denote-PLCs-Each-PLC_fig2_333649686](https://www.researchgate.net/figure/Architecture-of-the-control-portion-of-a-CPS-P1-P2-Pn-denote-PLCs-Each-PLC_fig2_333649686)


I will intuitively throw in an idea (untested) although this skirts the problem of "garbage" passing.

[https://www.rabbitmq.com/](https://www.rabbitmq.com/)

This allows one-to-one and one-to-many communications and can be setup quite easily using any of a number of languages with a local RabbitMQ server or a remote service (supported).

[https://www.rabbitmq.com/devtools.html](https://www.rabbitmq.com/devtools.html)


[P.S.] Explore Scribus for creation of labels for printing. process

---

