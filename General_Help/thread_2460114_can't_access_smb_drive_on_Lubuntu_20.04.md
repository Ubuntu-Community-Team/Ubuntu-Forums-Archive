---
title: "can't access smb:// drive on Lubuntu 20.04"
date: 2021-04-02
forum: General Help
---

### Post by Brent_Santin on 2021-04-02
Hi,

My internet provider (Bell Canada) supplies a modem/router for my house. On the side of it are USB ports you can plug a drive into and use it to share files across any device on the network.
Up until recently, everything was straightforward. My Blu-ray player, Android TV box, Android phone, Lubuntu 18.04 laptop and Lubuntu 18.04 desktop could all access the shared USB drive by typing the following into the address bar of a file browser:

smb://192.168.2.1/

I recently upgraded to a new desktop computer and installed Lubuntu 20.04. With this computer I cannot access that address. Instead I get the following error messages.

"Failed to retrieve share list from server: Software caused connection abort"
"The specified location is not mounted".

I've Googled around for the answer to this, but not found anything that was basic enough for me to follow or seemed to apply to my situation.

I was hoping someone here could help me determine what is going on and how to fix it.

From what I've learned, this has something to do with Samba file sharing, which interfaces Windows and Linux computers. Does that mean my router is running some version of Windows?

Thanks.

---

### Post by TheFu on 2021-04-02
Morbius1 has posted many answers in these forums. I'd guess it is an NT1 deprecated protocol problem on the 20.04 Samba, but I don't know. It was deprecated for security reasons, so you should look at other solutions like using a newer SMB protocol from the client devices, NFS or running a DLNA server for media streaming needs inside your home.  

miniDLNA, Plex, JellyFin are DLNA options worth considering.  No need for a paid client or any accounts unless you want access from outside your home LAN.

I've seen that with samba issues, one of the first questions is to run **testparm** on the samba server, and post the output here. That provides all the current settings as interpreted by samba.

---

### Post by Brent_Santin on 2021-04-02
> **TheFu said:**
> I've seen that with samba issues, one of the first questions is to run **testparm** on the samba server, and post the output here. That provides all the current settings as interpreted by samba.

Okay, I'm assuming the samba server in this case is the router (know very little about networking). Not sure how I run testparm on the router since it is not a real computer.
Can I do that from my desktop and target the tesparm program so it tests the router?

---

### Post by ActionParsnip on 2021-04-03
Have you tried rebooting the router? It is just another computer after all. Can help

---

### Post by TheFu on 2021-04-03
> **Brent_Santin said:**
> Okay, I'm assuming the samba server in this case is the router (know very little about networking). Not sure how I run testparm on the router since it is not a real computer.
Can I do that from my desktop and target the tesparm program so it tests the router?

Ah - I missed that. Sorry. I clearly didn't read carefully enough.
SMB1 / NT1 protocols are security liabilities, especially in a router.  In general, it is a bad idea to use a WAN router as a storage provider.  Most routers with this feature have been hacked and should be replaced.  Linksys, d-link, tp-link, netgear, Asus, Zyxel have all been hacked. Any storage connected to them was available on the internet.  I can't say anything about the exact router provided by your ISP. In general, ISPs don't do a great job keeping CPE - customer premise equipment - patched.  If nobody complains, that's their goal.  
[https://securityledger.com/2019/08/huge-survey-of-firmware-finds-no-security-gains-in-15-years/](https://securityledger.com/2019/08/huge-survey-of-firmware-finds-no-security-gains-in-15-years/) will open your eyes.

[https://askubuntu.com/questions/1265923/configuring-20-04-samba-for-smbv1](https://askubuntu.com/questions/1265923/configuring-20-04-samba-for-smbv1) says to modify the /etc/samba/smb.conf file on any client to say:
```
client min protocol = NT1
```
Make certain that really is what you want.  SMB2 and SMB3 are much more secure AND faster.

---

