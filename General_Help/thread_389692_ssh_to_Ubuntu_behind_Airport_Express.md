---
title: "ssh to Ubuntu behind Airport Express"
date: 2007-03-21
forum: General Help
---

### Post by russbuss on 2007-03-21
So I seem to be having problems gaining external access to my Ubuntu machines (both running 6.10).  I am using an Airport Extreme as my wireless router and I know that I have a functioning openssh-server on my Ubuntu machines; I can locally ssh into them.

I have a dynamic dns service running to keep the external IPs updated, but if I use the dynamic address (i.e. myname.dyndns.org) I get:

ssh: connect to host myname.dyndns.org port 22: Connection refused

I **can** ssh into an Apple laptop I have behind the same Airport using its dynamic address (i.e. mac'sname.dyndns.org), so I know that the Airport Extreme can do this.

I attempted to set up port mapping for my Ubuntu machines on the Airport Extreme because I read a forum post that intimated that this might help.  However, either this didn't work I didn't set it up properly.  Basically, I set public port 22 to map to private port 22 for a given IP address (i.e. 192.168.1.X) that I knew one of my Ubuntu machines had been assigned (i.e. I checked via ifconfig just before changing the port mapping).

Anyone out there know what my problem might be?

Thanks in advance.

---

### Post by scxtt on 2007-03-21
you can only ssh to one ssh-server on the network ... your router can only forward port 22 to one place ...

so ssh into your apple, then ssh from the apple to ubuntu (or vice-versa), but not both ... unless you change the port that ssh uses on ubuntu ...

you could probably map some random port (let's say 1111 externally to 22 internally) and forward that to ubuntu - not sure, never tried it ... that's UPnP on my linksys router ...

---

### Post by russbuss on 2007-03-21
> **scxtt said:**
> you can only ssh to one ssh-server on the network ... your router can only forward port 22 to one place ...

so ssh into your apple, then ssh from the apple to ubuntu (or vice-versa), but not both ... unless you change the port that ssh uses on ubuntu ...
.

I never had more than one port map set for port 22.  I tried to forward the two different IPs I got for my Ubuntu machines independently.

And I would love to just ssh into the Mac, but the Ubuntu machine stays at home and the Mac comes with me to the lab.  Thus, the desire to be able to ssh externally to Ubuntu.

Thanks for the help, though!

---

### Post by scxtt on 2007-03-21
i don't get what you're trying to say w/ the "I never had more . . ." statement ...

i think you need to more clearly define your goal here ... do you ALWAYS want to ssh into the ubuntu box and SOMETIMES ssh into the apple?

is it really such a big deal to have 1 box that handles ssh requests from your router, then you ssh into any other host on your network from it?  that's really the easiest solution ...

but really, any modern router should have at least a few UPnP-like entries open which will allow you to use a different port, then forward that port to port 22 on ubuntu ...

---

### Post by russbuss on 2007-03-21
> **scxtt said:**
> i don't get what you're trying to say w/ the "I never had more . . ." statement ...

Sorry if I was unclear.  That statement was in response to your advice about being able to only forward Port 22 to one place.  Basically, what I meant was that I never tried to forward Port 22 to more than one place.

> 
i think you need to more clearly define your goal here ... do you ALWAYS want to ssh into the ubuntu box and SOMETIMES ssh into the apple?

is it really such a big deal to have 1 box that handles ssh requests from your router, then you ssh into any other host on your network from it?  that's really the easiest solution ...

Again, sorry for being unclear.  I always want to ssh into the same computer, namely my Ubuntu machine that stays at home.  I mentioned that I could externally ssh into my Mac simply to indicate that my router wasn't broken or some other such nonsense...

> but really, any modern router should have at least a few UPnP-like entries open which will allow you to use a different port, then forward that port to port 22 on ubuntu ...

I am unfamiliar with UPnP, so bear with me if I sound clueless....  But if I got this to work I would ssh to a specific port (i.e. not port 22, but say 111111) and then the router would forward it to port 22 on whichever computer I tell it to?  If I am correct, I'll try to find out if the Airport can do this.


Thanks for the help.

---

### Post by scxtt on 2007-03-21
> Sorry if I was unclear. That statement was in response to your advice about being able to only forward Port 22 to one place. Basically, what I meant was that I never tried to forward Port 22 to more than one place.ok, i just didn't want you to be under the impression that that was possible ;)
> Again, sorry for being unclear. I always want to ssh into the same computer, namely my Ubuntu machine that stays at home. I mentioned that I could externally ssh into my Mac simply to indicate that my router wasn't broken or some other such nonsense...ok, but getting back to the above idea, if you're forwarding to your  mac, you CAN'T forward somewhere else @ the same time ...
> I am unfamiliar with UPnP, so bear with me if I sound clueless.... But if I got this to work I would ssh to a specific port (i.e. not port 22, but say 111111) and then the router would forward it to port 22 on whichever computer I tell it to? If I am correct, I'll try to find out if the Airport can do this.yes, this type of forwarding will allow you to connect via ssh, specifying a different port for the router, and then have that port x-late to port 22 on ubuntu ... so if you forward xternal port 1111 to internal port 22 to ubuntu, it'll connect ... i've tried this, and it works for me ...

ssh -p 1111 $user@$host

then my router will forward requests on port 1111 to my ssh server on $host listening on port 22 ...

---

### Post by russbuss on 2007-03-21
> **scxtt said:**
> 
ok, but getting back to the above idea, if you're forwarding to your  mac, you CAN'T forward somewhere else @ the same time ...

OK, now I see why you were confused by what I've been rattling on about.  I don't have to set up port mapping for my Mac; for some reason the Airport just knows to forward stuff to port 22.  The only port mapping I need to set up is for my Ubuntu machines.

Incidentally, I think that I have finally succeeded in getting the port mapping to work for one of my Ubuntu machines.  So this is fantastic.  Thanks for the help.

> 
yes, this type of forwarding will allow you to connect via ssh, specifying a different port for the router, and then have that port x-late to port 22 on ubuntu ... so if you forward xternal port 1111 to internal port 22 to ubuntu, it'll connect ... i've tried this, and it works for me ...

ssh -p 1111 $user@$host

then my router will forward requests on port 1111 to my ssh server on $host listening on port 22 ...

This sounds like it would be even better, but I still need to determine whether the Airport supports this.

Again, thanks for all the help.  Even if I can't do this with my Airport, at least I can ssh into my primary machine at home!  Word!

---

### Post by scxtt on 2007-03-21
i'll admit i know about --> <-- that much about macs :p ... but i don't know that i'd want SSH autoforwarded (and w/ no way to disable that?) ... but i'd imagine Apple put the right amount of thought into it and it's not a wide open "hole" (using the term loosely) ...

glad you're all sorted for now tho - that's great :)

---

