---
title: "Putty SSH Tunneling Problem"
date: 2007-08-29
forum: General Help
---

### Post by cjlindem on 2007-08-29
I have a windows 2003 server at home, and connect to is with SSH, using tunneling to get access to VNC and RDP from behind the firewall at my work.

This works fine from a windows XP client.  But when I try to connect in the exact same way from Ubuntu 7.04, I get 'connection refused' when trying to connect to either VNC or RDP.  The SSH connection connects fine, it just seems as though tunneling is not working at all.

These are my tunnels:
L3389  localhost:3389
L5900  localhost:5900

I don't know if I need to somehow open ports 3389 and 5900 on the linux box?

And because my work is using an HTTP proxy, I have not found a command to connect to my SSH server at home via command line, and rule out if the problem is specifically with putty.


Thanks in advance for any help,

---

### Post by KCPokes on 2007-08-29
I don't have access to my Ubuntu machine, at the current time, so I'm reciting from memory.  Can you verify in your SSH config that you have AllowTCPForward set to Yes.  Without that set you will not be able to loopback and tunnel, which sounds like is your current issue.

---

### Post by cjlindem on 2007-08-29
I wasn't under the impression that putty used any of OpenSSH's settings files.  It is what I'm using for the client.  As far as the server settings go, I was able to get the tunneling working just fine on an XP client so I don't think there is any issue with the server's settings.

Do you think I could be uncommenting something in /etc/ssh/ssh_config ?

Thanks for any further help.

---

### Post by cjlindem on 2007-08-29
Hmm I seem to have an option that is letting it work on Ubuntu now.  Putty->Connection->SSH->Tunnels->'Local Ports accept connections from other hosts'. 
This setting wasn't required in Putty under windows.

Real test will be for me to try from work tomorrow, that's where I was initially having the problem.  But it seems without that option checked I can replicate the same error on my home system.

I'll post a followup once I know.

Thanks,

---

### Post by cjlindem on 2007-08-30
The setting I mentioned above, 'local ports accept connections from other hosts' is working from my work, so thats apparently all I was missing.  Strange it is required only on Linux clients.


A second question, though maybe I should address it in a new post.  My work is using an HTTP proxy server to restrict internet access.  I have to specify this in my Putty settings (proxy-server port 8080).  If I wanted to accomplish the same thing using command line ssh, I have not figured how (if) there is a way to specify a http proxy server.

---

