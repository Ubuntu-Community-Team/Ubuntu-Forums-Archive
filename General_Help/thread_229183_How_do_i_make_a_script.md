---
title: "How do i make a script??????"
date: 2006-08-04
forum: General Help
---

### Post by dhruv_1884 on 2006-08-04
Hi Guys,

Whenever i need to log on to the net, i need to run the following command in the terminal

./crclient -u rajan

I was wondering if there was a possibility to create a script which i could just double click from my Desktop and i would be connected to the net.


Thanks

Regards

Dhruv

---

### Post by cantormath on 2006-08-04
> **dhruv_1884 said:**
> Hi Guys,

Whenever i need to log on to the net, i need to run the following command in the terminal

./crclient -u rajan

I was wondering if there was a possibility to create a script which i could just double click from my Desktop and i would be connected to the net.


Thanks

Regards

Dhruv

what command is that?

---

### Post by dhruv_1884 on 2006-08-04
Thats not a command,

it's the client distributed by my isp for linux systems, the binary files name is crclient, the option u is for user name and rajan is the user name

hope u get it now

regards 

dhruv

---

### Post by kerry_s on 2006-08-04
Yes just creat a text file put> 

exec ./crclient -u rajan
or
#!/bin/sh
./crclient -u rajan

Then save it and right click on it> Properties> Permissions> click on execute

Know it's all set up you can create the launcher,the command would be like> /home/(your name)/(name of your file)

You can also put your script in> /home/user/.gnome2/nautilus-scripts

and it will be in your right click menu under scripts.

---

### Post by dhruv_1884 on 2006-08-04
Sorry bro, but that didnt work,
i put the line in start up programs and it did work, now i log onto the net on startup, but i'd still prefer having some sort of script.

any other suggestions



thanks

regards

dhruv

---

### Post by CameronCalver on 2006-08-04
try this
```
gedit /home/username/Desktop/internet
```
then type in

```

#!/bin/sh
./crclient -u rajan

```

then 
```
chmod +x /home/username/Desktop/internet

```

then run it

---

### Post by Ramses de Norre on 2006-08-04
I'd copy (or symlink) the binary to /usr/bin/, make it executable and then just set crcclient -u rajan as a startup command.

---

### Post by skymt on 2006-08-04
> **Ramses de Norre said:**
> I'd copy (or symlink) the binary to /usr/bin/, make it executable and then just set crcclient -u rajan as a startup command.

That's:
```
sudo cp crclient /usr/bin/
sudo chmod +x /usr/bin/crclient
```

... in the terminal.

Then set up your startup command as described, in the Sessions control panel.

---

### Post by cantormath on 2006-08-04
> **dhruv_1884 said:**
> Thats not a command,

it's the client distributed by my isp for linux systems, the binary files name is crclient, the option u is for user name and rajan is the user name

hope u get it now

regards 

dhruv

ah, didnt see the ./

---

