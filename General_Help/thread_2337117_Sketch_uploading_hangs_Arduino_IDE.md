---
title: "Sketch uploading hangs Arduino IDE"
date: 2016-09-14
forum: General Help
---

### Post by mune on 2016-09-14
I use Ubuntu 16.04 Desktop.

I'm doing a little project with the Arduino One using the Arduino IDE.  Until two days ago everything have been fine. Suddenly, without any relevant reason, when I upload the sketch the IDE freeze and after a (long) while it says that after 10 times it can't connect to the board.

I tried with the standard example "Blink", to be safe that was not due to my sketch that the IDE wasn't connecting.
I tried with a spare Arduino board with some result.

I have also a Intel NUC that I use as server. It sports Ubuntu 16.04 Server
The server is headless so I connected using ssh.
With APT I installed arduino, which installed java + avr-libc + whetever_needed.
I added the current nuc's user to the group dialout and exited.
I logged in again with ssh -X user@nuc
I used the Arduino IDE on the nuc and it was fine.

I thought it might be the fresh installation, so I, in the main box, purged arduino, avr*, removed the folder .arduino , then installed arduino again via apt but nothing has changed.

As the USB ports work, my conclusion is that it is due to a misconfiguration; but what is configured in bad way?

Help me to find what is that bother the Arduino IDE: thanks

---

### Post by mune on 2016-09-16
Does something need to more clear?

---

