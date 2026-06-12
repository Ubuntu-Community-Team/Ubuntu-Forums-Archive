---
title: "dual monitors need help please"
date: 2008-05-02
forum: General Help
---

### Post by NULL712 on 2008-05-02
OK I have searched for and wide but still can't get this to work. I have  ATI graphics card Radion family. It has DVI and VGA. I am using two CRT monitors on with a DVI to VGA adaptor. One monitor is older than the other but both support 1024x768 Rez. I want to be able to use both monitors as one large screen. If system specs and config files are needed I can supply them. I can also provide pictures of the set up,and whats going on with the screens if needed.

Any help is greatly appreciated.

Thanx Craig.

---

### Post by NULL712 on 2008-05-05
Well I figured it out!! =)  I just followed a howto from howtoforge and and I'm up and running. It's a simple solution but hay it works for me. 
[http://howtoforge.com/dual-monitor-setup-on-ubuntu7.10]("http://howtoforge.com/dual-monitor-setup-on-ubuntu7.10")

just follow the instruction and this persons screen setup may be different then yours so remember to plugin your own data. (Ex."xrandr --output TMDS-1 --auto --left-of VGA" was "xrandr --output DVI-0 --auto --left-of VGA-0" for me) You will notice that you virtual screen will not have panels. Just right click on one of your current ones and select New Panel, and drag it into place on your new virtual screen and start adding applets.

Hope this helps people Have fun! =)

P.S. I have a Linux Wiki at wetpaint.com, and I am looking for people to help me add content. Just sign up! [http://mylinuxifo.wetpaint.com/]("http://mylinuxifo.wetpaint.com/")

Thanx! 
Craig.

---

### Post by RAOF on 2008-05-05
Right.  If you don't feel like hitting the command line for this, System->Preferences->Screen Resolution is a GUI that does the same thing as the xrandr tool, and will apply your last configuration on login.

You still need to manually add the Virtual line to xorg.conf, though.

---

