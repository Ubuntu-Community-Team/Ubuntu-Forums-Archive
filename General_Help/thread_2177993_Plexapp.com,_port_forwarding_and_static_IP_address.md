---
title: "Plexapp.com, port forwarding and static IP addresses"
date: 2013-10-01
forum: General Help
---

### Post by Kojak Peg on 2013-10-01
Hi Everyone
I've been trying to connect my computer wirelessly to my smart tv using Plex. However I'm having really problems connecting and on the odd occasion I do it only lasts for a few seconds before timing out.

I think I've worked out what is wrong, namely port forwarding and creating a static IP address. I've been reading up on how to create a static IP and I'm a little reluctant to mess around with it until I'm absolutely sure what I'm doing. The website I've been reading is [http://www.sudo-juice.com/how-to-a-set-static-ip-in-ubuntu/](http://www.sudo-juice.com/how-to-a-set-static-ip-in-ubuntu/) 

However I'll have to use the wireless connection and that is why I don't want to mess about with it until I'm more confident in want I'm doing because I don't want to end up disabling my entire wireless connection
 
So any help and guidance on how to 
make Plex work, or 
do port forwarding, or 
create a static IP address 

would be great, thanks

---

### Post by ian-weisser on 2013-10-01
Hmmm. Port forwarding should be an issue only if you are trying to connect to a machine on your (wired or wireless) LAN from upstream on the internet.

If both devices are on the same wireless network (or both are downstream from the same router), then port forwarding should not be relevant.

---

### Post by Kojak Peg on 2013-10-01
As far as I can make out you log into plex on your computer (mine is connected to the router wirelessly) you then connect your tv (my tv is wired to my router) to plex with a pin number. And then you can stream content from your computer to your tv. However Plex has to connect to your server, but it can't. I've connected twice for a few seconds but then it times out 

So I've done everything I can think of, I've even learnt a load of stuff I didn't know about, tried it all and still Plex won't connect. So I'm at a complete loss now as to how to make Plex work. The only thing I can think of (and it probably doesn't even apply now I'm on linux) is before switching to linux I downloaded a diagnoses program from dell which warned me my system could be accessed remotely so I followed the recommendation and closed the hole. However I can't remember how to do it, or how to reverse it and I'm not sure if it would even be an issue now I'm using linux. So if anyone has any ideas please let me know I'd be most grateful 

In fact does anyone know of another way to connect your computer to your tv, bearing in mind I have to connect wirelessly

Thanks

---

### Post by Kojak Peg on 2013-10-02
Okay I've got it half working. I managed to open a port with port forwarding and Plex is now connecting to my server and I'm able to log on to Plex through my tv as well and see the folders I created in Plex. However when I go into the folders there is no data. So there is obviously still something wrong somewhere, perhaps my static IP is wrong.

update 
I managed to work out port forwarding and static IP addresses and it's easy when you know how. here's a ling to a website which explains it all [http://portforward.com/](http://portforward.com/)

I would mark it as solved but can't find so perhaps the format has changed since I last marked a thread as solved

---

