---
title: "setting static IP address for WD My Cloud"
date: 2015-06-08
forum: General Help
---

### Post by Old Jimma on 2015-06-08
Hi Community:

I bought a WD My Cloud, and I want to change its IP address from a dynamic address to a static address. ;)

It was suggested to be sure to choose an IP address that is above or below your pool of DHCP IP addresses to avoid conflicts. 

I'm not sure what this means. :confused:

Could someone explain it to me and help me learn how I follow those instructions to choose a static IP address that is above or below my pool of DHCP IP addresses? [-o<

Thank you! ):P
Old Jimma

---

### Post by papibe on 2015-06-08
Hi Old Jimma.

A few thoughts:

It would be easier leave the WD as it is, and set a reservation on your DHCP server. If you haven't set up your own DHCP server, most probably your router is doing the job. Go to your router's admin pages, and try to set a reservation for the MAC address (or hostname) of your device. You may learn that your router does not support this function, but you are on the right place because...

The DHCP range should be on your DHCP server, or your router. If you go to the admin pages you should see what range is serving. You want to choose the same network, but outside the range. For instance, if the network is:
```
192.168.1.0
```
and the DHCP range is
```
100 to 254
```
you have available 192.168.1.1 to 192.168.1.99 Also make sure to avoid conflict with other static devices like... you guest it, your own router, which usually is 1 or 254

Does that help? Let us know if you have more questions.
Regards.

---

### Post by Old Jimma on 2015-06-08
Hi Papibe:

I wish I understood enough to follow your directions.

I attached a screenshot of my router. I couldn't find anything you referred to. There is nothing there that says "admin pages." I don't know what a DHCP server is. I have a router.

I think I want the IP address on the My Cloud device to be static because I want to use NFS to access the device and store backups on it.

I'm not sure whether what you propose will allow my to accomplish that.

The specific guide I planned to use is [http://cocoaallocinit.com/2014/01/04/wd-my-cloud-nas-on-ubuntu/]("http://cocoaallocinit.com/2014/01/04/wd-my-cloud-nas-on-ubuntu/")

There was other discussion of that plan at: [http://askubuntu.com/questions/469368/need-help-connecting-wd-my-cloud-nas-to-14-04]("http://askubuntu.com/questions/469368/need-help-connecting-wd-my-cloud-nas-to-14-04")

So, I'm confused by the advice, and wonder if it would eventually lead me to accomplishing my goal.

Thank you,
Old Jimma

---

### Post by papibe on 2015-06-08
...waiting for that screenshot...

Also, could you tell us the brand and model of your router?

Regards.

---

### Post by Old Jimma on 2015-06-08
I have an ATT 3801HGV. I think there is a user guide at [https://hackingbtbusinesshub.files.wordpress.com/2011/11/3801hgv_user_guide_rev-1-0.pdf]("https://hackingbtbusinesshub.files.wordpress.com/2011/11/3801hgv_user_guide_rev-1-0.pdf")

---

### Post by Old Jimma on 2015-06-08
Ahha!!!

I opened my router pages > Settings > LAN 

I attach a screen shot. It says my Private Network DHCP Info has the following range:  	192.168.1.64 – 192.168.1.253

Does that help??

I appreciate your patience.

Sincerely,
Old Jimma

---

### Post by papibe on 2015-06-08
hey! :D

I don't see a way to reserve an IP, so setting the static IP in the device itself is that way to go.

You can set up a static IP in the range: 192.168.1.1 – 192.168.1.63  (usually ATT routers assigned itself to 254).

Let us know how that goes.
Regards,

---

### Post by Old Jimma on 2015-06-08
hi papibe:

Here is what I did:

I chose the static address: 		192.168.1.51

From the router I found:
Subnet Mask: 		255.255.255.0
gateway: 		192.168.1.254

Also, i used the linux command to find the DNS server IP address:

cat /etc/resolv.conf

The DNS IP is 127.0.1.1

I put this info in the WD My Cloud settings > network > static

I'll reboot my router, My Cloud, and computer to see if it worked.

---

### Post by Old Jimma on 2015-06-08
Here is what I found after rebooting my router, My Cloud, and ubuntu computer:

I can type the static address I assigned my cloud using the my cloud software (192.168.1.51) and Firefox opens the My Cloud.

However, my router still things that the My Cloud NAS is still tye dynamic address  192.168.1.79

How do I get my router to think that the My Cloud is 192.168.1.51?

thanks,
Old Jimma

---

### Post by papibe on 2015-06-08
Glad to see you're making progress.

Try to see if you can release the DHCP lease. In your first screenshot there's a 'detail' button next to each device. May be you can release the lease from there.

Having said that, there's a chance that your router won't know your device any more. Your Ubuntu machine and other client machines would access it using its IP address. That would be the standard procedure, unless...

Does your router do local DNS? If that is so, you may not need a static IP.

For instance, could you resolve the IP addresses with just using the hostname? For instance, 'reinhardt' is a machine on my network and this works from every other machine on the network:
```
nslookup reinhardt

ping -c1 reinhardt
```
(since you changed your WD device, test this with other names).

Let us know how it goes.
Regards.

---

### Post by Old Jimma on 2015-06-08
I rebooted everything, and after assigning a static IP at the WD My Cloud Desktop, and assinging it 192.168.1.51, it snapped back to being a dynamic IP, and boy was I glad.

I am beginning to think that I don't need a static IP (or, hoping I don't).

When I come back from putting my mother-in-law in assisted care living next week, I'm going to just use nfs and try mounting it.

Take care. I owe you a beer.

Sincerely,
Old Jimma

---

### Post by papibe on 2015-06-08
If you can access the WD device using its hostname from the Ubuntu machine, you don't need static IP, just the hostname.

Let us know how that goes, and if you need more help.

Regards.

---

