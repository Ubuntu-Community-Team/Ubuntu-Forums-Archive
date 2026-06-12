---
title: "Ubuntu 18.04 Autorun a command at log in"
date: 2018-04-30
forum: General Help
---

### Post by ilyas95 on 2018-04-30
I would like to automatically run a command to connect to a vpn when I log in
Do you know how can i do it?
The command is sudo openvpn --config /etc/openvpn/blabla.ovpn
Thank you

---

### Post by Xian on 2018-05-01
First create a file /etc/rc.local

In that file add these contents:

```
#!/bin/sh -e
openvpn --config /etc/openvpn/blabla.ovpn
exit 0
```

Save the file. Make it executable with the terminal command:

$ sudo chmod +x /etc/rc.local

Commands in the file prior to exit 0 should be executed as root at startup.

---

### Post by yancek on 2018-05-01
You could also use a cron job to start the script on login.  Make sure the script is in the PATH.

> @reboot /bin/sh enter command here

---

### Post by ilyas95 on 2018-05-01
> **Xian said:**
> First create a file /etc/rc.local

In that file add these contents:

```
#!/bin/sh -e
openvpn --config /etc/openvpn/blabla.ovpn
exit 0
```

Save the file. Make it executable with the terminal command:

$ sudo chmod +x /etc/rc.local

Commands in the file prior to exit 0 should be executed as root at startup.

Thanks for your help Xian
I tried it but I don't know why but after doing it when I reboot it freezes at the purple screen after selecting ubuntu from grub
Then I went in recovery mode and I deleted the rc.local file and after that it booted normally
Do you know why?

---

### Post by ilyas95 on 2018-05-01
> **yancek said:**
> You could also use a cron job to start the script on login.  Make sure the script is in the PATH.

Thanks for helping, do you mean the cron file has to be in the same folder as the ovpn files?
Sorry but I'm a beginner and never did a cron job D:

---

### Post by Xian on 2018-05-01
First make sure you have a cron program installed, such as:

```
sudo apt-get install anacron
```

Then you just need to input the desired command. 
Type this into a terminal by using the edit (-e) option:

```
crontab -e
```

Scroll to the bottom of the file and type what you want to execute:

```
@reboot &#8203;[COLOR=#000000]/bin/sh [/COLOR][COLOR=#000000][FONT=&amp]openvpn --config /etc/openvpn/blabla.ovpn[/FONT][/COLOR]
```

Then save & exit the file. Usually keyboard strokes CTRL+s then CTRL+x
You can verify entered correctly with the list (-l) option:

```
$ crontab -l
```

But .... I can not say but that it might freeze again. 
I've no way to test it from the computer I'm working on currently.

---

### Post by yancek on 2018-05-01
> [COLOR=#000000]Thanks for helping, do you mean the cron file has to be in the same folder as the ovpn files?[/COLOR]

No.  Follow the steps posted above by Xian.  If the file opens with text editor vi/vim, you need to hit the i key for insert to insert data and when finished, hit the Esc key then enter  :wq and hit the enter key to save.

---

### Post by ilyas95 on 2018-05-02
> **Xian said:**
> First make sure you have a cron program installed, such as:

```
sudo apt-get install anacron
```

Then you just need to input the desired command. 
Type this into a terminal by using the edit (-e) option:

```
crontab -e
```

Scroll to the bottom of the file and type what you want to execute:

```
@reboot &#8203;[COLOR=#000000]/bin/sh [/COLOR][COLOR=#000000][FONT=&amp]openvpn --config /etc/openvpn/blabla.ovpn[/FONT][/COLOR]
```

Then save & exit the file. Usually keyboard strokes CTRL+s then CTRL+x
You can verify entered correctly with the list (-l) option:

```
$ crontab -l
```

But .... I can not say but that it might freeze again. 
I've no way to test it from the computer I'm working on currently.
  
I did it and the systems didn't freeze but it doesn't work as my ip didn't change and there is no openvpn process active
I guess I just have to do it manually D:

---

### Post by Xian on 2018-05-02
If this really has to be run at login and not reboot then you can:

Add the desired command at the bottom of your $HOME/.profile file

---

### Post by ilyas95 on 2018-05-03
> **Xian said:**
> If this really has to be run at login and not reboot then you can:

Add the desired command at the bottom of your $HOME/.profile file
Hi Xian,
It did but I still have a problem
If I insert the command without sudo it doesn't connect to the server due to the following error (this happens even if I run the command manually without sudo)
```

Thu May  3 11:41:09 2018 ERROR: Cannot ioctl TUNSETIFF tun: Operation not permitted (errno=1)
Thu May  3 11:41:09 2018 Exiting due to fatal error

```
But when I add the sudo command inside the .profile file, after I log in I get a black screen and when I press the power button to shut down I see in the background that is waiting for the password so that's the reason for the freeze
Is there a way to run a command as root in the profile file without password?
Thank you Xian

---

### Post by Xian on 2018-05-03
There are method(s) by entering some verbiage into your sudoers file. 
But that can be potentially less than secure ....

Let's try this first:

Create a file (I'll just call it foo.sh) with these contents:

```
#!/bin/bash
openvpn --config /etc/openvpn/blabla.ovpn
```

Save the file as foo.sh

Then perform a chown & chmod command on the file:

```
sudo chown root:root /path/to/foo.sh
sudo chmod 4775 /path/to/foo.sh
```

This will make the command run as root w/out neeeding to invoke sudo.

Finally go into System Preferences and look for Startup Applications.
Choose to add a new entry and type this as the command:

```
bash /path/to/foo.sh
```

---

### Post by ilyas95 on 2018-05-06
> **Xian said:**
> There are method(s) by entering some verbiage into your sudoers file. 
But that can be potentially less than secure ....

Let's try this first:

Create a file (I'll just call it foo.sh) with these contents:

```
#!/bin/bash
openvpn --config /etc/openvpn/blabla.ovpn
```

Save the file as foo.sh

Then perform a chown & chmod command on the file:

```
sudo chown root:root /path/to/foo.sh
sudo chmod 4775 /path/to/foo.sh
```

This will make the command run as root w/out neeeding to invoke sudo.

Finally go into System Preferences and look for Startup Applications.
Choose to add a new entry and type this as the command:

```
bash /path/to/foo.sh
```

I did it but it doesn't work: I'll just do it manually when I need it
Also thank you for your help, I learnt a lot of new things!

---

### Post by nlee2 on 2018-05-06
> **ilyas95 said:**
> I would like to automatically run a command to connect to a vpn when I log in
Do you know how can i do it?
The command is sudo openvpn --config /etc/openvpn/blabla.ovpn
Thank you

save the following in ~/.config/autostart/blabla.desktop. then logout and login

```
[Desktop Entry]
Type=Application
Exec=sh -c "sudo /usr/bin/openvpn --config /etc/openvpn/blabla.ovpn"
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=blabla
Comment=

```

If you need to run openvpn client as a service then

```
systemctl enable [EMAIL="openvpn@blabla.servic"]openvpn@blabla.servic[/EMAIL]e
systemctl start [EMAIL="openvpn@blabla.servic"]openvpn@blabla.servic[/EMAIL]e
systemctl status [EMAIL="openvpn@blabla.servic"]openvpn@blabla.servic[/EMAIL]e
```

---

### Post by ilyas95 on 2018-05-06
> **nlee2 said:**
> save the following in ~/.config/autostart/blabla.desktop. then logout and login

```
[Desktop Entry]
Type=Application
Exec=sh -c "sudo /usr/bin/openvpn --config /etc/openvpn/blabla.ovpn"
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=blabla
Comment=

```

If you need to run openvpn client as a service then

```
systemctl enable [EMAIL="openvpn@blabla.servic"]openvpn@blabla.servic[/EMAIL]e
systemctl start [EMAIL="openvpn@blabla.servic"]openvpn@blabla.servic[/EMAIL]e
systemctl status [EMAIL="openvpn@blabla.servic"]openvpn@blabla.servic[/EMAIL]e
```
I have no openvpn file/folder under /usr/bin. Should I just put openvpn?

---

### Post by nlee2 on 2018-05-06
what is the output of

```
which openvpn
```

---

### Post by ilyas95 on 2018-05-06
> **nlee2 said:**
> what is the output of

```
which openvpn
```

/usr/sbin/openvpn

---

### Post by nlee2 on 2018-05-06
Try saving this in ~/.config/autostart then logout and login

```
[Desktop Entry]
Type=Application
Exec=sh -c "sudo /usr/sbin/openvpn --config /etc/openvpn/blabla.ovpn"
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=blabla
Comment=
```

---

