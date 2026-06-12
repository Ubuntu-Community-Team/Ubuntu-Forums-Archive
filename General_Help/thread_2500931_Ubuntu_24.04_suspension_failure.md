---
title: "Ubuntu 24.04 suspension failure"
date: 2024-09-16
forum: General Help
---

### Post by chetinho10 on 2024-09-16
[COLOR=#000000]Good morning.

When my computer with an AMD dedicated graphics card is suspended it does not come back from sleep.

I have to connect the cable to the integrated one, restart the computer, and after that, reconnect the DisplayPort cable to the dedicated one to have the image again, how can I solve it?

Thank you.

Greetings.[/COLOR]
[COLOR=#000000]
[/COLOR]

---

### Post by chetinho10 on 2024-10-02
[COLOR=#000000]Hello

Please, I still cannot solve this problem, if I have the monitor off and I turn it on or with the HDMI input active, and I turn on the other computer connected through DisplayPort, if I don't realize it on the login screen the device goes into mode suspension after a short while and the screen remains black without being able to exit suspension and I have to restart the computer.

It happens to me with the AMD RX 7800 XT graphics card, with the integrated graphics card it doesn't happen to me and the computer comes out of sleep mode without problems.

How could I solve it?

Greetings.[/COLOR]
[COLOR=#000000]
[/COLOR]

---

### Post by him610 on 2024-10-02
I recently experienced a similar issue with a 2-port hdmi/usb switch. It was really bothering me until I found a way.

My system uses Xubuntu 24.04.1 so you may or may not have the same controls using Ubuntu 24.04. It may be necessary for you to install *Ubuntu Tweaks*.

Maybe this will help....

From Settings, click on Power Manager, navigate to tab General, under Buttons, 
When poweer button is pressed: Ask
When sleep button is pressed: Do nothing
When hibernate button is pressed: Do nothing
When battery button is pressed: Do nothing

From Settings, Power Manager, navigate to tab System, under Power saving,
Move *When inactive for* slider to left until it indicates Never

From Settings, Power Manager, navigate to tab Display, under Display power management, 
move *Blank afte*r slider all the way to the left until it indicates Never
move *Put to sleep after* slider all the way to the left until it indicates Never
move *Switch off after* slider all the way to the left until it indicates Never

Be advised mine is a desktop machine, not a laptop.

---

### Post by chetinho10 on 2024-10-03
[COLOR=#000000]Good afternoon.

I have modified these options but it is still not solved, once I have logged into the computer it does not happen to me since I have disabled suspension, it only happens to me during startup, I have to have the screen and the corresponding input (DisplayPort) on so that it does not It happens to me, if I have the other input selected (HDMI) or the monitor turned off, and I turn on the computer later, when I get to the login screen it goes into sleep mode and the screen remains black and does not come out of there.

It's a bit annoying because sometimes you don't realize that you have the monitor with the HDMI input selected and you turn on the computer, and the only solution when it goes into sleep mode is to restart the computer.

Thank you.

Greetings.[/COLOR]

---

