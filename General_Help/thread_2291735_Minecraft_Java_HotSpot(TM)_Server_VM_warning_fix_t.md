---
title: "Minecraft Java HotSpot(TM) Server VM warning fix the library with 'execstack -c &lt;libf"
date: 2015-08-22
forum: General Help
---

### Post by rdcence on 2015-08-22
This error message does not seem to effect anything as far as I can tell.  The kids have not reported anything odd while playing but after searching and searching with no answers as well as upgrading Minecraft, Java and Ubuntu, I thought I'd post this and see if I can get a discussion going.[INDENT]
[09:27:20] [Server thread/INFO]: Starting minecraft server version 1.8.8
[09:27:20] [Server thread/INFO]: Loading properties
[09:27:20] [Server thread/INFO]: Default game type: SURVIVAL
[09:27:20] [Server thread/INFO]: Generating keypair
[09:27:20] [Server thread/INFO]: Starting Minecraft server on *:25565
Java HotSpot(TM) Server VM warning: You have loaded library /tmp/libnetty-transport-native-epoll8217695465706653945.so which might have disabled stack guard. The VM will try to fix the stack guard now.
It's highly recommended that you fix the library with 'execstack -c <libfile>', or link it with '-z noexecstack'.
[09:27:20] [Server thread/INFO]: Using default channel type
[09:27:21] [Server thread/INFO]: Preparing level "world"
[09:27:21] [Server thread/INFO]: Preparing start region for level 0
[09:27:22] [Server thread/INFO]: Preparing spawn area: 4%
[09:27:23] [Server thread/INFO]: Preparing spawn area: 55%
[09:27:24] [Server thread/INFO]: Preparing spawn area: 96%
[09:27:24] [Server thread/INFO]: Done (3.300s)! For help, type "help" or "?"

[/INDENT]

---

### Post by wog on 2015-09-26
I've noticed it, too, when I start my Minecraft server. No idea what stack guard is or what it does. I'm not sure what I'm supposed to feed the command line in place of <libfile>, unless it's that .so file it mentions when it starts. It does say it attempts to fix stack guard and I assume it succeeds, but if so, why does it kick out this error message every time I start the server?

I notice here that your file is /tmp/libnetty-transport-native-epoll8217695465706653945.so, whereas mine is called
/tmp/libnetty-transport-native-epoll4857114076190409304.so -- not sure if that makes any difference at all.

Have you learned anything more since you first posted this?

---

