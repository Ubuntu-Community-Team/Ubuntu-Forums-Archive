---
title: "Ports Problem"
date: 2006-10-20
forum: General Help
---

### Post by Orbit45244 on 2006-10-20
I'm having a problem with ports on my computer, I assume.  I'm trying to set up SSH.  I have all the keys made, and everything is in place, but when I go to use an ssh command to connect to the computer, the terminal gives me an error that the connection was rejected at port 22.  Same thing happens with XDMCP.  I enable it, but when I go to connect with it, nothing shows up as an availiable host.  But the funny thing is, Rsync works just fine.  So I am stuck and need help.  I have a Firestarter firewall installed, but I have the computer set up to disable it on startup.  Even if it didn't get disabled, I have opened the ports in the firewall. I am running Dapper.

---

### Post by wieman01 on 2006-10-20
> **Orbit45244 said:**
> I'm having a problem with ports on my computer, I assume.  I'm trying to set up SSH.  I have all the keys made, and everything is in place, but when I go to use an ssh command to connect to the computer, the terminal gives me an error that the connection was rejected at port 22.  Same thing happens with XDMCP.  I enable it, but when I go to connect with it, nothing shows up as an availiable host.  But the funny thing is, Rsync works just fine.  So I am stuck and need help.  I have a Firestarter firewall installed, but I have the computer set up to disable it on startup.  Even if it didn't get disabled, I have opened the ports in the firewall. I am running Dapper.
If you are using Firestarter then you need to open ports on both the server & the client machine:

>> Client: "Outbound traffic policy" -> 22
>> Server: "Inbound traffic policy" -> 22

See snapshots for "inbound" and "outbound"...

BTW: Once you have installed it, it runs on startup, no matter what. The GUI is NOT Firestarter, it's just a tool that helps you configure it. So even if you don't see the icon in the task tray, it is running as a process in the background.

---

### Post by dcstar on 2006-10-20
> **Orbit45244 said:**
> I'm having a problem with ports on my computer, I assume.  I'm trying to set up SSH.  I have all the keys made, and everything is in place, but when I go to use an ssh command to connect to the computer, the terminal gives me an error that the connection was rejected at port 22.  Same thing happens with XDMCP.  I enable it, but when I go to connect with it, nothing shows up as an availiable host.  But the funny thing is, Rsync works just fine.  So I am stuck and need help.  I have a Firestarter firewall installed, but I have the computer set up to disable it on startup.  Even if it didn't get disabled, I have opened the ports in the firewall. I am running Dapper.

If you want to test if a connection to a port is possible:
```
telnet ip-address port_no
```
You should (eventually) see a connection or a "Connection refused" message if there is either something blocking the port (or there is nothing listening on the port).

---

### Post by Orbit45244 on 2006-10-20
> **wieman01 said:**
> If you are using Firestarter then you need to open ports on both the server & the client machine:

>> Client: "Outbound traffic policy" -> 22
>> Server: "Inbound traffic policy" -> 22

See snapshots for "inbound" and "outbound"...

BTW: Once you have installed it, it runs on startup, no matter what. The GUI is NOT Firestarter, it's just a tool that helps you configure it. So even if you don't see the icon in the task tray, it is running as a process in the background.

But, I have set my computer to run a script when I login, which runs a firestarter command to disable the firewall.

---

### Post by wieman01 on 2006-10-20
Ok, do you have a Windows Manager / GUI? Can you fire up Firestarter and see what's going on?

---

