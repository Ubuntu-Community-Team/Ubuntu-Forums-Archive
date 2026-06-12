---
title: "Ubuntu's default Firewall?"
date: 2006-10-22
forum: General Help
---

### Post by Dudeguythingman424 on 2006-10-22
Im using bittornado (or something) and im downloading things and it is going kinda slow because it says i have a firewall or something, i need to shut it off or something. Thanks for the help

---

### Post by wieman01 on 2006-10-23
Well... Ubuntu's firewall (IP Tables) is permissive by default, so that's not the cause. Having said that your router is a different story. You need to enable port forwarding there. 

First thing you need to do is find out about the ports that need to be opened. Use this page to do that:

[http://www.portforward.com/english/routers/port_forwarding/routerindex.htm]("http://www.portforward.com/english/routers/port_forwarding/routerindex.htm")

First check out the page for your router model, then search for "Bittornado".

A note: For portforwarding you need to have a "static IP leases", and not DHCP. If your PC's IP address keeps changing the router won't be able to forward traffic to your machine.

---

### Post by Malakia on 2006-10-23
Basically Ubuntu comes installed with no ports open, its only when you access the port that it opens. Like port 22 for ssh isn't open by default if you do a port scan it will come up stealth or closed.

---

### Post by siefkencp on 2006-10-27
Great answer now how do you open those ports... Or just ditch the damned firewall completely.... Spare me the lecture --

---

### Post by wieman01 on 2006-10-27
> **siefkencp said:**
> Great answer now how do you open those ports... Or just ditch the damned firewall completely.... Spare me the lecture --
?

Asking a question, but then asking us to spare you the lecture? 

I think that these ports will be open by default.

---

### Post by beerfan on 2006-10-27
> **Dudeguythingman424 said:**
> Im using bittornado (or something) and im downloading things and it is going kinda slow because it says i have a firewall or something, i need to shut it off or something. Thanks for the help

First, a firewall may exist outside of your computer. Do you have router connected to your modem? If so then it probably has it's own firewall. You may need to open the ports on it or see if it and your torrent client supports UPnP which can autonegotiate this for you. Azureus handles this well but I have no experience with bittornado.

---

### Post by siefkencp on 2006-10-27
Spare me the lecture about my security... and answer my question

You are terribly mistaken if you think there is an extra port open by default... Ubuntu is extremely restrictive... Go to your network tools do a port scan (not on your loop back) and see for yourself..

---

### Post by skymt on 2006-10-27
Firewall shouldn't be an issue unless you installed Firestarter or something like it. The Ubuntu firewall is permissive by default, as some above posts said.

Are you behind a router? If so, you need to forward some ports. I can't tell you exactly how, because it's different for each model of router, but generally you:

* Connect to your router using a web browser (often "192.168.1.1" or "192.168.0.1", check your router documentation)

* Enter a username and password (see your router docs for the defaults)

* Go to the port forwarding screen

* Tell it to forward appropriate ports (by default, Bittorrent/tornado uses 6881-6889)

---

### Post by skymt on 2006-10-27
> **siefkencp said:**
> Spare me the lecture about my security... and answer my question

You are terribly mistaken if you think there is an extra port open by default... Ubuntu is extremely restrictive... Go to your network tools do a port scan (not on your loop back) and see for yourself..

That's just because nothing's running on those ports by default. A port isn't "open" unless a program is using it.

---

### Post by siefkencp on 2006-10-27
> **beerfan said:**
> First, a firewall may exist outside of your computer. Do you have router connected to your modem? If so then it probably has it's own firewall. You may need to open the ports on it or see if it and your torrent client supports UPnP which can autonegotiate this for you. Azureus handles this well but I have no experience with bittornado.

I am my firewall administrator the 2 PC's I want to talk are on the same network, same subnet and are not applicable to any firewall except the one on the UBUNTU box... (The PC has it's firewall disabled)

---

### Post by skymt on 2006-10-27
> **siefkencp said:**
> I am my firewall administrator the 2 PC's I want to talk are on the same network, same subnet and are not applicable to any firewall except the one on the UBUNTU box... (The PC has it's firewall disabled)

If it's behind a NAT router, the router acts like a firewall. See my first post in this thread.

---

### Post by siefkencp on 2006-10-27
> **skymt said:**
> That's just because nothing's running on those ports by default. A port isn't "open" unless a program is using it.

Meaning I have to deal with inetd

---

### Post by siefkencp on 2006-10-27
> **skymt said:**
> If it's behind a NAT router, the router acts like a firewall. See my first post in this thread.

Which part of same subnet didn't you get? theres 1 hop between the boxes...

---

### Post by skymt on 2006-10-27
> **siefkencp said:**
> Meaning I have to deal with inetd

No, you don't. If you port scan *while Bittorrent is running*, and nothing comes up (in the 6880-6889 range by default), then you have a problem.

---

### Post by siefkencp on 2006-10-27
> **skymt said:**
> No, you don't. If you port scan *while Bittorrent is running*, and nothing comes up (in the 6880-6889 range by default), then you have a problem.

I just want open a port... (for samba) I'm not really interested in Bittorrent...

---

### Post by skymt on 2006-10-27
> **siefkencp said:**
> Which part of same subnet didn't you get? theres 1 hop between the boxes...

So you're using Bittorrent from one computer to another? Or does your question have nothing to do with the original post?

EDIT: I read your post. Samba is running, but you don't get any ports open? That's strange. Do you have Firestarter? Is Samba really running?

---

### Post by siefkencp on 2006-10-27
> **skymt said:**
> So you're using Bittorrent from one computer to another? Or does your question have nothing to do with the original post?

EDIT: I read your post. Samba is running, but you don't get any ports open? That's strange. Do you have Firestarter? Is Samba really running?

Yes sorry--- I've been asking the question about samba and MySQL for a WHILE now I just tagged along because the subject matches...

---

### Post by siefkencp on 2006-10-27
> **siefkencp said:**
> Yes sorry--- I've been asking the question about samba and MySQL for a WHILE now I just tagged along because the subject matches...

I am certain that MySQL and samba are running...

EDIT I dont have firestarter

---

### Post by skymt on 2006-10-27
> **siefkencp said:**
> I am certain that MySQL and samba are running...

EDIT I dont have firestarter

So, Samba shows up if you scan your loopback? I'm just eliminating that possibility before we move on, so please be patient.

---

### Post by siefkencp on 2006-10-27
> **skymt said:**
> So, Samba shows up if you scan your loopback? I'm just eliminating that possibility before we move on, so please be patient.

Yup [445] so does MySQL [3306]

---

### Post by skymt on 2006-10-27
Please post the output of:```
sudo iptables -L
```

---

### Post by wieman01 on 2006-10-27
> **siefkencp said:**
> You are terribly mistaken if you think there is an extra port open by default... Ubuntu is extremely restrictive... Go to your network tools do a port scan (not on your loop back) and see for yourself..
I don't think I am. My IP tables were permissive by default. That changed of course after I had installed Firestarter later on. But that's a different issue.

_**EDIT:**_
And that's not a lecture, but my own personal experience.

---

### Post by siefkencp on 2006-10-30
```
sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by siefkencp on 2006-10-30
> **wieman01 said:**
> I don't think I am. My IP tables were permissive by default. That changed of course after I had installed Firestarter later on. But that's a different issue.

Apparently inetd is being used? Ubuntu's documentation on it is a bit -- sparse

---

