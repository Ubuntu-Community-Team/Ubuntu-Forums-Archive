---
title: "x11vnc stop working"
date: 2020-11-17
forum: General Help
---

### Post by iespinosan on 2020-11-17
THE PROBLEM IS SOLVED. YOU CAN CLOSE THIS THREAD. THANKS.


Good morning.

I have some computers with x11vnc working and using a .service to start the vnc connection when boot, but for some reason this is not working in the last computers that I configured. Only it works if I execute the command "x11vnc", I checked the configurations and are exactly the same.

I created the file /etc/systemd/system/x11vnc.service with this configuration:

[ATTACH=CONFIG]287370[/ATTACH]

The password file is located in /etc/.vnc/passwd and as you can see both files are owned by "root"

[ATTACH=CONFIG]287372[/ATTACH]

As you can see the service starts fine, but seems that something is failing and I dont know what exactly is. I check some posts to verify configs and even i made the change to lightdm and "dpkg-reconfigure lightdm" and still nto working.

[ATTACH=CONFIG]287371[/ATTACH]

Any help will be appreciated. Thanks for your time.

---

