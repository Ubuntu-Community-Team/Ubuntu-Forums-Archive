---
title: "firestarter and juniper vpn"
date: 2007-07-21
forum: General Help
---

### Post by dachinster on 2007-07-21
hi,
i recently got my juniper vpn to work following a bit of madscientist's tutorial and another from off the web at flexion.org

here is what i did to get it to work on ubuntu 7.04 if you are interested:
> sudo apt-get install openssl
sudo apt-get install libmotif3
sudo apt-get install libstdc++2.10-glibc2.2
sudo ln -s /usr/lib/libssl.so.0.9.8 /usr/lib/libssl.so.2
sudo ln -s /usr/lib/libcrypto.so.0.9.8 /usr/lib/libcrypto.so.2
sudo gedit /etc/ld.so.conf
Add the line...
/usr/X11R6/lib
sudo ldconfig
rm -rf ~/.juniper_networks

Login to your Juniper SSL VPN homepage.
Click on the Network Connect Start button.
A popup will appear saying "Loading Network Connect Client. Please wait"
An xterm window will appear with the title installNC.sh which will prompt you for a password.
CTRL-D at the password prompt and when asked to try again answer 'N'.
Logout from the SSL VPN homepage and close Firefox/Mozilla.
From a shell do the following...
cd ~/.juniper_networks
rm -rf network_connect
cp -R tmp network_connect

then simply log back in and this time, put in your password when prompted

now i have another problem.
The VPN and firestarter don't play nice together.
Once firestarter is enabled, the VPN does not work.

I have visited firestarter's website and they have assistance for other firewalls such as Cisco VPN but not for the Juniper SSL VPN.

Can anyone here assist me?

---

### Post by dachinster on 2007-07-22
anyone?

---

### Post by dachinster on 2007-07-22
bump

---

### Post by dachinster on 2007-07-23
anyone?
anything?

---

### Post by dachinster on 2007-07-24
i guess ill have to keep hunting

---

### Post by wnelson on 2007-07-25
Issue netstat -tanup and find out which port is being used and go into firestarter and create a policy letting that port be open.

Walt

---

### Post by dachinster on 2007-07-28
Hi Walt,
Using your suggestion i was able to make it work!

I just did sudo netstat -tanup before initating the connection and then after and compare.

thanks again for the help!

---

