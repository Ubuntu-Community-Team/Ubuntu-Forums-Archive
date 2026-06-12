---
title: "[SOLVED] WebMin access denied on allowed IP"
date: 2007-10-28
forum: General Help
---

### Post by Hopworks on 2007-10-28
I have Ubuntu Feisty 7.04 Server configured as a LAMP, and everything works great except one little annoying webmin quirk.

I have Webmin installed, and I can access it just fine using my wireless connection. My wireless IP is static and different than my wired ethernet connection static IP,. I added that wired IP address in Webmin

Webmin Configuration/IP Access Control/Allowed IP addresses

but I still get access denied when I try to access webmin. I've restarted webmin, even rebooted. The address is there plain as day, and I double checked the IP of my wired connection. They match, but still access denied.

Both the wired and wireless are on my laptop, using the same browser, the same bookmark I created.

Is there another place I should be looking to allow that wired IP address? Every machine I have on my LAN has a static IP, and all of the ones I put the IP address into webmin can access webmin except that one IP.

Thanks for your time.

Hop

EDIT: I checked /etc/webmin/miniserv.conf allow= to see if the IP is there, and it is. It isn't even at the end of the list, or the beginning, but almost in the middle.

---

### Post by Hopworks on 2007-10-28
Fixed!
I KNEW there was another place I needed to look in Webmin to fix this.
I googled this a lot and didn't find this answer, so I'll put it here in case someone else runs into this problem.

The problem was, even though I had the correct IP addresses in the allow= line of /etc/webmin/miniserv.conf, I couldn't connect and received "ACCESS DENIED" from a certain IP in that list. That made no sense to me, so I looked at more Webmin options, and fixed it by updating the list of IPs a user is allowed to log in from, at
(in the Webmin interface) Webmin/Webmin Users/(username)/Edit Webmin User/IP access control.

Once I did that, I can connect from the wired IP I mentioned above in this thread.

I don't know if it is a bug, but I don't understand why access denied would happen BEFORE a username and password was even prompted if the reason was because IP access control for a user didn't have the requesting IP address in there. Maybe it is a cookie thing, but I'm not going to explore that because it is working for me now.

Hop

---

