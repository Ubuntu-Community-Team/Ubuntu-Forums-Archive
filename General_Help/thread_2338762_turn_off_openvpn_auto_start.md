---
title: "turn off openvpn auto start"
date: 2016-10-01
forum: General Help
---

### Post by marchello_lippi2 on 2016-10-01
Hi all, 
How do I turn off openvpn auto start? 
I would like rather to start it manually on demand using 
```
sudo service openvpn start
```
Please advise.

---

### Post by #&amp;thj^% on 2016-10-01
What version are you using?? 14.04 or 16.04

---

### Post by marchello_lippi2 on 2016-10-03
Sorry I did not say this earlier, I'm using 14.04 version for now.
Please advise.

---

### Post by #&amp;thj^% on 2016-10-03
The method here is for 14.04...(Non systemd)
You have two options:

    Run in Terminal:

   ```
 sudo update-rc.d openvpn disable

```
    Then you'll have to run **"sudo service openvpn start"** to manually start the VPN.

    Or edit the file /etc/default/openvpn

    ```
sudo gedit /etc/default/openvpn
```
Or use the text editor you prefer.

    And uncomment the line:

  ```
  #AUTOSTART="none"
```

    So it looks like:

  ```
  AUTOSTART="none"
```

    Then you'll have to run sudo service openvpn start <vpn-name> to manually start the VPN. <vpn-name> is the config file name without .conf.
Hope this makes sense.

---

### Post by kevdog on 2016-10-04
Maybe I'll take a crack at this one since you are using upstart -- sudo service openvpn stop,  sudo service openvpn remove

---

