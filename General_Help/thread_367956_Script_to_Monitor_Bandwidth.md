---
title: "Script to Monitor Bandwidth"
date: 2007-02-22
forum: General Help
---

### Post by black_wolf on 2007-02-22
Hello,

After trying out Ubuntu some time ago, I decided to reinstall it to my desktop to use as a file server and a general try-out-Ubuntu machine.

For the file server part, I installed Hamachi and am using Samba to serve out the files. Occasionally I have a problem where Hamachi doesn't start correctly, or doesn't login to the Hamachi networks but I think I've sorted all of that out.

My problem is that I'm on a university network that has a bandwidth cap on how many GB (10 in this case) can be in/out per IP per 24 hours. Since the files I'm sharing are large (large enough to hit the cap in less than 24 hours), I was thinking that I needed a script that would drop my connection and get a new IP/MAC address whenever my bandwidth got close to 8 GB . 

I don't know very much at all about bash scripting, although I'm assuming that there is a command (something to do with ifconfig) that can tell me how much has been downloaded and uploaded. I'd add those two numbers together to get the throughput, and if that number was above 8 GB then run a command to drop the connection, stop networking, restart networking, and then try to get an IP address (I would also need to make sure that the new IP address isn't the same as the old one). Although I have no idea on how to do that. 

Also, I've already had this computer blocked from the network (by the MAC address) so I have set up the computer to change the MAC address on boot so that I can access the internet.

Could someone point me in the right direction to help out with the bash scripting or with the script itself? I found a script on [Rob Pectol's site]("http://rob.pectol.com/component/option,com_wrapper/Itemid,61/") that displays the up and down bandwidth since the adapter has been up, but I only need it to be concerned about a 24 hour window. I tried to modify the script but since I don't know much about bash I'm clueless. 

Any help is appreciated, thanks.

---

### Post by mr.v. on 2007-02-22
First thing I'd say is that you're probably going to have a problem because it sounds like you're getting your ip address from a DHCP server (unless I'm wrong with my assumption). If the DHCP server is even marginally competent in the network architecture, even if you release your connection and request a new one, you're likely to get the same ip address with the same used bandwidth quota.

As far as bash scripting goes, what you want to do will require knowledge of command execution and string processing. It's not impossible but it'll take you a bit to learn what you need. A good place to start is the linux documentation project at tldp.org
[http://www.tldp.org/guides.html](http://www.tldp.org/guides.html)
and go through the Bash Guide for Beginners and then the Advanced bash-scripting guide
if you go through both you'll be a scripting ninja =)

---

### Post by black_wolf on 2007-02-22
Yes, you are correct I'm on DHCP, which complicates things. Thanks for your advice, I'm going to look up tldp and see where I can go from there. Thanks for your help.

As far as the ninja part goes...I'm going to try to be fast...fast like a ninja.

---

### Post by Vil on 2007-03-10
I would think the DHCP server would have a lease time of a day or so, and, if memory serves, they base the given IP on the MAC address, so shouldn't changing MAC addresses before requesting the new IP address give you a different IP?

---

