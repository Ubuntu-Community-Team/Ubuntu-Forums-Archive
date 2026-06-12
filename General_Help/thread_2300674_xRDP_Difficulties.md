---
title: "xRDP Difficulties"
date: 2015-10-27
forum: General Help
---

### Post by Kevin_Tigelaar on 2015-10-27
Hello guys,

I am trying to get xrdp working on my server but I can't seem to figure it out. I'll try to give as much information as I can.

First thing I tried was a vnc server, but whatever I tried I kept getting the error:
[IMG]http://puu.sh/kZQ3D/b508611355.jpg[/IMG]
(I have the external port as 9999, it points to 5901)
I have tried SSH tunneling in Putty but it doesn't seem the connect at all.

After a couple tries with different vncservers/clients, I found out you could use the Windows Remote Desktop thingy built into Windows. After a bit research I installed it correctly but I am getting this error on the RDP client of Windows:
[IMG]http://puu.sh/kZQda/50faee9b0e.png[/IMG]

I have set the port of xrdp to 5901 in the xrpd.ini.

I have done a lot of research on the errors I'm getting but none of the solutions worked for me. For instance, the 0x1104 error can be fixed by disabling virtual styles in the RDP client, doesn't do a thing.

Hope to get an answer from you since I'm quite out of ideas.


Thanks in advanced!

Kevin.

---

### Post by TheFu on 2015-10-27
Welcome to the forums.

Is your server Linux or Windows?

If Linux, consider using the NX protocols which go over ssh and feel 2-3x faster than RDP or VNC. x2go is the tool. There is a client and a server. Only the ssh port is needed. Use the x2go PPA and follow their install instructions.  Takes 5 minutes if you don't understand it and 15 min if you have to read up (assuming ssh is already working and some approved DE/WM is already installed on the remote machine). Performance is great from any broadband connection in the world, IME.

IMHO-VNC and FTP should be dead like telnet is.

---

### Post by Kevin_Tigelaar on 2015-10-27
I have installed it and its works like a charm! Thank you so much :)

---

