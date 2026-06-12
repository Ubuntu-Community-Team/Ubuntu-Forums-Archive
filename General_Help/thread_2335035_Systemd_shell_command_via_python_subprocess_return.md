---
title: "Systemd shell command via python subprocess returns non-zero exit status 127"
date: 2016-08-24
forum: General Help
---

### Post by bluedragon1460 on 2016-08-24
I have a celery worker that isn't able to execute subprocess commands when it's being ran inside of a Systemd service.
[SIZE=2]
[/SIZE]```

[SIZE=2][Unit][/SIZE]
[SIZE=2]Description=Celery instance to serve worker[/SIZE]
[SIZE=2]After=network.target[/SIZE]

[SIZE=2][Service][/SIZE]
[SIZE=2]User=root[/SIZE]
[SIZE=2]WorkingDirectory=/home/worker/worker[/SIZE]
[SIZE=2]Environment="C_FORCE_ROOT=yes"[/SIZE]
[SIZE=2]Environment="PATH=/home/worker/venv/bin"[/SIZE]
[SIZE=2]ExecStart=/home/worker/venv/bin/celery -A tasks worker --logfile=/var/log/worker.log[/SIZE]

[SIZE=2][Install][/SIZE]
[SIZE=2]WantedBy=multi-user.target[/SIZE]
[SIZE=2]Example Subprocess call[/SIZE]

```[SIZE=2]

[/SIZE]```

[SIZE=2]c = 'sudo cp /home/somefile /somewherelse/somefile'[/SIZE]
[SIZE=2]result = subprocess.call(c, shell=True)[/SIZE]

```[SIZE=2]

[/SIZE][COLOR=#242729][FONT=Arial][SIZE=2]The celery worker is able to pickup jobs fine. The only problem is when I try executing shell commands via Python's subprocess package. Any of the subprocess commands return either non-zero exit, or [Errno 2] No such file or directory.[/SIZE]
[/FONT][/COLOR]

---

### Post by papibe on 2016-08-24
Hi bluedragon1460.

I'm not familiar with celery, but that python code will only work if it is executed from a terminal.

If the process is trigger, from another source, like running it with a Alt+F2 command, it won't work because 'sudo' is an interactive command that needs a tty (terminal) **.

I can think of a couple of solution:
[LIST]
[*]don't use sudo in your script. Run the script as the user that has the proper permissions to run the code (root maybe?), or
[*]run the script inside GNU screen, or a tmux session. This does not solve the problem of requiering to enter the password, but at least there would be a way to get to it.
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

P.S.: ** you should be able to see the sudo/pam errors by running:
```
tail /var/log/auth.log
```

---

### Post by ian-weisser on 2016-08-24
That systemd job seems to run [COLOR=#000000][FONT=&amp]/home/worker/venv/bin/celery [/FONT][/COLOR]as root.
Any subprocess does not need to use sudo...it's already root.

---

