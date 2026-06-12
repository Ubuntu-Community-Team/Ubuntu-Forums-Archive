---
title: "[Self-hosted?] TeamViewer alternative?"
date: 2020-11-07
forum: General Help
---

### Post by uc50_ic4more on 2020-11-07
Twice  in the last few months I have had TeamViewer sessions terminated after a  warning that (something to the effect of) "commercial use has been  detected" when using Teamviewer. Their free-tier service has been  exactly what I need to support some friends, family and neighbours'  Ubuntu installations but having a session crap out after this  "commercial use" warning is unacceptable.

I'd  prefer to use a solution that does not require my friends, family and  neighbours' routers to be messed with as some are too far away from me,  else I'd use the standard desktop sharing VNC.

I'd  be happy to use a free-tier Google Cloud Platform virtual machine to  broker connections in place of TeamViewer's server but am not familiar  with what solutions are out there. I would appreciate suggestions.
Thanks!

---

### Post by TheFu on 2020-11-07
You can setup a nebula VPN and have them join it. Then you can connect to whatever their desktop remote desktop tool provides. You'll need to setup a public Nebula primary node which does have open ports on the internet, but none of the clients needs to do any more.
[LIST]
[*][https://arstechnica.com/gadgets/2019/12/how-to-set-up-your-own-nebula-mesh-vpn-step-by-step/](https://arstechnica.com/gadgets/2019/12/how-to-set-up-your-own-nebula-mesh-vpn-step-by-step/)
[/LIST]

You may be able to use a reverse ssh connection too.  That would be how I did it.  I supported my Mom over ssh for years, before she died, but it wasn't a reverse ssh. 
[LIST]
[*][https://www.howtogeek.com/428413/what-is-reverse-ssh-tunneling-and-how-to-use-it/](https://www.howtogeek.com/428413/what-is-reverse-ssh-tunneling-and-how-to-use-it/)
[*][https://www.howtoforge.com/reverse-ssh-tunneling](https://www.howtoforge.com/reverse-ssh-tunneling)
[/LIST]
ssh is text. 99% of the time, I used the text ssh interface. Only 1% of the time did I use an x2go connection into a GUI on her system. Once the ssh tunnel is up and working, you can use VNC or RDP safely through that tunnel to connect, if you prefer those methods. I've always found x2go to be 2-3x faster however.

Another option is wireguard VPN. Again, you'd need to setup a public wireguard VPN server (just 1 port open), but then connections on that VPN LAN are all like local LAN connections. For linux-to-linux, wireguard is pretty fast. It is new, but considered almost production.
[LIST]
[*][https://arstechnica.com/gadgets/2018/08/wireguard-vpn-review-fast-connections-amaze-but-windows-support-needs-to-happen/](https://arstechnica.com/gadgets/2018/08/wireguard-vpn-review-fast-connections-amaze-but-windows-support-needs-to-happen/)
[*][https://wiki.debian.org/WireGuard?action=show&redirect=Wireguard](https://wiki.debian.org/WireGuard?action=show&redirect=Wireguard)
[*][https://github.com/angristan/wireguard-install](https://github.com/angristan/wireguard-install)
[/LIST]

Depending on network performance, these can be fairly fast or terribly slow. Just depends.

None of these are point-n-click setups for your side.  

One more idea ... if your friends and neighbors just want someone to watch them as they do maintenance, then you could use the built-in screen sharing from any of the video conferencing tools available now.  My LUG meets weekly and we will share either a window or an entire desktop to show how to do something with the entire group. There's no "hand-off" of the mouse and keyboard, just view-only access.  We use jitsi meet - [https://meet.jit.si/](https://meet.jit.si/) - it requires a browser that supports javascript and webRTC, which is almost all of the browsers available today. No sign up. $0.  You can run your own instance if you like or use that URL and a random trailing location. Meetings can have passwords.  Android is supported as are POTS telephones for someone with only voice connectivity. It is good to avoid international calling rates.

Anyways, those are some options.

---

### Post by uc50_ic4more on 2020-11-07
Thank you, TheFu, for the suggestions: I am leaning towards reverse ssh tunnelling. I have to routinely guide elderly parents and neighbours through some tasks (sometimes repetitively!) but can perform updates and other maintenance via a conventional secure shell. Thanks!

---

### Post by TheFu on 2020-11-07
> **uc50_ic4more said:**
> Thank you, TheFu, for the suggestions: I am leaning towards reverse ssh tunnelling. I have to routinely guide elderly parents and neighbours through some tasks (sometimes repetitively!) but can perform updates and other maintenance via a conventional secure shell. Thanks!

There are some other options, I'm certain. Perhaps give some of the smart people here some hours to make suggestions.  

I have a bias against trusting any 3rd parties, especially google and the other big 20 tech companies in tracking our packets.

---

### Post by ActionParsnip on 2020-11-08
Do you have port 22 opened already so that you can manage their updates (I do this). If so then you can SSH tunnel (for security) then use VNC

---

### Post by dhavalbbhatt2 on 2020-11-08
AnyDesk is a great alternative to TeamViewer.

---

### Post by mastablasta on 2020-11-08
is reverse SSH like having SSH with option that local user can confirm connection? or they initiate it and you connect via that connection?

i think some of these chat apps like MS teams, Skype etc. offer desktop sharing and you can take over the mouse control if you need to show them something in GUI. i just use that to help my colleagues now that we work from home. i can only help them, if it doesn't requires admin password. and most of their issues don't.

---

### Post by ActionParsnip on 2020-11-08
> **mastablasta said:**
> is reverse SSH like having SSH with option that local user can confirm connection? or they initiate it and you connect via that connection?

i think some of these chat apps like MS teams, Skype etc. offer desktop sharing and you can take over the mouse control if you need to show them something in GUI. i just use that to help my colleagues now that we work from home. i can only help them, if it doesn't requires admin password. and most of their issues don't.

The SSH connection is made without the user using the system being connected to knowing. There may be VNC server side settings that need approval but once you are on the system you already have the system by the balls. Obviously use SSH keys and configure the system to only listen to VNC connections from localhost.

---

