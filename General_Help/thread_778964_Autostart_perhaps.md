---
title: "Autostart perhaps?"
date: 2008-05-02
forum: General Help
---

### Post by AlanR8 on 2008-05-02
Afternoon

Just set up a home server on an old P4 1.8 MHz with a Gig of RAM and a brand new 500 Meg hard disk. It works well and is fast!

I've just set up the standard desktop version of Hardy 8.04 and the intention is to run this box without a monitor and keyboard. 

Have set up KRDC and that works well, whilst the machine is logged on. If I shut it down and move it to it's permanent new home in a cupboard without the mouse and keyboard, then turn it on I CAN'T get to the machine remotely with KRDC. The error is "No server at that address....". I can however access the share from the network so for day to day file saving and sharing all is good. It seems that KRDC does not load until AFTER the log on screen is clicked through.

How can I get round this so I can administer the "server" from the comfort of any machine on the network? If Autostart is the answer, how do I set that up?

Applied some lateral thought processes to the problem. When I was in the IT business running a Windows 2000 desktop environment and an NT4 server structure over five sites spread out over the UK linked with a frame relay network, I used VNC to remotely log on to desktops. If I had to reboot the remote desk top it was no problem.

Big difference here in Linux as it appears that until the log on screen has been accepted certain services do not become available, KRDC being one of them.

So I went to \System Settings\Advanced\Login Manager\Convenience and selected the user and changed to "Auto login". I then tested and it worked! Not very secure so I went back to the same screen and selected "Lock Session".

Now I can log on to my remote "server" and do stuff from the comfort of my arm chair and Sony Laptop.

---

