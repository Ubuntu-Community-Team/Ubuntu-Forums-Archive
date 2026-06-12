---
title: "Run supervisor on startup"
date: 2016-08-31
forum: General Help
---

### Post by j.crater on 2016-08-31
Greetings all,
I am very new to Ubuntu and Unix in general. I am currently working with a Ubuntu system with very few components installed. 
My attempt is to make supervisord process manager to run on system startup. The system, for example, starts a postgres process with a file in: /etc/init.d/S40postgresql, the contents of this file are:
mkdir /run/postgresql
chown postgres:postgres /run/postgresql
su - postgres -c "pg_ctl start -D /var/lib/postgres/data/"
alias v="sournce /python_dev/venv_pythondev/bin/activate"

How can I create a script in the similar way that will run supervisor on startup? Manually I run supervisor in command line with:
supervisord -c /path/to/configfile

The system version is: 2016.02

Thank you for your help in advance,
best regards 
Josh C

---

### Post by oldos2er on 2016-08-31
Please tell us which Ubuntu version you're running; I don't know offhand what "system version is: 2016.02" means.

---

### Post by j.crater on 2016-09-01
With *uname -a* I get:
Linux version 4.1.13-g8dc6617  (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-12ubuntu1)

*lsb_release -a *command is not found, so with my knowledge this is all information I can provide ATM. I hope it can be of use.

---

### Post by ian-weisser on 2016-09-02
Linux already has a supervisor process. It's called 'init', and it has already has tools to start, stop, and monitor child processes.
What do you want your supervisor process to do?
There are several flavors of init - sysvinit, Upstart, and systemd. We need to know which you are using to help you better. Each is very different.

---

### Post by j.crater on 2016-09-19
Ubuntu system runs on an embedded device, and it uses [this supervisor]("http://supervisord.org/").
I would like supervisord process to start automatically on system startup. Now I have to start it manually via command line in the following way:
# supervisord -c /path/to/config

---

### Post by ian-weisser on 2016-09-19
A system version of '2016.02' is nonsense. But let's assume you meant 16.04, the most recent release of Ubuntu.

One easy way in 16.04 is to create a systemd .service file (examples are in /lib/systemd/system ) so systemd knows how to start your supervisor.
Then place a link to that service file within /etc/systemd/system/multi-user.target.wants/

Systemd will automatically trigger the service in order to achieve it's multi-user system.
You can choose a different target within /etc/systemd/system. Avoid early-startup targets before the filesystem and network are up.

There is a great  deal of [systemd documentation]("https://wiki.ubuntu.com/systemd") available to help you.

Are you really running as root? Rather unwise.

---

