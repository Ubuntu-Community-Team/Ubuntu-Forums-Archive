---
title: "How to Setup a VPN Server??"
date: 2007-07-12
forum: General Help
---

### Post by NiceGuy12 on 2007-07-12
Hello all,

I am new to Linux/Ubuntu ... and would like to install it on an empty P4 System I have. My goal is to build a VPN server.

I have never set up a VPN Server before ... but am not daunted by the task of doing so. Having said that, I wll not pretend that I know exactly what needs to be done. For this project .. I think its far to consider me a newbie.

Having said that .. before I begin I need to know if I have the proper setup. I plan to build the VPN server and run it behind my ADSL modem/router ("Siemens Speedstream 6250 wireless ADSL Gateway") at my house. My setup would be similar to:
  
>                
         
| VPN Server | --------  | Router/ Modem | ---------* *  Internet ** -----------  |  Client  | 
 


I guess my confusion right (before I begin) is at the modem/router.  The one that I have was given to my from my ISP (Bell Sympatico) for free as part of my subscription. Its really nothing fancy
but I guess to keep things simple I would like to know:
[B]
1. Is my setup is possible?? 
2  Do I need to configure something on the router/modem to achieve my goal??
3. Suggested readings??
[/B]
Additionally my router modem does not have a VPN pass through option. It does have some DMZ configuration abilities as well as port forward/mapping abilities. 

So do I have all the ingredients to create me desired setup??
Thanks and I apologize for the long post
Take Care

---

### Post by SgtDude on 2007-07-16
> 1. Is my setup is possible??
Yes (since your router does port forwarding)

> 2 Do I need to configure something on the router/modem to achieve my goal??
Yes (you'll have to forward the ports your VPN server will be listening on)

> 3. Suggested readings??
Well, if this post were somewhere else, I would tell you to check ubuntuforums.org, but as you're allready here, I have no suggestions.  I actually came across this post looking for some VPN answers myself.  I'll post here as I find information on this subject, but as this is a side project for me, don't expect hourly updates ;)

---

### Post by bodhi.zazen on 2007-07-17
See if this helps you at all :

[http://doc.gwos.org/index.php/Reverse_VNC](http://doc.gwos.org/index.php/Reverse_VNC)

---

### Post by wasutton3 on 2008-05-29
that link is apparantly stuck in a permanant loop, does anyone have any other ideas?

---

