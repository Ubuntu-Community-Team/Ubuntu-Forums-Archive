---
title: "FreeRDP as Thin Client"
date: 2014-02-06
forum: General Help
---

### Post by mike-ratcliff on 2014-02-06
Hi,

I am looking to use FreeRDP as a thin client solution to connect to Microsoft Windows Server 2012, running Remote Apps (Remote Desktop Services).  I have created a virtual test client using the Ubuntu Minimal CD, onto this test client I have installed **xorg** and **freerdp. **

I am not sure if this question if best fit for the Ubuntu forums or a Microsoft forum, however here it goes.

I am connecting to the Windows Server with the following command: **xfreerdp -d domain -u username -p password --ignore-certificate server.domain.local** - This works great and starts a fullscreen RDP session on my test client and I am greeted with the Windows Server 2012 login screen, which I am then required to authenticate on to login. The problem is, if I connect again using the same command (from another machine) the first session is disconnected because the same user has connected. This rules out using a single account across all potential thin clients to connect to the server.

The idea behind this is that the PC will boot, automatically login to a restricted user account and launch FreeRDP without any user interaction, as far as the user is concerened their PC will still be running Windows. 

Do you know if it is possible to allow FreeRDP to connect to a Windows host without supplying any credentials on the command line and show the standard Windows login?


Many thanks,
Mike

---

### Post by TheFu on 2014-02-06
Can't help with anything around Windows - simply don't use it enough.
However, using a full Linux OS is overkill for this need.  Check out **TinyCore** - with a GUI, it is just 12MB in size.  I think the freerdp package is available for TinyCore.  The smaller the footprint, the less issue you will have and network boot is an option too.

---

### Post by mike-ratcliff on 2014-02-06
Thanks for your input TheFu. I will certainly take a look at TinyCore for this as well however I am much more familiar with Ubuntu - I've used the Minimal CD install which was only 30MB.

The problem lies with FreeRDP I think, I need to find a way to allow it to connect to an RDP server without authentication and then allow the user to log in using their normal Domain credentials on the remote desktop session.

---

### Post by TheFu on 2014-02-06
Well, the exact method used by the Windows domain to authenticate will need to known.  Microsoft has closed many security holes over the years, but a few still remain even with the latest authentication (even if using Kerberose).

Or you can replace AD with FreeIPA.

BTW, that minimal install is impressive - I'll be checking into that BIG TIME! Thanks!

---

### Post by Gonzalo_E._Alvarez on 2014-03-25
Hey there,

I think I found the solution, I was researching the same thing. If you start it with --sec tls it will ask you for password inside the login screen. I tested this with Ubuntu 12.01 and Windows 2012 R2.

---

### Post by yui2 on 2014-08-29
Hi,
i using Freerdp to connect my remote app on Mircosoft Server 2012 too..but i failed login. I tried alot of commend still cant. Can u all provide me some help?
Sorry, I'm newbie..

---

