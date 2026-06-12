---
title: "wpa_supplicant problems please help"
date: 2007-10-08
forum: General Help
---

### Post by olieviya on 2007-10-08
This is very important, I am on a campus network and this year they have changed stuff and need us to use wpa_supplicant to connect to the network.

The instructions are (I added sudo in front of all):

```
Network Access Service
NAS Setup - Linux with WPA Supplicant
Download the root certificates from Verisign at : http://www.verisign.com/support/roots.html

Change to the directory where the file was downloaded to.

# unzip roots.zip

# cp VeriSign_Roots/SecureServer.509 /etc/wpa_supplicant/

Now create /etc/wpa_supplicant.conf as shown below :-

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=root
ap_scan=0
network={
key_mgmt=IEEE8021X
eap=PEAP
ca_cert=/etc/wpa_supplicant/SecureServer.509
subject_match="/C=GB/L=York/O=University of York/OU=Computing Service/OU=Terms of use at www.verisign.co.uk/rpa (c)05/OU=Authenticated by VeriSign/OU=Member, VeriSign Trust Network/CN=nasaaa1.york.ac.uk"
subject_match="/C=GB/L=York/O=University of York/OU=Computing Service/OU=Terms of use at www.verisign.co.uk/rpa (c)05/OU=Authenticated by VeriSign/OU=Member, VeriSign Trust Network/CN=nasaaa2.york.ac.uk"
identity="usernamegoeshere"
password="passwordgoeshere"
phase1="peaplabel=0"
phase2="auth=MSCHAPV2"
}

# ifconfig eth0 promisc

# wpa_supplicant -i eth0 -d -B -Dwired -c /etc/wpa_supplicant.conf

# dhclient eth0
```

Unfortunately this doesn't work for me, I get the following errors:

```
# sudo wpa_supplicant -i eth0 -d -B -Dwired -c /etc/wpa_supplicant.conf
Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'wired' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group='root' (DEPRECATED)
ap_scan=0
Line 7: failed to parse ca_cert '/etc/wpa_supplicant/SecureServer.509'.
Line 7: failed to parse ca_cert '/etc/wpa_supplicant/SecureServer.509'.
Line 14: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface eth0
Cancelling scan request

```

Please help.:(

---

### Post by strabes on 2007-10-08
Does nm-applet not support WPA for you or something? Why are you doing it this way?

---

### Post by olieviya on 2007-10-08
> **strabes said:**
> Does nm-applet not support WPA for you or something? Why are you doing it this way?

Was told to, is there another way?
Still not working.

---

### Post by flargen on 2007-10-11
I have been having problems with the network here at York too. I found that surrounding the path to the certificate with double quotes gets rid of the error, but does not solve the problem:

```
ca_cert="/etc/wpa_supplicant/SecureServer.509"
```
instead of:

```
ca_cert=/etc/wpa_supplicant/SecureServer.509
```
I wish that nm-applet supported secure wired networks as well as it does wireless - this would be much easier!

---

### Post by olieviya on 2007-10-11
> **flargen said:**
> I have been having problems with the network here at York too. I found that surrounding the path to the certificate with double quotes gets rid of the error, but does not solve the problem:

```
ca_cert="/etc/wpa_supplicant/SecureServer.509"
```
instead of:

```
ca_cert=/etc/wpa_supplicant/SecureServer.509
```
I wish that nm-applet supported secure wired networks as well as it does wireless - this would be much easier!

Yes, this is ****, do you know of anybody who has managed to get it working here at york????

---

### Post by olieviya on 2007-10-11
bump bump bump, help anybody?

---

### Post by viciouslime on 2007-10-13
I am also having problems with the network here at York :(

Are you both freshers too?

---

### Post by flargen on 2007-10-14
Yeah, i'm a fresher.

I got it to work! Make a /etc/wpa_supplicant.conf file as it says on [http://www.york.ac.uk/services/cserv/net/nas/linux.html]("http://www.york.ac.uk/services/cserv/net/nas/linux.html") Delete the lines from /etc/wpa_supplicant.conf that start with ca_cert and subject_match. Replace the username and password fields with your own York ones. Follow the rest of the instructions. You will have to run wpa_supplicant and dhclient each time you turn on your pc manually, unless you make a script or whatever.

Hope this is helpful!

---

### Post by viciouslime on 2007-10-14
> **flargen said:**
> Yeah, i'm a fresher.

I got it to work! Make a /etc/wpa_supplicant.conf file as it says on [http://www.york.ac.uk/services/cserv/net/nas/linux.html]("http://www.york.ac.uk/services/cserv/net/nas/linux.html") Delete the lines from /etc/wpa_supplicant.conf that start with ca_cert and subject_match. Replace the username and password fields with your own York ones. Follow the rest of the instructions. You will have to run wpa_supplicant and dhclient each time you turn on your pc manually, unless you make a script or whatever.

Hope this is helpful!

Odd... i tired that before and it didn't work for me... I'll try it again though.

---

### Post by viciouslime on 2007-10-15
This does indeed work... Don't know why it didn't before, I must have forgotten to run that last command again i think... anyway I am in the process of building a deb to do this. Nearly finished now, should make it easier for all :D

---

### Post by olieviya on 2007-10-17
> **viciouslime said:**
> This does indeed work... Don't know why it didn't before, I must have forgotten to run that last command again i think... anyway I am in the process of building a deb to do this. Nearly finished now, should make it easier for all :D

Interesting, where/when are you uploading it? :)
Btw not a fresher, since you asked. We used the SNS last year which is why I am having trouble.

---

### Post by viciouslime on 2007-10-18
Ok, the deb is ready. If anyone else is having problems, just go to my site ([http://www.viciouslime.co.uk/]("http://www.viciouslime.co.uk/")) then go to Downloads, then Debs and you'll find york-sns. Install this, enter your username and password when prompted et voila...

---

### Post by olieviya on 2007-10-18
> **viciouslime said:**
> Ok, the deb is ready. If anyone else is having problems, just go to my site ([http://www.viciouslime.co.uk/]("http://www.viciouslime.co.uk/")) then go to Downloads, then Debs and you'll find york-sns. Install this, enter your username and password when prompted et voila...

Sorry for being a pain but since you went through all the trouble etc etc you might like to share it, with the rest of the uni, I dunno how useful it will be ie how many people are in fact using the NAS (yeah, the SNS was used last year it's the NAS now) on ubuntu, but you could send them the link and explain a bit so that they could direct people to it I suppose. Thanks! :KS:KS:KS:KS:KS

Ps: Unless you have been on-line for the same time period as me editing your .deb or something you have a small bug on your site which does not allow for d/l the file. "The document is being edited/updated by a User and is unavailable at this moment.".

---

### Post by viciouslime on 2007-10-19
Thanks for pointing out all those mistakes! You're not being a pain at all, it's really useful! :D

I think I've corrected all of them now. Please let me know if it works for you :)

---

### Post by olieviya on 2007-10-20
> **viciouslime said:**
> Thanks for pointing out all those mistakes! You're not being a pain at all, it's really useful! :D

I think I've corrected all of them now. Please let me know if it works for you :)

Ok, I don't know why or how but I did a clean install of ubuntu the other day and you definately do not need to use wpa_supplicant or anything the internet seems to work fine, I just booted up and it was all "normal". Does yours not work without wpa_supplicant??
PS: Actually it's funky, probs needs wpa_supplicant to work properly. But it's almost perfect, very weird.

---

### Post by viciouslime on 2007-10-20
> **olieviya said:**
> Ok, I don't know why or how but I did a clean install of ubuntu the other day and you definately do not need to use wpa_supplicant or anything the internet seems to work fine, I just booted up and it was all "normal". Does yours not work without wpa_supplicant??
PS: Actually it's funky, probs needs wpa_supplicant to work properly. But it's almost perfect, very weird.

Have you tried using something dynamic? Like signing in to gmail, or your bank account or something? You'll probably find you're just accessing pages from the Uni's cache and with so many students accessing so many things an awful lot of stuff is cached. I had the same thing. You can't check e-mail (via pop/imap), use ssh, connect to msn, yahoo, jabber etc though...

---

### Post by olieviya on 2007-10-20
> **viciouslime said:**
> Have you tried using something dynamic? Like signing in to gmail, or your bank account or something? You'll probably find you're just accessing pages from the Uni's cache and with so many students accessing so many things an awful lot of stuff is cached. I had the same thing. You can't check e-mail (via pop/imap), use ssh, connect to msn, yahoo, jabber etc though...

Yeah, you are right, the very weird thing is I have installed the .deb and it's still not working... but I can log in to my email (not gmail) and facebook but not other sites, weird.

---

### Post by viciouslime on 2007-10-21
> **olieviya said:**
> Yeah, you are right, the very weird thing is I have installed the .deb and it's still not working... but I can log in to my email (not gmail) and facebook but not other sites, weird.

Hmm that's odd, I've tried it from a fresh install and it works fine for me. Have you tried restarting... I know that's not the typical linux way to fix something, but I don't think I made the deb run the script that gets everything going once it ha been installed because it caused the installation to hang. Instead it is run every boot.

I will work on this for the next version. For now though, installing the deb then restarting should work... or you could manually run:

sudo wpa_supplicant -i eth0 -d -B -Dwired -c /etc/wpa_supplicant.conf
sudo dhclient eth0

---

### Post by olieviya on 2007-10-21
> **viciouslime said:**
> Hmm that's odd, I've tried it from a fresh install and it works fine for me. Have you tried restarting... I know that's not the typical linux way to fix something, but I don't think I made the deb run the script that gets everything going once it ha been installed because it caused the installation to hang. Instead it is run every boot.

I will work on this for the next version. For now though, installing the deb then restarting should work... or you could manually run:

sudo wpa_supplicant -i eth0 -d -B -Dwired -c /etc/wpa_supplicant.conf
sudo dhclient eth0

Yes, it needed a reboot, dunno what I was smoking last night (nothing, honestly) my brain was just running on 3 hours sleep, so it when it did occur to me to try that I somehow decided it was better to go to the kitchen and make food and then completely forget, anyway, it works perfectly. :lolflag:

---

### Post by viciouslime on 2007-10-21
> **olieviya said:**
> Yes, it needed a reboot, dunno what I was smoking last night (nothing, honestly) my brain was just running on 3 hours sleep, so it when it did occur to me to try that I somehow decided it was better to go to the kitchen and make food and then completely forget, anyway, it works perfectly. :lolflag:

Lol good to know, thanks. I'll try working on it later so that you don't have to reboot.

---

