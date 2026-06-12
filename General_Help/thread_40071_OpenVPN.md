---
title: "OpenVPN"
date: 2005-06-07
forum: General Help
---

### Post by pilate on 2005-06-07
I am having the hardest time trying to get OpenVPN installed! So far this is what I've done and the wall that I've hit:
[I]dpkg the openvpn .tar, ./configure- LZO library and headers not found
apt-get install openvpn- can't find the directory where it was installed to which means I can't start working on it[/I]
New problem.
I've found out that apt-get has installed open VPN correctly. So I moved on to the next step which is setting up your own Certificate Authority. In this step it has you edit a vars file then enter the following commands:
> . ./vars
./clean-all
./Build-ca

All is well until ./build-ca where I get and error saying "openssl:command not found". To top it off the only place I can find this vars file is in the "examples" directory and I'm not so sure that's where it's supposed to be.

I'm using this guide for reference:
[http://openvpn.net/howto.html#pki](http://openvpn.net/howto.html#pki)

I'm using hoary, and if you didn't already gather am a linux newb. I've tried read any guide I could get my hands on and so far, no luck. 
So would someone be so kind as to help me?

---

### Post by blueplazma on 2005-06-07
Why don't you just apt-get it?  I think it's in universe.

---

### Post by pilate on 2005-06-08
actually I did apt-get it. If you'll notice I've edited my post and put up a new problem.
Also I just noticed that I posted this in warthog and not hoary. Sorry for that. would someone mind moving it perhaps?

---

### Post by sgenchev on 2005-06-08
The examples directory is the right place to be for those files. In a perfect world you would have your own certificate authority elsewhere, disconnected from the network, powered down and burried 20 feet underground :-). You would create your certs there and just move them to your openVPN server on floppy/USB stick/whatever.
 Actually, from security perspective it is a Very Bad Idea to keep CA on the openVPN box - that's why these scripts are just provided to you as examples.
 Since OpenVPN does not need OpenSSL to operate, it does not depend on it package-wise. The example scripts do call openssl though so if you want create certs on this box, you need to get openssl: 
 apt-get install openssl
 I suspect it may not be in main - there are some weird licensing/GPL issues with it but if so, it is certainly in (uni|multi)verse.

 A suggestion: if you do want to have your CA on the OpenVPN box - and most home users would probably have to - keep keys that server does not need to operate  i.e. CA private key, generated client keys etc. - on encrypted filesystem and only mount it when  you need to create/revoke a cert. Look at [http://www.ubuntulinux.org/wiki/EncryptedFilesystemHowto](http://www.ubuntulinux.org/wiki/EncryptedFilesystemHowto) and creale a little filesystem-in-a-file

---

### Post by pilate on 2005-06-08
That was exactly the problem sgenchev. Thank you for your help!

---

### Post by psypher on 2005-09-18
for a bridge mode vpn go here: [http://openvpn.net/wiki/Bridged_Mode_OpenVPN_Server_on_Debian_HOWTO](http://openvpn.net/wiki/Bridged_Mode_OpenVPN_Server_on_Debian_HOWTO)

i followed this to a T and I got it working no problem.(except apt-get bridge-utils instead of bridgeutils) I needed bridge mode to play lan games that rely on broadcast traffic. I got it working tonight and have yet to test out BFME. But I am pretty positive it works as I could see my workgroup from a client vpn connection without any hassle. This will not work with traditional VPN's. 

As a windows client I used OpenVPN Gui for Windows [http://openvpn.se/](http://openvpn.se/) and that just worked. Instead of copying my client keys and config files into /etc/openvpn it went into c:\programfiles\openvpn\config. right clicked openvpn gui, connect and it connected, waited 3 minutes and could see my server side workgroup and could browse all the shares at quite a pleasant speed. connection was between 2 - 512 adsl's and got 40k d/l from server

the config isn't that much different with normal route mode. but route mode is all that most people need. like I said I needed bridge mode for games and workgroup browsing.  just create tun's instead of tap devices and skip out the bridge-utils sections. edit the openvpn init script to not load in bridge mode as well

have a quick look at the openvpn howto on the home page just to gget an idea of how it works.

---

