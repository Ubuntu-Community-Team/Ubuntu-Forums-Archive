---
title: "advice,help,tips..."
date: 2012-11-10
forum: General Help
---

### Post by prodrumernate on 2012-11-10
1.i have been working with ubuntu for a couple years.got real serious lately.stopped fora while then got back into it...

2.please move this to the correct category if it is not correctly placed.not sure where to post this at.and i currently have a head ache..

i have created a home webserver using ubuntu.i have all my files in my var/www/(sitnames) folders. i can access them through my local network using the ip number and site name i created.

my ISP is centurylink.im using zyxel Q1000Z modem/router. i use a separate computer for my server.it is only a server computer.

i currently forwarded ports 80,22,443..

now to the point...once i buy a domain name.how do i set the ip address and my modem/router to allow outsiders to access my website using my domain name and how do i set it to direct to my domain name?if that makes any sense.

thank you in advance for the help.and i know this has been asked several times.currently using most recent ubuntu OS with GUI.

and having a video or picture description would work a lot better for me as well as text.(im ADHD so i cant sit and read very long or kinda get ahead of reading looking for the main points)oh and if i could afford to go through like goddady i would for hosting.but id rather save the money and do it from my own home since i have tons of computers and want to learn more about servers etc...

by the way its a fish forum.nothing fancy.just another place like many on the web for getting help with fish and aquarium help/advice.

---

### Post by Merrattic on 2012-11-10
Do you have a fixed IP address (the internet one, not inside your home network)? If so, when you buy your domain you just point it at that IP. If you don't have a fixed IP, you can still do this, and just hope that when the dhcp lease expires you are reassigned with the same IP. Alternatively (and depending on the amount of traffic you generate) you can use a service such as dynds.org which keeps track of your IP. This could save you having to buy a domain.

Now then, if you are going to open up your server  / pc to the world you will need to think about security. Suggest you have a good read of ubuntu wiki on servers and security.

Have fun

---

### Post by prodrumernate on 2012-11-10
> **Merrattic said:**
> Do you have a fixed IP address (the internet one, not inside your home network)? If so, when you buy your domain you just point it at that IP. If you don't have a fixed IP, you can still do this, and just hope that when the dhcp lease expires you are reassigned with the same IP. Alternatively (and depending on the amount of traffic you generate) you can use a service such as dynds.org which keeps track of your IP. This could save you having to buy a domain.

Now then, if you are going to open up your server  / pc to the world you will need to think about security. Suggest you have a good read of ubuntu wiki on servers and security.

Have fun

i actually dont have a fixed IP address..that is 1 thing im trying to figure out how to setup.i mean i have my modem ip address and a dns on it..i believe with the modem i have it makes hosting websites a lot easier.but im not sure how to set it up exactly using it..

ive been reading a little up on security.i actually plan on maybe hosting 1 month or so through godaddy as a means to get the ad search service they give when buying hosting plans.and once my site has enough users and i have learned enough about the security settings then ill switch it over to my home server.i use filezilla to upload files to it from my other computers in my network so i have backups on them.

---

