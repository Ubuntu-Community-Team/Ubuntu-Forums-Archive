---
title: "XFCE Printing"
date: 2015-06-03
forum: General Help
---

### Post by zoomy942 on 2015-06-03
I'm a sharp guy but I have no idea how to make this work.  I like the lightweight XFCE environment but i REALLY like the printing manager in regular Ubuntu (Unity? Gnome?).  

Can I install that print manager in XFCE?  I don't mind if it installs extra parts via dependencies, as long as it works.

PZ

---

### Post by Bucky Ball on 2015-06-03
You could try installing system-config-printer-gnome from Synaptics. 'Printers' should then pop up in 'System' (or possibly 'Preferences' if you have that, I'm running a minimal install with xfce4 rather than a full Xubuntu so could be different for you). 

Let us know how that works (I thought this was installed in Xubuntu by default anyhow).

---

### Post by zoomy942 on 2015-06-03
thank you!

It installed but now when I open the print manager, it says printer service is not started.

---

### Post by Bucky Ball on 2015-06-03
Hmm. All I can think of is there might be a conflict with the existing printing setup in Xubuntu, but doubt this, or ...

Have you restarted the machine? Just might need to turn the printing service on and that might do it (logging out and in may achieve the same). Also, if you check in Settings> Session and Startup> Applications and make sure you have the 'Print queue applet' ticked to start when you boot the machine.

When you try to start 'Printers' and get this message, can you cancel the message and you end up with the printers GUI anyhow? If so, can you add a printer? Was your printer installed prior to this (with the correct drivers and working with the Xubuntu set up)?

---

### Post by leunam12 on 2015-06-03
I once installed the gnome printer manager on LXDE and it gave me a lot of problems, I had to uninstall it. I don't know if it's the same with XFCE. Have you tried managing your printers from the CUPS web browser interface? Open Firefox and type: localhost:631 on the address bar and press enter.

---

### Post by Bucky Ball on 2015-06-03
> **leunam12 said:**
> Have you tried managing your printers from the CUPS web browser interface? Open Firefox and type: localhost:631 on the address bar and press enter.

This is another (good) alternative and bypasses using a 'Printers' GUI altogether. I generally set printers up and maintain them using the CUPS interface as suggested by leunam12.

---

### Post by HermanAB on 2015-06-03
You don't need yet another print manager.

Just type in your browser:
[http://localhost:631](http://localhost:631)

---

### Post by zoomy942 on 2015-06-04
Sigh.

I'm really rusty.

This worked - sudo /etc/init.d/cups restart

---

### Post by Bucky Ball on 2015-06-04
Your issue is solved? If so, please have a look at the second link in my signature. ;)

---

### Post by zoomy942 on 2015-06-04
Done and done!

---

### Post by Bucky Ball on 2015-06-04
Enjoy! ;)

---

