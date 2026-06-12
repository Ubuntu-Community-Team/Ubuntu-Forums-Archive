---
title: "Shutdown Problems"
date: 2013-03-16
forum: General Help
---

### Post by Corky98 on 2013-03-16
When I press shutdown it goes to this screen:
mountall: Disconnected from Plymouth
                                                            acpid : exiting
[1078.933492] INFO: task Xorg :1128 blocked for more than 120 seconds.
[1078.933628] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[1078.933492] INFO: task Xorg :1128 blocked for more than 120 seconds.
[1078.933628] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[1078.933492] INFO: task Xorg :1128 blocked for more than 120 seconds.
[1078.933628] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.

and hasn't turned off 10 minutes later
running 12.10 with cinnamon DE, AMD HD3000 graphics, /home partition on different drive and conky setup
any ideas?

---

### Post by matt_symes on 2013-03-17
Hi

What happens if you try to shut down from a terminal ?

```
sudo shutdown -h now
```

I expect that may still hang.

The message mentions xorg as the hung task. Can you stop x from a console.

Press Crtl + alt + f1 at the same time to get to a console.

Type in your username and password to login.

type (I assume your using lightdm)

```
sudo service lightdm stop
```

Does that hang ?

If not, type 

```
sudo shutdown -h now
```

Does that hang ?

I would also suggest looking in the log files.

Specifically /var/log/syslog and /var/log/xorg.0.log and older versions of those same logs (they usually end in .1 etc)

Kind regards

---

### Post by unitedoceanic on 2013-03-30
well i just jump in, i have the same problem!

running 12.10 64bit lenovo b570 laptop

i use unity not cinamon

system shuts down correctly with:
```
sudo shutdown -h now
```
kernel log:

```
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200925] ptrace of pid 2325 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200929] ptrace of pid 2327 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200931] ptrace of pid 2329 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200933] ptrace of pid 2330 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200934] ptrace of pid 2340 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200936] ptrace of pid 2341 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200937] ptrace of pid 2342 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200939] ptrace of pid 2343 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200941] ptrace of pid 2344 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200942] ptrace of pid 2345 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:51 Red-Queen kernel: Kernel logging (proc) stopped.
```

sys log:

```
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200925] ptrace of pid 2325 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200929] ptrace of pid 2327 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200931] ptrace of pid 2329 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200933] ptrace of pid 2330 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200934] ptrace of pid 2340 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200936] ptrace of pid 2341 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200937] ptrace of pid 2342 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200939] ptrace of pid 2343 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200941] ptrace of pid 2344 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:50 Red-Queen kernel: [ 1135.200942] ptrace of pid 2345 was attempted by: PeerInterface (pid 2658)
Mar 30 16:03:51 Red-Queen gnome-session[1402]: CRITICAL: gsm_manager_set_phase: assertion `GSM_IS_MANAGER (manager)' failed
Mar 30 16:03:51 Red-Queen gnome-session[1402]: Gtk-CRITICAL: gtk_main_quit: assertion `main_loops != NULL' failed
Mar 30 16:03:51 Red-Queen kernel: Kernel logging (proc) stopped.
Mar 30 16:03:52 Red-Queen rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="897" x-info="http://www.rsyslog.com"] exiting on signal 15.
```

xorg log show nothing interesting,

any help appreciated

---

### Post by matt_symes on 2013-03-30
Hi

@[**[COLOR=#000000]unitedoceanic[/COLOR]**]("http://ubuntuforums.org/member.php?u=958253").

Can you shutdown from the terminal as per post #2.

Can you shutdown after stopping lightdm as per post #2.

Those ptrace log entries are interesting. Can you post back the process that is associated with those PID's. They will be different PIDS after a reboot.

Kind regards

---

### Post by unitedoceanic on 2013-03-30
hi thank you for your reply,

you were faster than my *ninja* edit =)

---

### Post by matt_symes on 2013-03-30
Hi

Shutdown works. That's good as it gives you an initial workaround.

Let's try to narrow this down then

Does this shutdown cleanly (copy and paste into the terminal).

```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```

I'll be back and forth from keyboard today and tomorrow i may not be about much either. A Friends birthday tonight (again) so it may be Monday before we have a real look at this.

Kind regards

---

### Post by unitedoceanic on 2013-03-31
Thank you again for your help!
i have this problem two weeks now no need to hurry especially on eastern :)

tried the command and my laptop shouts down just perfectly.

---

