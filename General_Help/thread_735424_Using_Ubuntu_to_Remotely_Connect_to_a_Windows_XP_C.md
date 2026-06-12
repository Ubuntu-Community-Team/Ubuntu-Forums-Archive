---
title: "Using Ubuntu to Remotely Connect to a Windows XP Computer"
date: 2008-03-25
forum: General Help
---

### Post by xVehemencityx on 2008-03-25
Hi.  This is kinda random, but my friend is having issues with her Windoze XP computer, and seeing as I can't go to her house to fix it (her parents are crazy), is there any way I can remote connect to her pc just using her IP address so I can fix it?

---

### Post by PinkFloyd102489 on 2008-03-25
You could try VNC. RealVNC is easy to install and to connect, you just type "vncviewer" in the terminal and input their IP address.

---

### Post by xVehemencityx on 2008-03-25
Okay, I just tested that on my home network to see if it would work.  I typed in my ip address : ##.###.##.###:Port  And it said 

```
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
alex@alex-desktop:~$ 

```

Does that mean there's something I need to have changed on the Windoze PC?

---

### Post by sillyxone on 2008-03-25
I did it first time last week on one of my lab machine. On the XP machine, enable Remote Assitance by rightclicking on My Computer, select Properties -> Remote Assistance. On Ubuntu machine, go to menu -> Internet -> Terminal Server Client, type in the XP machine's IP, choose RDP and there you go.

---

### Post by xVehemencityx on 2008-03-25
> **sillyxone said:**
> I did it first time last week on one of my lab machine. On the XP machine, enable Remote Assitance by rightcling on My Computer, select Properties -> Remote Assistance. On Ubuntu machine, go to menu -> Internet -> Terminal Server Client, type in the XP machine's IP, choose RDP and there you go.


Okay, where do I type in the IP?  I know I probably sound like an idiot, but there's so many places to type stuff in.  What do I put for Computer, Username, Password, Domain, Client Hostname, or Protocol File?

---

### Post by HermanAB on 2008-03-25
Enable remote desktop in Windoze forward port 3389/tcp in the router to the Windoze desktop then install rdesktop from synaptic on Ubuntu and do:
$ rdesktop -g 90% ip.add.re.ss

BTW, for RDP to work, the Windows user MUST have a password.

Cheers,

Herman

---

### Post by xVehemencityx on 2008-03-25
Also, there is no Remote Assistance option under My Computer > Properties.

---

### Post by xVehemencityx on 2008-03-25
Okay, I think I know why I can't connect to my brother's computer.  His XP isn't activated.  The serial on our CD case doesn't work, so it's just not activated.  Maybe that's why.  Is there any chance someone would let me try it with their computer?  Haha, I doubt it, but if you do, I promise I won't delete or move anything, haha.

---

### Post by sillyxone on 2008-03-25
> **xVehemencityx said:**
> Okay, where do I type in the IP?  I know I probably sound like an idiot, but there's so many places to type stuff in.  What do I put for Computer, Username, Password, Domain, Client Hostname, or Protocol File?

Computer: ip address
Protocol: RDP
username: administrator, or leave blank
password: leave blank
domain: leave blank
client hostname: leave blank

Sorry, I didn't have an XP machine to look at, so enabling XP remote assitance again:

-right-click My Computer, choose Properties.
- in the opened System Properties panel, select Remote tab
- in the Remote Desktop section, check the box "Allow user to connect remotely to this computer"

---

### Post by xVehemencityx on 2008-03-25
> **sillyxone said:**
> Computer: ip address
Protocol: RDP
username: administrator, or leave blank
password: leave blank
domain: leave blank
client hostname: leave blank

Sorry, I didn't have an XP machine to look at, so enabling XP remote assitance again:

-right-click My Computer, choose Properties.
- in the opened System Properties panel, select Remote tab
- in the Remote Desktop section, check the box "Allow user to connect remotely to this computer"


Okay, well, that's not an option, so I'm guessing it's just because my brother's Windoze isn't activated.

---

### Post by xVehemencityx on 2008-03-25
Oh, and what do you do for port?

---

### Post by xVehemencityx on 2008-03-25
Oh, lord, I hate bumping, but no one's answering me, and it's kinda important.

---

### Post by sillyxone on 2008-03-25
it could be that option is only available in Professional version, not Home version. So your friend will have to do the extra step of downloading VNC Server and install it on her computer.

---

### Post by xVehemencityx on 2008-03-25
> **sillyxone said:**
> it could be that option is only available in Professional version, not Home version. So your friend will have to do the extra step of downloading VNC Server and install it on her computer.

Umm, okay, once she installs it, is there anything she needs to configure?

---

