---
title: "SSH and a University Network"
date: 2007-10-12
forum: General Help
---

### Post by Scheater5 on 2007-10-12
I have a desktop set up in my dorm room I would like to access remotely when I'm at home or in class.  I've tried to do this kind of thing before, but I've never been able to get it to work, so I'll freely admit I could be missing something or making a stupid mistake.  I believe I have the additional problem of port 22 being blocked.  (I know the network firewalls occasionally block ports, as you can't access IRC from on campus - however you can SSH).  I found the external IP of the desktop via whatsmyip.com, and attempting to SSH to it yields the result 

ssh: connect to host 199.120.31.19 port 22: Connection refused

I don't think port forwarding will get the job done, 'cus I'm still gonna hit the University's firewall, won't I?  I'm not really sure how to go about accessing this computer.  Anyone have any ideas?

---

### Post by cwaldbieser on 2007-10-12
> **Scheater5 said:**
> I have a desktop set up in my dorm room I would like to access remotely when I'm at home or in class.  I've tried to do this kind of thing before, but I've never been able to get it to work, so I'll freely admit I could be missing something or making a stupid mistake.  I believe I have the additional problem of port 22 being blocked.  (I know the network firewalls occasionally block ports, as you can't access IRC from on campus - however you can SSH).  I found the external IP of the desktop via whatsmyip.com, and attempting to SSH to it yields the result 

ssh: connect to host 199.120.31.19 port 22: Connection refused

I don't think port forwarding will get the job done, 'cus I'm still gonna hit the University's firewall, won't I?  I'm not really sure how to go about accessing this computer.  Anyone have any ideas?

You desktop is likely on the university LAN behind a gateway using NAT (network address translation).  So if you are trying to ssh into it from off campus, you are out of luck unless the campus provides you with some kind of VPN access to the university LAN.

If you are in class, you are probably still on the LAN, so the rules may be different, depending on how the campus network is set up.  You will want to try to reach your LAN IP address.  You can find it out from the terminal with the "ifconfig" command.

To see if connectivity exists between a remote computer on the university LAN and your computer, log into the campus PC, open a command window, and try to ping your IP address.

---

### Post by trippinnik on 2007-10-12
You may also need to configure SSH to use another port, depending on what your University does on it's network.  I used to do this quite a bit at my university (and using SSH remotely was one of the reasons I fell in love with using linux)

---

### Post by rscott5 on 2007-10-12
You will also want to apply for a Static IP Address from your campus. I know at my college it is really easy, just a matter of going to a webpage and putting in your ID and password and it immediately takes effect, but I'm sure the process is different from school to school. You will need to have their firewall allow port 22 for your new static IP. I would say send an email to your campus network people, I'm sure someone has wanted to run a server before and they can help you out. Good luck!

---

### Post by Scheater5 on 2007-10-12
Thanks for the replies guys.  I think what I may need to do is SSH through a different port.  I've got openssh-server installed on my laptop, and I will install it on the desktop in my dorm soon.  So I think what I'm going to try and get SSH to listen on a different port (preferably 22 as well as another one, so that if I forget to reset it after I leave campus it will still work).  Can anyone walk me through that, or point me to instructions?  I think the command sshd is what I need to use.

---

### Post by bcl1713 on 2007-10-12
I can almost guarantee you that you are having a NAT problem.  When you try to connect to the "external IP" you are connecting to the IP assigned to the school by their ISP, not your personal computer.  Running the  ssh server on a different port won't solve the problem because the schools routers do not know where to send the request.  Port forwarding is possible however it is unlikely that the network admins at your school will allow it.  Have a chat with the IT department.  Talk to the network admins and plead your case.  Be ready to explain exactly why you need access and good luck...  Odds are they're going to tell you no. :(

---

### Post by Scheater5 on 2007-10-12
Well, the school is an ISP from what I can tell.  Whatsmyip.com lists the ISP as Coastal Carolina University, with a range of external IP's assigned to it.  I do know that the University network covers a wide range, including wifi in most buildings and four different complexes of dorms, so I can believe that.

---

### Post by timcredible on 2007-10-12
99% chance the university is nating.  so, the ip address you got via whatsmyip.com means nothing - it's not your ip address, it's the nated ip of the firewall/proxy.  if i read your post right, you want to access from the internet INTO the university, so you need to:

1 - get a static ip for the pc on the university network
2 - have the IT department of the university setup port forwarding

i wouldn't do it on my network, and i doubt they'll do it, but you can try.

---

### Post by Scheater5 on 2007-10-12
Ok, so remember what I said it's was entirely possible that I was missing something stupid?  I didn't know that the NAT router affected my external IP - and yes, I do know that they have "are nating."  I know the IT guys, and I can assure you they won't do anything like that for me.  However, I would like to be able to SSH into my computer from elsewhere on campus as well.  Is there any way I can do that?  Or I could almost as easily take the computer home and set it up there, and then SSH *out* of the university network - would that be easier?

---

### Post by bcl1713 on 2007-10-12
SSHing out to a computer at home would be much easier.  As far as getting to your box from a computer on the local network... that should be as easy as using your local IP which you can find by typing ifconfig.  This is assuming that it is all one network.  Slippery Rock University had two separate networks when I left...  One for the dorms, and one for the labs...

---

### Post by Scheater5 on 2007-10-12
Ok, so if the University is blocking port 22, are they blocking it outgoing as well?  Or would I still have to get SSH to listen on a different port even if the desktop was not on the University network?

---

### Post by bcl1713 on 2007-10-12
I doubt they are blocking the ssh port outbound..  try this "ssh www.ubuntu.com"  If you get a response... its not blocked.

---

### Post by Scheater5 on 2007-10-12
I did in fact get a response - the test will be when I try from my dorm and see if I can get a response from there as well.  If that works I may just set up a server at home as opposed to in my dorm.

---

### Post by bcl1713 on 2007-10-12
good luck to you.

---

### Post by p_quarles on 2007-10-12
Outbound SSH traffic doesn't use port 22. On my machine, it uses a random high port. They could potentially be blocking any connections with a *destination* port of 22, but I don't see why they would. All of the universities I've worked with have telnet/ssh accounts from which students can access their e-mail (Pine) or set up personal web pages. Even if this one doesn't, though, it would be bizarre if they blocked the destination ports.

---

### Post by rscott5 on 2007-10-12
Setting up SSH on your computer at home would be much easier. I have an apartment off campus and I SSH, FTP, and even VNC into it when I am in class or somewhere on campus and need something. What I did was set up a dyndns.org account so that I don't have to get a static IP from my ISP in my apartment. That way, every couple hours or so, my Ubuntu machine pings dyndns.org telling them what my IP is. Then I just ssh to [email]user@myaccount.dyndns.org[/email] instead of having to deal with getting a static IP from the ISP. Also, make sure you forward port 22 on your router at home. You shouldn't have a problem SSH-ing out from campus to your home, they usually don't block traffic like that. Hope that helps!

---

