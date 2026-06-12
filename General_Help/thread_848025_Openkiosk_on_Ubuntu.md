---
title: "Openkiosk on Ubuntu???"
date: 2008-07-03
forum: General Help
---

### Post by 4t0m1c_w07f on 2008-07-03
HI
I am looking for a good cafe management system and I stumbled upon Openkiosk. I would really like to use this program but I have one simple error... It is made for KDE not Gnome...

Is there anyway that I can run it on Ubutnu and not have to re-install with kubuntu??

---

### Post by RealPSL on 2008-07-04
It would be easy enough to just install the kubuntu desktop with ```
sudo tasksel install kubuntu-desktop
```. I guess it would make sense to uninstall the ubuntu desktop with ```
sudo tasksel install ubuntu-desktop
``` too.

---

### Post by Gunman1982 on 2008-07-04
Why uninstall the ubuntu-desktop? Its not like kde and gnome hate each other (even the developers work together) so just leave it on the system if you are not too concerned about diskspace and like to have the option to choose either kde or gnome at startup.

I have kde,gnome and xfce installed, works like a charm.

---

### Post by RealPSL on 2008-07-05
The uninstall is not a requirement. However if you are looking to lock something down to a kiosk level and your lock down software only supports KDE then leaving a gnome option might leave you exposed.

---

### Post by 4t0m1c_w07f on 2008-07-06
My problem though is that the gnome desktop is a lot more friendly to windows users especially the way that I have set it up.

I have been able to isolate the executable which I can now run successfully under gnome. The only thing standing in my way is jnodeview which I have absolutely no idea about. It works through a web page loaded on the server.

---

### Post by konungursvia on 2008-07-06
Just install it without kubuntu. KDE software runs fine on gnome as well, it just has to add a few dependencies, which aptitude will do for you.

---

### Post by 4t0m1c_w07f on 2008-07-06
Thanks

And any suggestions about jnodeview?

---

### Post by deebocean on 2008-10-09
hey 4t0m1c, i am glad you got kiosk to work, but would you share us how did you do that, i just got lost for many days to get it work but no go.
so if you please give us step by step begining from downloads links, installation, till you got it works on ubuntu gnome , that would be very kindness from you.

---

### Post by 4t0m1c_w07f on 2008-10-26
> **deebocean said:**
> hey 4t0m1c, i am glad you got kiosk to work, but would you share us how did you do that, i just got lost for many days to get it work but no go.
so if you please give us step by step begining from downloads links, installation, till you got it works on ubuntu gnome , that would be very kindness from you.

I didn't manage to get it to work.. :(

---

### Post by deebocean on 2008-10-28
that's so sad, i had tried to contact the owner to ask for paid support but no answer :( , anyway i think it's about time until a fully featured net cafe software appears like windows's.

---

### Post by 4t0m1c_w07f on 2008-10-28
Yeah, I really hope so... It just means a lot more control over the customers..

---

### Post by marianlibrarian on 2009-07-30
Has anyone managed to get OpenKiosk to work?

I too, have tried to make contact with the owners of the application. I left a message on the list serve today. There is no documentation anywhere that I can find. The help buttons within the application do nothing.

However, I was able to "successfully" install the client on a Kubuntu 8.0.4.2 computer. I have installed the Node Viewer on my Windows XP machine. I can see the client in my Node View window as soon as they login. But this is what I see if I try to do anything like send a message or restart or logoff, etc.:
> Tracking operator: Director
Starting Kiosk Lock Protocol listener...
Listening for requests on the network...
8:58 am Station PAC02 offline
Error in connecting to station 192.168.1.36: the connection was refused. Please check your network connection

I was able to manually "reserve" an IP address for the Node View computer (windows xp). However, when I tried to manually reserve the IP for the Client (Kubuntu) computer, I lost connection to the internet. 

Any ideas or thoughts are appreciated.

---

