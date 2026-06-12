---
title: "Why can't connect with ssh or ping my VPS?"
date: 2019-07-14
forum: General Help
---

### Post by surzo18 on 2019-07-14
[COLOR=#242729][FONT=Arial]I need help. I don't know why i can't connect (with ssh) or ping my VPS. Iptables looks good i have ssh on 2080 and it is running. But i am still getting message: [/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I also tried restart ssh but nothing works. Until yesterday everything was ok and i didn't change anything on server.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][[IMG]https://i.stack.imgur.com/Ry3UQ.png[/IMG]]("https://i.stack.imgur.com/Ry3UQ.png")[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What should i do? I still can connect to my server with VNC. I also can't do apt-get update it show me some warning (failed to fetch from contabo... and SOME index files failed to download)

[/FONT][/COLOR]

---

### Post by TheFu on 2019-07-14
> **surzo18 said:**
> [COLOR=#242729][FONT=Arial]I need help. I don't know why i can't connect (with ssh) or ping my VPS. Iptables looks good i have ssh on 2080 and it is running. But i am still getting message: [/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I also tried restart ssh but nothing works. Until yesterday everything was ok and i didn't change anything on server.[/FONT][/COLOR] 
[COLOR=#242729][FONT=Arial]What should i do? I still can connect to my server with VNC. I also can't do apt-get update it show me some warning (failed to fetch from contabo... and SOME index files failed to download)

[/FONT][/COLOR]

You've made a few statements without providing proof.  Please proove those statements.
* ssh is on
* ssh is using port 2080/tcp
* VNC is working, which makes me think you've been hacked, hacked, hacked.

VNC should never be enabled that works outside the localhost, thus forcing a secured network connection be used to access it. There is an option on vncserver to only allow localhost connections.
If you've been hacked, wipe the system completely and start over using more secure setup.

Check the log files for issues.  

BTW, please avoid posting images when it isn't needed. Text is tiny in comparison.

My ssh troubleshooter: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

---

