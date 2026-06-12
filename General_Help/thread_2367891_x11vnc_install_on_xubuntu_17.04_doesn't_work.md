---
title: "x11vnc install on xubuntu 17.04 doesn't work"
date: 2017-08-04
forum: General Help
---

### Post by tomofedekkula on 2017-08-04
Can you please tell me where is problem with configuring x11vnc. I am using a xubuntu 17.04. On xUbuntu 14.04 working just fine. I just cant connect, where is problem?


this is how i install and configure x11vnc
```

sudo apt-get install x11vnc -y && 
sudo x11vnc -storepasswd johnyking123 /etc/x11vnc.pass && 
sudo chmod 744 /etc/x11vnc.pass && 
sudo cp /home/johny/x11vnc.conf /etc/init 

```


My x11vnc.conf file


```

start on login-session-start
script
x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever -shared -bg -o /var/log/x11vnc.log -rfbauth /etc/x11vnc.pass -rfbport 5900
end script

```

---

### Post by steeldriver on 2017-08-04
You probably need to replace the upstart-based conf file with an equivalent systemd unit file as described here:

[How to setup x11vnc to access with graphical login screen?](https://askubuntu.com/a/676978/178692)

Hope this helps

---

### Post by tomofedekkula on 2017-08-04
I dont have[COLOR=#111111][FONT=Consolas] /etc/systemd/system/x11vnc.service file[/FONT][/COLOR]

---

### Post by steeldriver on 2017-08-04
The point is that you should create one - **instead of** creating a /etc/init/x11vnc.conf file

The different versions of Ubuntu use different init systems

---

