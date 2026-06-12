---
title: "Cross Platform RMM"
date: 2013-10-09
forum: General Help
---

### Post by jackson-eyton on 2013-10-09
Hi guys,
    I was really hoping someone could point me in the right direction. I am looking for a free open source rmm remote access type platform or application to manage windows and linux/unix based machines remotely. I can develop some of this but would like to not reinvent the wheel as much as possible. My current thought is to utilize vnc and ssh, however this would need to be something that I can have the remote user simply install on their machine and then that "agent" will start reporting in to my server. I was considering using cygwin for windows ssh access, though I do not know how to get this to check into my server. I would need to commands to delivered to the remote agent as responses to its connection so as to utilize NAT and skip configuring the remote firewall as much as possible. The other component I would need is direct visual access, likely with VNC. With ssh access I think I should be able to connect a vnc session without the user having to do anything (would have to look up those commands cant recall off the top of my head), the second method would be that I'd need a VNC hub thats web accessible so I can direct clients to the website and have them click a link that downloads a prepackaged VNC and connects them to me. If anyone has any resources on how to setup any of this it would be greatly appreciated. I am completely open to other ideas as well. Thanks!

P.S.
I have tried both spiceworks and Zenoss but these did not seem to fill my needs.

---

