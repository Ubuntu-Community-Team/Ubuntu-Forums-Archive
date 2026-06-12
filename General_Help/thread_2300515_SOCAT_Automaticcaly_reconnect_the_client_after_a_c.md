---
title: "SOCAT: Automaticcaly reconnect the client after a close and restart of the server"
date: 2015-10-26
forum: General Help
---

### Post by alice9 on 2015-10-26
Hi,

I'm using socat to send data from a serial port to a distant server.
The command I use is "socat  pty,link=/dev/ttyS0,raw  tcp:[IP]:8887".
My problem is that I need to be able to close and restart the server without having to re-send the socat command.
I put the socat command in a while loop to reconnect it automatically but socat does'nt exit when the server is closed, but when the application containing the server exits. 

I've tried almost all parameters of socat, I'm running out of ideas.

Do you have any idea ?
Sorry for my bad english :)
Thanks.

---

