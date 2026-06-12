---
title: "Connecting to Ubuntu 7.10 Remotely from Windows"
date: 2007-12-31
forum: General Help
---

### Post by TR3GO on 2007-12-31
Hello,

        I was reading up on remote connection to Ubuntu and I thought I would be a handy tool to have. I've read that FreeNX is the fastest and best remote software to do this.

How can I use FreeNX to connect securely (SSH) into Ubuntu from college or a friends house with my portable flash drive?

I have effectively used Putty to get into my Ubuntu system through the Unix environment, I just want to have the fluid visual experience as if I were sitting at my PC through a GUI environment.

Any help would be greatly appreciated! :D

Thanks!

---

### Post by dlegend on 2007-12-31
What I did (though this is from within the same network) is set up remote desktop via System > Preferences > Remote Desktop. I used TightVNC as my Windows client to connect. If you have a router you'll need to forward the proper port to your Ubuntu machine. 

Depending on the display, a different port will be used. I googled a precise answer for port number:
> 
**What port does VNC use? What is a display?**

VNC typically has one server per user running. It also typically assigns desktop (or ``display'') numbers in sequence, starting with '1' for the first instance created, as in the example in Subsection 1.4. To each desktop corresponds a port number. The port number is computed as port= display + 5900. So in the above case, the VNC server is listening for connections on port 5901.


I'm not sure if this helps but let me know.

---

### Post by TR3GO on 2007-12-31
I turned on remote connection in Ubuntu -- The only problem is I don't want to use VNC to connect since its not secure. I could tunnel it through puTTy via SSH. But I don't know how to do that at the moment.

I would like to use FreeNX because that incorporates SSH into the connection. Also they say FreeNX is much faster even over low bandwidth internet like my DSL.

Any further ideas?

Thank you!

---

### Post by sethfc on 2007-12-31
i'm a noob - trying to make a connection to my parents computer (from my dorm room) so i can help them maintain their new linux box.

so i'll be watching this carefully...

---

### Post by TR3GO on 2007-12-31
I found this good tutorial: [http://richbradshaw.wordpress.com/2007/11/28/installing-nomachine-nx-on-linux/34/]("http://richbradshaw.wordpress.com/2007/11/28/installing-nomachine-nx-on-linux/34/")

But I still can't seem to get it to connect.... Don't know why... It tells me CONNECTION TIMED OUT

---

### Post by paulkaye on 2008-02-13
Did you ever resolve this? I use logmein to access my PC and those of my parents, grandparents, wife and in-laws from anywhere. It's so simple and works perfectly through a browser without having to install anything. It's such a shame it's not linux-compatible. Is there anything this simple for ubuntu? Every option I've looked at would involve installing software on the client PC.

---

