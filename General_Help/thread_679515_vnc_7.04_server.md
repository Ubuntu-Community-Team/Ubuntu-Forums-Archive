---
title: "vnc 7.04 server"
date: 2008-01-27
forum: General Help
---

### Post by taimur on 2008-01-27
hi 
i m using linux ubuntu 7.04 server
by terminal i install by sudo apt-get install ubuntu-desktop

now after that i want to configure vnc through terminal (putty) 

thanks 
taimur

---

### Post by gvartser on 2008-01-27
1) log on to your server ussing ssh

2) Install VNC Server: (Need sudo / root access to do this)
```
sudo apt-get install vncserver

```

3) Start VNC Server: (Start it as the user you would like to login as. NOT AS ROOT)
```
vncserver
```

Then set a password, when asked for it:
```
You will require a password to access your desktops.

Password: 
Verify:   

New 'X' desktop is <host_name>:1
```


4) Connect to your vnc server using the info given in "New 'X' desktop is:"

Additional info regarding VNC:
To stop the vncserver:
```
vncserver -kill :<display number>
```

Further information:
```
vncserver --help
```

/g

---

