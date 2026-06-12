---
title: "how to run a command when reboot &amp; shutdown"
date: 2018-09-16
forum: General Help
---

### Post by rasitha2 on 2018-09-16
[COLOR=#333333][FONT=&quot]hi[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]hope this is the right place to post this question[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]i need to kill the process motion every time i reboot & shutdown the pc[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]can i use the command [/FONT][/COLOR]

**sudo killall -9 motion**

[COLOR=#333333][FONT=&quot]& how can i run this command when i reboot & shutdown the pc[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]why i need to do this is everytime i reboot the motion precess takes 5 mins to end[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]im starting motion with this command [/FONT][/COLOR]**sudo motion**[COLOR=#333333][FONT=&quot] manually[/FONT][/COLOR]

---

### Post by TheFu on 2018-09-16
Perhaps setting up a systemd init/stop script would be better?  There are lots of examples under /etc/systemd/system/

And example from sshd
$ more sshd.service 
```
[Unit]
Description=OpenBSD Secure Shell server
After=network.target auditd.service
ConditionPathExists=!/etc/ssh/sshd_not_to_be_run

[Service]
EnvironmentFile=-/etc/default/ssh
ExecStart=/usr/sbin/sshd -D $SSHD_OPTS
ExecReload=/bin/kill -HUP $MAINPID
KillMode=process
Restart=on-failure
RestartPreventExitStatus=255
Type=notify

[Install]
WantedBy=multi-user.target
Alias=sshd.service
```
This assumes you are running Ubuntu 16.04 or later.

---

### Post by rasitha2 on 2018-09-19
solved .. this is how

[COLOR=#2E8B57][FONT=monospace]sudo touch /etc/systemd/system/motionkill.service

[/FONT][/COLOR][COLOR=#2E8B57][FONT=monospace]xed admin:///etc/systemd/system/motionkill.service

[/FONT][/COLOR][Unit]
Description=Kill motion
DefaultDependencies=no
Before=shutdown.target reboot.target halt.target


[Service]
Type=oneshot
ExecStart=/usr/bin/killall -9 motion


[Install]
WantedBy=halt.target reboot.target shutdown.target
[COLOR=#2E8B57][FONT=monospace]
sudo systemctl enable motionkill[/FONT][/COLOR][COLOR=#2E8B57][FONT=monospace]

[/FONT][/COLOR][COLOR=#2E8B57][FONT=monospace]
[/FONT][/COLOR]

---

### Post by TheFu on 2018-09-19
```
sudoedit  /etc/systemd/system/motionkill.service
```
is a safer way to create/edit system files, but whatever works is fine.

If you like xed just set that as your EDITOR environment variable and it will be used.

---

