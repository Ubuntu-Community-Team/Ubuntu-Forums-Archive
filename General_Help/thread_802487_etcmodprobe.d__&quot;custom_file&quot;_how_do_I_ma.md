---
title: "/etc/modprobe.d/  &quot;custom file&quot; how do I make one in a terminal?"
date: 2008-05-21
forum: General Help
---

### Post by oxymoron on 2008-05-21
hI,

Im trying to install my hvr-3000 Tv card. Im using the guide below:

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000)

```
 Single Frontend Diff (sfe)

Now all you need to do is edit /etc/modprobe.conf to have

This option will load the DVB-S/S2 frontend and is the default:
options cx88-dvb frontend=0

This option will load the DVB-T frontend:
options cx88-dvb frontend=1

NOTE: On Debian and Ubuntu Systems you will have to enter /etc/modprobe.d/ and create a custom named file that holds the above mentioned content.
```

It says I have to "NOTE: On Debian and Ubuntu Systems you will have to enter /etc/modprobe.d/ and create a custom named file that holds the above mentioned content"

How do i create this custom file in a terminal?

Hope you can help.

---

### Post by pytheas22 on 2008-05-21
It's not entirely clear to me what exactly you're supposed to do, but it seems like they want you to create a file at /etc/modprobe.d/modprobe.conf that contains what they want.  This would do it:

```
sudo -s
cd /etc/modprobe.d
touch modprobe.conf
echo "This option will load the DVB-S/S2 frontend and is the default:" >> modprobe.conf
echo "options cx88-dvb frontend=0" >> modprobe.conf
echo "This option will load the DVB-T frontend:" >> modprobe.conf
echo "options cx88-dvb frontend=1" >> modprobe.conf
```

---

### Post by ibuclaw on 2008-05-21
> **pytheas22 said:**
> It's not entirely clear to me what exactly you're supposed to do, but it seems like they want you to create a file at /etc/modprobe.d/modprobe.conf that contains what they want.  This would do it:

You could name the file anything you like.

For standing out sake, I recommend that you create a file called **wintvhvr.conf**

```

sudo touch /etc/modprobe.d/wintvhvr.conf
sudo gedit /etc/modprobe.d/wintvhvr.conf

```
Then copy and paste it in there.

And remember, any comments put in the file must be commented out with a "#" hash.
To take your quote:
[PHP]
#This option will load the DVB-S/S2 frontend and is the default:
options cx88-dvb frontend=0

#This option will load the DVB-T frontend:
options cx88-dvb frontend=1
[/PHP]

Regards
Iain

---

