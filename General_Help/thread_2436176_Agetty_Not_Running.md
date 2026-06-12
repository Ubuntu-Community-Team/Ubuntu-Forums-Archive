---
title: "Agetty Not Running"
date: 2020-02-01
forum: General Help
---

### Post by toml_12953 on 2020-02-01
I have Ubuntu 19.10 installed on a PC and did the following steps to get agetty running on my six serial ports:

1. For each serial port (0 - 5) I made a copy of the template, replacing the digit after ttyS with the actual serial port number:
[COLOR=#000000][FONT=Monaco]
  cp /usr/lib/systemd/system/serial-getty@.service /etc/systemd/system/serial-getty@ttyS0.service

2. I edited the agetty line in each copied file to match my uppercase-only terminals:
[/FONT][/COLOR]ExecStart=-/sbin/agetty -L -U ttyS0 9600,1200,110

3. I created symlinks to each edited file:

ln -s /etc/systemd/system/serial-getty@ttyS0.service /etc/systemd/system/getty.target.wants/

4. For each serial port, I started the service:

systemctl daemon-reload
systemctl start [email]serial-getty@ttyS0.servic[/email]e
systemctl enable [email]serial-getty@ttyS0.servic[/email]e

5. I looked at the running processes to make sure everything was working:

ps -aux | grep agetty

All six ports had agetty running on them with my changed parameters. Perfect!

I shut down the machine for the night. Then when I booted up again, I used the ps command again to make sure everything was still OK.
None of my agettys were running! Well, OK. I'll just start them manually.

I did this again:

systemctl daemon-reload
systemctl start [email]serial-getty@ttyS0.servic[/email]e

Oh oh. After I hit enter on the second command, the terminal prompt didn't come back. I hit Ctrl-C and the prompt came back.
I typed

systemctl enable [email]serial-getty@ttyS0.servic[/email]e

The prompt reappeared but a ps showed no agettys running. I can't start agettys on my serial terminals anymore.

Is there a new procedure for 19.10? Why did this work right after I followed the procedure the first time but not after a restart?

Tom L

---

