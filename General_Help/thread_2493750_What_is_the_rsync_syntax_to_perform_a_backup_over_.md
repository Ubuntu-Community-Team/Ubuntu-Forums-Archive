---
title: "What is the rsync syntax to perform a backup over a VPN tunnel ?"
date: 2023-12-23
forum: General Help
---

### Post by freeflyjohn on 2023-12-23
What is the rsync syntax to perform a backup over a VPN tunnel ?

I have tried the following...

```
rsync user@192.168.3.1:/media/vpntest /home/vpntest/
```

But nothing happens, so I press CTRL-C it gives the following error...

```
^Crsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(713) [Receiver=3.2.7]
```

I have setup a Wireguard VPN using this guide...

[https://www.cyberciti.biz/faq/ubuntu-20-04-set-up-wireguard-vpn-server/](https://www.cyberciti.biz/faq/ubuntu-20-04-set-up-wireguard-vpn-server/)

The Wireguard server is running on my Dell T30 Ubuntu server and the Wireguard client is running on an iMac.

The VPN seems to work because:

1. From the client (iMac) I can ping the VPN server IP address 192.168.3.1 
2. From the client (iMac) I can SSH into the server and see its files etc.

I'm hoping the problem is just a syntax with rsync ?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293242&stc=1[/IMG]

---

### Post by MAFoElffen on 2023-12-23
The syntax looks okay. It may help to add "--verbose" for help debugging that...

What is the local address? If in a different net address range, it there a net route between them?

---

### Post by freeflyjohn on 2023-12-23
Thanks MAFoElffen

> **MAFoElffen said:**
> The syntax looks okay. It may help to add "--verbose" for help debugging that...

I tried adding --verbose but the outcome was the same (nothing happened so I had to press CTRL-C)

> **MAFoElffen said:**
> What is the local address? If in a different net address range, it there a net route between them?

Are you referring to the VPN address, or the local IP address of the machine ?

As the iMac is 100 miles away, I am initially using wireguard VPN on a virtual machine (Parallels Desktop) which is running on my Mac Book Pro.

I can ping and ssh in the same way I can with the iMac

The idea is to get it wokring on the Mac Book Pro Ubuntu VM, before trying it on the iMac

I dont know anything about the net address range or net route ? I ran 'ip address' on each machine in case that helps

---

### Post by The Cog on 2023-12-23
The rsync syntax does not change. rsync would be completely unaware that there is a vpn involved.It just connects to another IP address. 
If "nothing happens", you are probably just not waiting long enough for the connection timeout failure.
You can test connectivity with this command which will timeout after 3 seconds (I assume you put the right IP address in):
```
nc -vzw3 192.168.3.1 22
```

---

### Post by MAFoElffen on 2023-12-23
Yes. Curious. 

rsync "uses" ssh to connect to a remote connection. Usually if you get an ssh connection then everything should work for rsync.

If I am having a time trying to debug a cannection, sometimes I'll do this...
```

rsync -e "ssh -v" -avz remote:~/file

```
I have noticed when doing some remote ssh and rsync to OSX hosts...

That sometimes it's an issues with quarts on the OSX machine. If that is an issue with X Forwarding... then I'll pop over an shh session with it, and edit the ~/.ssh/config... and check to see if "ForwardX11 no" is there and uncommented. If I have to change that, I'll restart ssh/sshd on the remote... Then try again.

Since you mentioned OSX, you might check for that.

---

### Post by The Cog on 2023-12-23
OK, you put a lot of info up while I was writing my last reply. In the light of that new info:
Yes, the IP address 192.168.3.1 looks correct. Can you can ping 192.168.3.1 from the laptop? Can you ssh to it?

---

### Post by freeflyjohn on 2023-12-23
Thanks all, I found the problem and fixed it.

The issue was because I am not using the default port for ssh (i.e. port 20), I have changed it to something else to increase security.

So I need to include the ssh port in the syntax as follows...

```
 rsync -a -b --rsh='ssh -p xxxx' user@192.168.6.1:/media/vpntest /home/vpntest/
```

rsync ran and copied the file in the test folder, so the next thing to try is running it on the iMac.

---

### Post by freeflyjohn on 2023-12-23
On a seperate topic (I was going to make a new post)... when I installed wireguard by following the guide, I was unable to ping the server from the client.

The only way I could get it to work was to open port 41194 on my router and then everything worked.  

But this is not mentioned in the guide, so I'm unsure if this is the correct thing to do and whether its secure and safe ?

---

### Post by The Cog on 2023-12-24
I presume that's the port that the wireguard tunnel is using. You have to let that through. It's safe - wireguard won't even respond to any packets that are not encrypted with your secret key.

---

### Post by freeflyjohn on 2023-12-24
> **The Cog said:**
> I presume that's the port that the wireguard tunnel is using. You have to let that through. It's safe - wireguard won't even respond to any packets that are not encrypted with your secret key.

Thanks The Cog

Yea that’s correct, it’s the port that’s defined in the WireGuard config file as shown in the installation guide…

```

## Set Up WireGuard VPN on Ubuntu By Editing/Creating wg0.conf File ##
[Interface]
## My VPN server private IP address ##
Address = 192.168.6.1/24
 
## My VPN server port ##
ListenPort = 41194
 
## VPN server's private key i.e. /etc/wireguard/privatekey ##
PrivateKey = eEvqkSJVw/7cGUEcJXmeHiNFDLBGOz8GpScshecvNHU=
```

Strange how it’s not mentioned in the guide that you have to open the port on the router. It just says to ping the server but this didn’t work unless I opened the router port.

---

### Post by MAFoElffen on 2023-12-24
Just a thought. 

Maybe you might want to mention that to the author of that guide... Them updating that guide with that may help others who might follow that.

---

### Post by freeflyjohn on 2023-12-24
> **MAFoElffen said:**
> Just a thought. 

Maybe you might want to mention that to the author of that guide... Them updating that guide with that may help others who might follow that.

Yeh I’ve already left a comment at the bottom of the page asking the question. Just keeping an eye on it to see if I get a response.

---

