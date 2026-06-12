---
title: "Can't keep Docker from starting at boot 16.04"
date: 2017-03-08
forum: General Help
---

### Post by gue22 on 2017-03-08
[COLOR=#445D6E][FONT=&amp]Tried all kinds of things
sudo systemctl disable docker says
Synchronizing state of docker.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install disable docker
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of scriptdocker' overrides LSB defaults (0 1 6).
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of scriptdocker' overrides LSB defaults (0 1 6).[/FONT][/COLOR]
[COLOR=#445D6E][FONT=&amp]
systemd-manager says disabled, but it isn't.

In sudo sysv-rc-conf Docker runlevels are unchecked[/FONT][/COLOR]
[COLOR=#445D6E][FONT=&amp]
Docker keeps starting at boot.
Thanks
G.[/FONT][/COLOR]

---

### Post by Frogs Hair on 2017-03-09
Docker as in KDE/Gnome system tray application ?

---

### Post by gue22 on 2017-03-09
> **Frogs Hair said:**
> Docker as in KDE/Gnome system tray application ?

Thanks! Nope, no KDE, no Gnome. What's the default? Unity?
Normal Docker service / daemon.
G.

---

### Post by Frogs Hair on 2017-03-09
If it's docker.io (Linux container runtime) , I don't use it and defer to to a user who does. ;)

---

### Post by #&amp;thj^% on 2017-03-09
Never having this as an issue for myself, Maybe there is a container open?

After using Docker for a while, you'll have many active (running) and inactive containers on your computer. To view the active ones, use:

  ```
  docker ps
```

You will see output similar to the following:
```
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
f7c79cc556dd        ubuntu              "/bin/bash"         3 hours ago         Up 3 hours                              silly_spence

```
So you may have to kill the open ones first...then try to disable auto-start-up again.

---

### Post by gue22 on 2017-03-10
Thanks, 1fallen,
yup, one container from an Intel Deep Learning SDK install that installed Docker too always ran, so I
sudo systemctl enable docker #was disabled (actually not) from last attempt
# restarted the VM
docker stop 2240e8eexxxx -t 0
sudo systemctl stop docker
sudo systemctl disable docker
#warnings about runlevels as in 1st post; /etc/rc5.d contains K01docker
#Docker still autostarts

Thanks
G.

---

### Post by #&amp;thj^% on 2017-03-10
If you have no more use for your old containers,  then you can do this if you want. (You may need to this to disable the auto-start)
Back up any containers you want first.
[COLOR=#ff0000]***Please don't forget - all your data in the containers will be removed!***[/COLOR]

 1. Kill all running containers:

```
sudo docker kill $(docker ps -q)
```

2. Delete all stopped containers

```
sudo docker rm $(docker ps -a -q)
```

3. Delete all 'untagged/dangling' images

```
sudo docker rmi $(docker images -q -f dangling=true)
```

4. Delete all images

```
sudo docker rmi $(docker images -q)
```

I seem to have good luck stoping docker with:
```
sudo systemctl stop docker

```
Friendly Reminder...Please don't forget - all your data in the containers will be removed!

---

### Post by gue22 on 2017-03-11
Well, thanks 1fallen, for reiterating the commands from the docs to get rid of everything -- but that can't be the point.
Point would be to find why Docker daemon keeps autostarting though allegedly disabled.

---

### Post by gue22 on 2017-03-11
OK, as mostly recently, I found some crude "solution" myself.

sudo nohup gedit /lib/systemd/system/docker.service

#I commented out the command from ExecStart=
ExecStart= #/usr/bin/dockerd -H fd://

As the money is with Ubuntu at some point they thought the can force upstart and the doc says since 15.04 they changed back to systemd, but it seems to be still incomplete a year later in 16.04, because in /lib/systemd/system/docker.service there is a comment
# the default is not to use systemd for cgroups because the delegate issues still
# exists and systemd currently does not support the cgroup feature set required
# for containers run by docker
but the docs everywhere talk about systemd in 15.04 and above.

When I now try to start Docker manually by
sudo systemctl start docker.service
I get
docker.service - Docker Application Container Engine
   Loaded: error (Reason: Invalid argument)
  Drop-In: /etc/systemd/system/docker.service.d
           &#9492;&#9472;http-proxy.conf
   Active: inactive (dead)

There is no proxy configured and http-proxy.conf just contains
[Service]
Environment=


When I
sudo /usr/bin/dockerd -H fd://
I get
no sockets found via socket activation: make sure the service was started by systemd
though I didn't disable this dependency.

Can anyone shed some light on this convoluted BS?
Thanks
G.

---

### Post by #&amp;thj^% on 2017-03-11
> **gue22 said:**
> Well, thanks 1fallen, for reiterating the commands from the docs to get rid of everything -- but that can't be the point.
Point would be to find why Docker daemon keeps autostarting though allegedly disabled.

Maybe give this a try as I just seen you newest post#9 You will have to undo your changes first though.(Just a Heads Up)

I was never able to reproduce your problem...so just the basic rules I follow is all.
No offense meant...Kind of hard for me to gauge someone else's skill level in one post...so forgive the reiterating of the commands.(Maybe useful for future visitors though)

I have just now been able to reproduce your Request for **"Disbaling Docker from Autostarting"**
First just so we are comparing apples to apples...this is the Docker I have installed:
```
~$ apt policy docker.io
docker.io:
  Installed: 1.12.6-0ubuntu1~16.04.1
  Candidate: 1.12.6-0ubuntu1~16.04.1
  Version table:
 *** 1.12.6-0ubuntu1~16.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     1.10.3-0ubuntu6 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
```
After creating a couple of containers I started seeing your same warning/errors
```
Synchronizing state of docker.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install disable docker
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of scriptdocker' overrides LSB defaults (0 1 6).
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of scriptdocker' overrides LSB defaults (0 1 6).
```
I had also seen this in early development so I ran through my normal process of updating the "rc.d"Via:
 ```
sudo update-rc.d docker disable
```
Then finding it was still marked for autostart so I then just changed the switch via:
```
sudo bash -c 'echo manual | sudo tee /etc/init/docker.override'
```
Which now makes it a manual Start by user.


Now after a reboot I show Docker now inactive.
```
$ systemctl status docker
&#9679; docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; disabled; vendor preset: 
   Active: inactive (dead)
     Docs: https://docs.docker.com
```
Now if this dose not work out for you then I would suggest "bum"
```
sudo apt install bum
```
> graphical runlevel editor
  
Boot-Up Manager is a graphical tool to allow easy configuration
of init services in user and system runlevels, as far as changing
Start/Stop services priority.
And just untick it from the startup services.
As for why this happens I have no clues...but the problem of Autostarting Docker should now be up to you to manualy start.
```
$ sudo systemctl start docker.service
[sudo] password for me: 
me@me-750-417c:~$ systemctl status docker
&#9679; docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; disabled; vendor preset: 
   Active: active (running) since Sat 2017-03-11 13:11:32 MST; 50s ago
     Docs: https://docs.docker.com
 Main PID: 16971 (dockerd)
    Tasks: 19
   Memory: 57.9M
      CPU: 402ms
   CGroup: /system.slice/docker.service
           &#9500;&#9472;16971 /usr/bin/dockerd -H fd://
           &#9492;&#9472;16990 containerd -l unix:///var/run/docker/libcontainerd/docker-con

Mar 11 13:11:31 me-750-417c dockerd[16971]: time="2017-03-11T13:11:31.652886317-
Mar 11 13:11:31 me-750-417c dockerd[16971]: time="2017-03-11T13:11:31.653400401-
Mar 11 13:11:31 me-750-417c dockerd[16971]: time="2017-03-11T13:11:31.654372248-
Mar 11 13:11:31 me-750-417c dockerd[16971]: time="2017-03-11T13:11:31.850921339-
Mar 11 13:11:32 me-750-417c dockerd[16971]: time="2017-03-11T13:11:32.373907154-
Mar 11 13:11:32 me-750-417c dockerd[16971]: time="2017-03-11T13:11:32.505518519-
Mar 11 13:11:32 me-750-417c dockerd[16971]: time="2017-03-11T13:11:32.505700857-
Mar 11 13:11:32 me-750-417c dockerd[16971]: time="2017-03-11T13:11:32.505714160-
Mar 11 13:11:32 me-750-417c dockerd[16971]: time="2017-03-11T13:11:32.520280739-
Mar 11 13:11:32 me-750-417c systemd[1]: Started Docker Application Container Eng
```
Cheers

---

