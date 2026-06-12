---
title: "Ubuntu (6.10) Shows up on Windows Network when it Darn well pleases.  :("
date: 2007-03-14
forum: General Help
---

### Post by Adam_GUI on 2007-03-14
Yet another Samba thread.

*sigh*:( 

Anywho.  I'm at my Pop's Windows machine, working on my last MSAccess assignment.  I want to listen to MP3s I have stored on my Ubuntu machine upstairs and stream them through iTunes on the Desktop downstairs running XP.  I got the login-thingamagiggy settled and working how I wanted it last night.

I shut down my computer for the night and turned it back on this afternoon.

Now on both XP boxes, the XP boxes see each other on the network.  But only the Ubuntu box sees the Ubuntu shares.

I know there's a work around for this, but I figured I'd go ahead and ask anyway.  

Thanks for any help you can give me in advance!

--Adam

---

### Post by gus sett on 2007-03-14
:?: can you ping for the Ubuntu machine IP address, and if so what kind of response
     occurs
:?: is there a usual boot up sequence among the machines on the network when
    all are up and available
:!: retrace your steps and track down the little things you might have changed
    when obtaining the login prompt.

> **Adam_GUI said:**
> Yet another Samba thread.

*sigh*:( 

Anywho.  I'm at my Pop's Windows machine, working on my last MSAccess assignment.  I want to listen to MP3s I have stored on my Ubuntu machine upstairs and stream them through iTunes on the Desktop downstairs running XP.  I got the login-thingamagiggy settled and working how I wanted it last night.

I shut down my computer for the night and turned it back on this afternoon.

Now on both XP boxes, the XP boxes see each other on the network.  But only the Ubuntu box sees the Ubuntu shares.

I know there's a work around for this, but I figured I'd go ahead and ask anyway.  

Thanks for any help you can give me in advance!

--Adam

---

### Post by Adam_GUI on 2007-03-14
> **gus sett said:**
> :?: can you ping for the Ubuntu machine IP address, and if so what kind of respond 
     occurs
:?: is there a usual boot up sequence among the machines on the network when
    all are up and available
:!: retrace your steps and track down the little things you might have changed
    when obtaining the login prompt.

1.  No, I cannot Ping the IP on my Ubuntu machine.  Even though it's connected to the same router and can connect to the internet.

2.  I'm not sure what you mean.  If you mean the normal booting procedures, they all come up behaving normally.

---

### Post by darrenm on 2007-03-14
> **Adam_GUI said:**
> 1.  No, I cannot Ping the IP on my Ubuntu machine.  Even though it's connected to the same router and can connect to the internet.

2.  I'm not sure what you mean.  If you mean the normal booting procedures, they all come up behaving normally.

You really should be able to ping the Ubuntu machine. If you can't there's a major problem or you have a firewall enabled.

---

### Post by Adam_GUI on 2007-03-14
> **darrenm said:**
> You really should be able to ping the Ubuntu machine. If you can't there's a major problem or you have a firewall enabled.

So where do I go from there?
Is GuardDog, or another firewall program, on edgy that I have to tweak?  
I'm pretty sure the problem is on the Ubuntu side of the equation.

---

### Post by darrenm on 2007-03-14
> **Adam_GUI said:**
> So where do I go from there?
Is GuardDog, or another firewall program, on edgy that I have to tweak?  
I'm pretty sure the problem is on the Ubuntu side of the equation.

If you haven't enabled the firewall or installed firestarter or anything then it won't be enabled. The firewall isn't switched on by default on Ubuntu.

Are you absolutely positive you can't ping the Ubuntu machine? Are you sure you have the correct IP? Can you ping the Windows machines from the Ubuntu machine? If so then you have a problem thats related to something like the network card not being supported correctly, a network card fault, a fault with the network media or connection or set up somewhere.

As I say ICMP echo requests are a pretty fundamental part of the kernels networking. It has to work.

---

### Post by Adam_GUI on 2007-03-14
> **darrenm said:**
> If you haven't enabled the firewall or installed firestarter or anything then it won't be enabled. The firewall isn't switched on by default on Ubuntu.

Are you absolutely positive you can't ping the Ubuntu machine? Are you sure you have the correct IP? Can you ping the Windows machines from the Ubuntu machine? If so then you have a problem thats related to something like the network card not being supported correctly, a network card fault, a fault with the network media or connection or set up somewhere.

As I say ICMP echo requests are a pretty fundamental part of the kernels networking. It has to work.

D'oh!  I pinged the wrong IP.  I have the printout of ifconfig in front of me, and just overlooked it.  I think I know where to go from here.

---

