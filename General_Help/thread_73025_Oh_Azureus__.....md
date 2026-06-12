---
title: "Oh Azureus  ...."
date: 2005-10-07
forum: General Help
---

### Post by dbee on 2005-10-07
Where art thou Azureus ????

---------------------------------------------------------------------------------------------------------

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-backports main universe restricted multiverse restricted

---

### Post by tehwa on 2005-10-07
He's been sighted here.

[http://ubuntuforums.org/showthread.php?t=71817](http://ubuntuforums.org/showthread.php?t=71817)

---

### Post by Pablo_Escobar on 2005-10-08
Step 1. Download from [http://azureus.sourceforge.net/download.php]("http://azureus.sourceforge.net/download.php") GTK client
Step 2. Untar it to some created folder (/home/username/Programs/azureus/)
Step 3. Make a link to azureus file in the folder You've created 

and voila :)

(Considering You've setup java properly :D )

---

### Post by flub on 2005-10-09
Being a bit of a N00b to Linux can you help me.

I've completed steps 1 and 2 and "think" Ive done no.3 but when I click the link the nothing happens.

Java also appear to have been load (I can load applets within Firefox and the Java control panel loads up).

Thanks in advance.

---

### Post by flub on 2005-10-09
It's ok I fixed it .. thanks.

(had the program path wrong)

---

### Post by sickdude on 2005-10-12
well this sucks, i used to install azureus trough apt-get, but now its gone i did the manual thing and it worked....... well it worked once or twice. now when i try to run it it kinda does nothing

StartSocket: passing startup args to already-running Azureus java process.
DEBUG::Wed Oct 12 22:43:39 CEST 2005
  java.net.ConnectException: Connection timed out
        at java.net.PlainSocketImpl.socketConnect(Native Method)
        at java.net.PlainSocketImpl.doConnect(Unknown Source)
        at java.net.PlainSocketImpl.connectToAddress(Unknown Source)
        at java.net.PlainSocketImpl.connect(Unknown Source)
        at java.net.SocksSocketImpl.connect(Unknown Source)
        at java.net.Socket.connect(Unknown Source)
        at java.net.Socket.connect(Unknown Source)
        at java.net.Socket.<init>(Unknown Source)
        at java.net.Socket.<init>(Unknown Source)
        at org.gudy.azureus2.ui.swt.StartSocket.<init>(StartSocket.java:44)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:75)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:98)

Azureus TERMINATED.
sickdude@megatron:~/azureus$


i did a killall java and azureus tried it again but nothing dam azureus :(

---

