---
title: "VNC vs SSH"
date: 2006-07-29
forum: General Help
---

### Post by ProjectGod on 2006-07-29
sorry for posting one thread after another! but i guess saturdays are days when there arent too many critisers ;)

sorry for the cheesy thread title... but i noticed how SLOW command line based SSH is compared to VNC. is this the norm? i'm testing out ssh on the LAN and its very very slow. i heard ssh can handle GUI too... if so would that be eXtra slow?

give a little feedback on your experiences with these remote tools. 

cheers.

---

### Post by CameronCalver on 2006-07-29
Hey are you the guy from the open office org thread lol
anyway isnt ssh like file sharing and vnc like remote desktop?

---

### Post by scxtt on 2006-07-29
ssh should be 'faster' than vnc - especially since ssh (command line) is just text as opposed to 'images' ... if you're getting slow response (i've had it happen to me, not lately tho) it could be a result of the sshd not getting proper CPU time and/or there are a lot of background procs running ...

and you can get ssh to forward X apps ...
[indent]ssh -X $USER@$HOST[/indent]of course you'd have to have a session that can handle the forwarded apps ...

---

### Post by ProjectGod on 2006-07-29
the guy from the openoffice thread... yup that's me!

anyway since were on the topic... i was wondering... after i install ssh server...:

openssh-server

from another computer i just:

ssh user@host

to connect to that ssh-server using the server user's password... is there anything wrong with this? is there a security risk do i need to generate keys? or use some form of encryption for extra security? or is this safe enough? should be safer than telnet right?

i really don't feel like reading a long document just wondering if anyone could give me a quick wrap! so don't say RTFM!!!! :mrgreen:

cheers.

---

### Post by scxtt on 2006-07-29
you can connect as any valid $USER on $HOST when you do $USER@$HOST - so whatever password you'd use to login locally, you use w/ SSH ... you don't need to use dsa/rsa [ ssh-keygen -t {dsa/rsa} ], but you can ... i'm sure encryption isn't a bad idea, but i don't find it to be necessary ...

---

### Post by CameronCalver on 2006-07-29
can someone quicly answer my question
isnt vnc a remote desktop?
and ssh is grafical two Places--Connect to server then ssh

---

### Post by ProjectGod on 2006-07-29
thanks for your answer scxtt

as for CameronCalver, yes VNC is like the RDP connection tool in windows. you can use it to control / login / view remote computers... all graphical as though your siting on the machine. 

ssh is relatively new to me. but it can basically act like a VNC... with GUI capabilities... it closely resembles telnet... but much more secure... i like thinking of it as... the basic shell (sh) with secure infront of it. (ssh)... something you can use to admistrate remote hosts (servers) via the command line or gui,.

---

### Post by YorYor on 2006-07-29
> OpenSSH is a FREE version of the SSH connectivity tools that technical users of the Internet rely on. Users of telnet, rlogin, and ftp may not realize that their password is transmitted across the Internet unencrypted, but it is. OpenSSH encrypts all traffic (including passwords) to effectively eliminate eavesdropping, connection hijacking, and other attacks. Additionally, OpenSSH provides secure tunneling capabilities and several authentication methods, and supports all SSH protocol versions.

Check out [http://www.openssh.com/]("http://www.openssh.com/") for more information if you're concerned about security.

---

