---
title: "gAIM file transfer/direct connect"
date: 2005-06-18
forum: General Help
---

### Post by xbilly on 2005-06-18
File transfer and Direct Conections do not work in My GAIM. 
Me establishing Direct Connection with buddy: 

Asking ***** to connect to us at 192.168.0.100:5190 for Direct IM.
(19:30:17) Attempting to connect to ***** at 68.228.21.53:4443 for Direct IM.

(Then nothing beyond this point)

Trying to establish Direct Connection with me:
Attempting to connect to ***** at 68.228.21.53:4443 for Direct IM.

(Then nothing beyond this point)

Trying to send a file: Offering to send /home/billy/Desktop/RvB_Episode06_LoRes.avi to *****

(Then nothing beyond this point)

Trying to send me a file:
I get the TRANSFER dialog box, but the file doesn'tgo beyond "Waiting for transfer to begin"

PLEASE help

---

### Post by sethmahoney on 2005-06-18
They've never worked for me, either.

---

### Post by Prog on 2005-06-18
Never worked for me either; I'm hoping someone has a solution. T_T

---

### Post by xbilly on 2005-06-18
Hmmm. I know AOL has their version of AIM for Linux. Does anyone know if that one works well?

---

### Post by Prog on 2005-06-18
I tried it about a year ago and it was very feature light.  I don't remember if DC worked, though.

Also, they don't release new versions of that very often (or at all, for all I know), so it's probably still the same version out.

---

### Post by byen on 2005-06-18
lol...I tried getting a file an hour ago and it did not work for me either...so guess its not me!!

---

### Post by skoal on 2005-06-18
What version are you using? Once I updated to v1.3 and...and...and...(did I say and?)...and...opened up some ports on my router, Direct connect worked again.  I was behind a firewall and didn't even know it, so I put myself up in the DMZ.  In direct connect, when I send pictures it freezes up all the gAIM windows for a spell, then...poof!...comes back in 5 seconds or so.  I've learned to live with it...

\\//_

---

### Post by eyequeue on 2005-06-18
Someone who knows more about gaim should be able to help more, but:

[QUOTE=xbilly]File transfer and Direct Conections do not work in My GAIM. 
Me establishing Direct Connection with buddy: 

Asking ***** to connect to us at 192.168.0.100:5190 for Direct IM.
(19:30:17) Attempting to connect to ***** at 68.228.21.53:4443 for Direct IM.

(Then nothing beyond this point)
[/quote]

The problem appears to be that you are telling the other end that your IP address is "192.168.0.100" (and to use port 5190.) 192.168.x.x is considered unroutable, (see RFC 1918 for further on this) and therefore none of the Internet Service Providers between you and your friend should allow routing to such an address. It's only of use on your LAN.

What happens is that gaim probably looks at the interface address (such as you would see in the output of 'ifconfig') to determine what IP address to send. The address that you'd want to be sending is the address of your firewall/router/whatever machine. I presume you are on a LAN behind some other Internet-facing hardware, right? It's that other hardware whose IP address is the "routable" one.

How do you get gaim to use that "external" IP address?  Unfortunately, I don't know that, but perhaps someone will come along that does.

---

### Post by keybreckaba on 2005-06-18
[QUOTE=xbilly]File transfer and Direct Conections do not work in My GAIM. 
Me establishing Direct Connection with buddy: 

Asking ***** to connect to us at 192.168.0.100:5190 for Direct IM.
(19:30:17) Attempting to connect to ***** at 68.228.21.53:4443 for Direct IM.

(Then nothing beyond this point)

Trying to establish Direct Connection with me:
Attempting to connect to ***** at 68.228.21.53:4443 for Direct IM.

(Then nothing beyond this point)

Trying to send a file: Offering to send /home/billy/Desktop/RvB_Episode06_LoRes.avi to *****

(Then nothing beyond this point)

Trying to send me a file:
I get the TRANSFER dialog box, but the file doesn'tgo beyond "Waiting for transfer to begin"

PLEASE help[/QUOTE]
 if i remember correctly on gaims website it says that file trasfer and DC on aim are not supported if you are behind a router or firewall

---

### Post by mofknjosh on 2005-07-18
I logged into my rounter and forwarded port 5190 to my local ip address. That seemed to solve the problem.

---

### Post by ducttapeandzipties on 2007-03-10
I'm running gaim 2.0.0beta3.1 on Ubuntu 6.10 behind a linksys wrt54g router.  I've been having the same kind of problems.  I just forwarded port 5190 to my local IP and d/c is working fine now :grin:

---

### Post by kaede on 2007-04-26
can you guide me how to do this?

how can we assign forwarded port to my local IP if we're using dhcp ?

---

