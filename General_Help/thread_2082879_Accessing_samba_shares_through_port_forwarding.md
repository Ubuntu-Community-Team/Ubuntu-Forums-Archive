---
title: "Accessing samba shares through port forwarding"
date: 2012-11-10
forum: General Help
---

### Post by Stephan H on 2012-11-10
Hello Forum,

I got a few questions as I'm setting up a machine to function as a NAS / backup / remote access.

1. In "system settings" under "sharing" one can set a standard user name and password. When would I get prompted for it?

2. I can access samba shared folders in the local network. But it promts for user details. The standard name/PW doesn't work (as in 1.), what is it asking for? Local profile details of the other machine?

3. I'd like to port-forward the whole machine using a static IP. Ideally the user should see a profile login prompt using the IP in his browser. But it doesn't work. 
The machine got a fixed IP assigned from the router, a port is forwarded to the local IP and I can acces an IP cam this way too (though here I'm using dyndns). The provider IP is static, so typing 123.456.678:xxx should take you to the machine with a profile promt.
What's wrong? The connection just doesn't work, it times out.

Would be great if some idead could be shared about it here.

Stephan

---

### Post by mikewhatever on 2012-11-10
1. When you try logging into that machine remotely, in other words, from another device.

2. It asks for a valid samba user, usually, a local user on the machine that runs the Samba server.

3. Something must be wrong with the port forwarding rule. Need more details to answer that.

---

### Post by Stephan H on 2012-12-09
> **mikewhatever said:**
> 1. When you try logging into that machine remotely, in other words, from another device.

2. It asks for a valid samba user, usually, a local user on the machine that runs the Samba server.

3. Something must be wrong with the port forwarding rule. Need more details to answer that.

Hello,

So what should one get when one contacts a local machine through port forwarding?
I've got an IP cam and did it exactly the same way.
I left DHCP on the local machine but gace this machine a fixed IP on the router (MAC filtering). It does get the same IP all the time. If I set a fixed IP on the local machine, it won't connect to the router at all
For this one I then forwarded a port and got a no-ip.org dynalic DNS (even though the IP is static and couldf only chenge if the router gets switched off).

Do I see this correctly that Samba does not need to be involved here at all?
I made three user profiles (plus root admin) to which I was hoping users would just get access from outside the LAN.

Stephan

PS: I changed the subject slightly but left it here for the context. Did not open another thread...

---

