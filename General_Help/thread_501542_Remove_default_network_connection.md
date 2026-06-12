---
title: "Remove default network connection?"
date: 2007-07-15
forum: General Help
---

### Post by mcarro on 2007-07-15
Hi.  Time ago, when I installed Ubuntu on my laptop (almost a couple of years ago?) I selected the ethernet port (eth0) to be the default Internet connection.  Today I am using mostly the wireless connection.  However, upon hibernate/resume or suspend/resume, and also after startup, the system always tries to bring eth0 up.  I just bring it down with ifconfig, but I am tired of doing that.

Is there any way not to have a default internet connection?  I am ok with NetworkManager and with manually selecting the network profile (I have already several profiles).

Thanks in advance for any help!

---

### Post by jimbob on 2007-07-15
My advice would be to ditch Ubuntu's network-managr and go with something like Wicd (*[COLOR="Blue"]http://wicd.sourceforge.net/download.php[/COLOR]*) that is smart enough to detect which network connection is hooked up and automatically connect you to it.  (At least that's the way it works on both of my laptops; a Toshiba and an HP running Feisty).
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by mcarro on 2007-07-16
> **jimbob said:**
> My advice would be to ditch Ubuntu's network-managr and go with something like Wicd (*[COLOR="Blue"]http://wicd.sourceforge.net/download.php[/COLOR]*) that is smart enough to detect which network connection is hooked up and automatically connect you to it.  (At least that's the way it works on both of my laptops; a Toshiba and an HP running Feisty).


Maybe I did not explain myself clearly.  A default network interface (eth0, ethernet) is set up without doing anything on my side every time I boot the computer or I resume (either froms suspension or from hibernation).

Thanks for your tip, anyway.  Just one question: Is wicd able to assign a *fixed* IP address to a WAP-encrypted wireless connection?  I was using NetworkManager (caps necessary) to deal with wireless, which worked fine except that the stable version didn't seem capable of doing precisely that.

---

### Post by jimbob on 2007-07-16
Don't know since I use DHCP but it's worth a try and simple to go back to Ubuntu's network-manager if you don't like it.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by imdano on 2007-07-16
You can assign a static IP in wicd, yes.

---

### Post by mcarro on 2007-07-16
> **imdano said:**
> You can assign a static IP in wicd, yes.

How does wicd compare with wifi-radar, if you have any experience with the latter?  Is it easy to set WPA authentication with wicd?

Thanks a lot for all your help!

---

### Post by jimbob on 2007-07-16
> Is it easy to set WPA authentication with wicd?

If it was any easier a caveman could do it ...
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by imdano on 2007-07-16
I haven't used wifi radar, but in wicd you just open the expander for the network you want to connect to, set the encryption type to WPA 1/2, then enter your password, then hit connect.  Once it's entered the first time you don't have to do it again.  Pretty simple.

---

### Post by pak33m on 2007-07-16
mcarro,

You would simply use the built-in network-admin to both configure a static IP and connect every time with one interface.  network-admin will modify your /etc/network/interfaces file with the configuration that you setup or you can even manually do it.  However, you will want to remove Network Manager if you do this beacause network-admin and Network Manager conflict when trying to establish a network connection.  If you use network-admin you will either Alt+F2 and type network-admin or go to System -> Admin -> Networking.

You can still configure a static IP with Network Manager. 

Hope this helps some.

---

### Post by mcarro on 2007-07-17
> **pak33m said:**
> mcarro,

You would simply use the built-in network-admin to both configure a static IP and connect every time with one interface.  network-admin will modify your /etc/network/interfaces file with the configuration that you setup or you can even manually do it.  However, you will want to remove Network Manager if you do this beacause network-admin and Network Manager conflict when trying to establish a network connection.  If you use network-admin you will either Alt+F2 and type network-admin or go to System -> Admin -> Networking.

You can still configure a static IP with Network Manager. 

Hope this helps some.

For some reason network-admin (or at least the version I am using - I am on Feisty) does not give any way to enter a WPA password.  I do use network-admin for wired connections.  May this be due to the conflicts you are referring to?

Thanks for your help!

---

### Post by mcarro on 2007-07-18
Guys,

thanks for the WICD advice.  It's been working beautifully so far.

---

### Post by diafygi on 2007-08-09
I've found that this post is particularly helpful. I just wish it was easier to find.

[http://ubuntuforums.org/showthread.php?p=2316847#post2316847](http://ubuntuforums.org/showthread.php?p=2316847#post2316847)

---

