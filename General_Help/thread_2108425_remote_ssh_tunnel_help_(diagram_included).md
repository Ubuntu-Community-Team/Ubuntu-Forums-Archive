---
title: "remote ssh tunnel help (diagram included)"
date: 2013-01-24
forum: General Help
---

### Post by Scotty562 on 2013-01-24
What I want to do is set a slingbox up for my parents so they can access it from their phones / ipad ect. Their internet is in the form of an unlimited 4G data connection provided through Verizon. Verizon 4G only hands out 10.x.x.x addresses so simply forwarding a port isn't an option. They also offer a static ip for $500, but that's a last resort kind of option. Also, I realize the performance is going to suffer by going through a ssh tunnel.

Below is a diagram of my setup.

I have an ssh server on PC1 (my house) and PC2 (my parents house). PC2 is able to create an ssh tunnel to PC1 and then PC1 is able to make a tunnel to PC2. Fantastic. Where I'm hung up is actually accessing the slingbox from PC1 and eventually from anywhere in the world via my 75.x.x.x router. I'm assuming it's just a few forwarding ports, but everything I've found is so confusing I don't even really know where to start.

I also want to note I have local and remote forwarding setup on both ssh servers until I figure out what I don't need.

I think [http://www.noah.org/wiki/SSH_tunnel#simple_port_forwarding_.28SSH_tunneling.29](http://www.noah.org/wiki/SSH_tunnel#simple_port_forwarding_.28SSH_tunneling.29) explains what I want to do under "Tricky reverse forwarding" but it's not explained well enough for me to recreate it.

[IMG]http://i.imgur.com/uHAha6P.jpg?1[/IMG]

---

### Post by Crafty Kisses on 2013-01-24
You might want to look into FreeNX w/ a reverse SSH tunnel to achieve your goal. This seems to be what you're looking for

```

                    +-------+                   +--------+
                    |       |                   |        |
                    |       |                   |        |
 +-------+          |       |                   |        |                    +----------+
 |       |          |       |   traffic type:   |        |                    |          |
 |       | traffic: |       |   NX "protocol"   |       +-------+traffic type:| remote X |
 |       |    X     |local  | (internet, modem) |remote |nxagent| X protocol  | applicat.|
 |local X|<-------->|nxproxy|<----------------->|nxproxy| 
    <-------------->|(or compl.|
 |display|          |       |    "roundtrips"   |       |       |             | KDE/GNOME|
 |       |          |       |   close to zero   |       +-------+             |  session)|
 |       |          |       |                   |        |                    |          |
 +-------+          |       |                   |        |                    +----------+
                    |       |                   |        |
                    |       |                   |        |
                    +-------+                   +--------+
                    decompression              compression
                    +caching                   +caching
```

---

### Post by Lars Noodén on 2013-01-24
So for clarification, you can only access PC2 via a reverse tunnel it makes to PC1?

You can chain together tunnels, so if you also make one from PC2 to Slingbox, you should be able to ssh to the forwarded port on PC1 and have it carried forward to Slingbox.

---

### Post by Lars Noodén on 2013-01-25
Ok.  I can't make a net with quite the same topology but here's one guess any way.  You can make the reverse tunnel from PC2 to PC1 forward over to Slingbox.

On PC2 make the tunnel to PC1 with forwarding to slingbox:

```

ssh -R 2224:192.168.1.10:22 scotty562@75.x.x.x

```

Then from elsewhere in the world, connect to port 2224 on PC1 which is really port 22 on slingbox.

```

ssh -p 2224 scotty562@75.x.x.x

```

---

### Post by Scotty562 on 2013-01-25
Thanks for your help guys. I ended up figuring it out. I only needed one SSH server as well which is cool.

I used logmein to connect to PC2 and then used putty to ssh into PC1. I setup a remote port of 192.168.1.10:5001 and then hit connect. I then forwarded the the slingbox port to PC1, tried it, and life was good.

I honestly couldn't believe it worked the first time!

---

