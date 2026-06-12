---
title: "coding help with wake on lan instructions"
date: 2007-06-22
forum: General Help
---

### Post by fast eddie on 2007-06-22
I posted this in the beginners forum but hannt had any replies - can anyone here please help.

I was given this bit of code to make the wake on lan function work. The problem is I am not a coder so can someone please let me know how I would create a start up file as described in the code in red
```


> First become the root user
> # sudo -i
> 
> Find the name of your ethernet port (most likely eth0) look for your ip 
> address
> # ifconfig
> 
> Issue the volitile command to enable magic packet wakeup (example if your 
> port is called eth0)
> # ethtool -s eth0 wol g
> 
> [COLOR="Red"]Create a startup file to always set this parameter
> # vi /etc/init.d/wol
> 
> ...and add the following between the ---'s
> 
> ---
> #!/bin/bash
> /usr/sbin/ethtool -s eth0 wol g
> exit
> ---[/COLOR]
> 
> Make the script executable
> # chmod 755 /etc/init.d/wol
> 
> Make the script run at startup
> # update-rc.d -f /etc/init.d/wol defaults
> 

```

---

### Post by aJayRoo on 2007-06-22
The text in red is simply describing the process of creating a file call "wol" in the directory "/etc/init.d". The command:
```
vi /etc/init.d/wol
```
launches a text editor called vi allowing you to edit the specified file. Vi is a pretty complicated editor to get to grips with so perhaps you would be better off using something simpler. Try this:
```
gksudo gedit /etc/init.d/wol
```
which will open up a blank text file in the gnome text editor gedit. The next step is to simply copy the text between the --- lines:
```
#!/bin/bash
/usr/sbin/ethtool -s eth0 wol g
exit
```
into that text file and save it then exit the text editor. The next two steps should be typed at the terminal in the same way as the first three were. Hope that helps.

---

