---
title: "SSH port forwarding"
date: 2013-10-16
forum: General Help
---

### Post by 8RDRrAR on 2013-10-16
[COLOR=#282828][FONT=helvetica]Let me start by explaining the goal. I am at my university and I would like to reverse ssh to connect to certain services remotely. I have an EC2 instance that is acting as my server.[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]On to the problem. When I ssh to my server like this:[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]ssh -R 9091:localhost:9091 [username]@[serverip][/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]and at the same time configure firefox and do this:[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]ssh -D 8080 [username]@[serverip][/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]I can connect to the service running on localhost:9091. However when I point my web browser to [serverip]:9091 with no proxy I get nothing. If someone could explain what I am doing wrong that would be wonderful. [/FONT][/COLOR]

---

### Post by TheFu on 2013-10-16
I';m pretty good with ssh and port forwarding, but after reading your post twice, I don't understand what you are trying to accomplish. Could you clarify please?

---

### Post by papibe on 2013-10-16
Hi 8RDRrAR.

It looks like you are trying to access transmission-daemon (because of the port 9091).

If so, note that by default you can only access the transmission's webui from localhost. In order to enable access remotely, you need to edit the config file located:
```
/etc/transmission-daemon/settings.json
```
then you need enable the white list by changing this field to 'true':
```
"rpc-whitelist-enabled": true
```
and then either add your client IP, or use wildcards to accept connections from anywhere:
```
"rpc-whitelist": "*.*.*.*"
```
Hope that helps. Let us know how it goes.
Regards.

---

### Post by markbl on 2013-10-16
OP, it seems you are trying to do 2 unrelated things there but confused them together. If you want to access the transmission web server (as papibe suggests?) remotely from Uni, then you need a local port forward from client to your server, not a remote port forward which goes the other way. So from Uni:
```

ssh -L9091:localhost:9091 [username@]serverip

```
(i.e. -L, not -R). And then point your browser on your Uni pc to [http://localhost:9091](http://localhost:9091).

Completely separate to this, if you want to tunnel all your Uni pc web traffic via your server (e.g. to get around Uni web blockers etc), then you can use ssh dynamic proxy:
```

ssh -D 8080  [username@]serverip

```

Then configure your Uni PC browser to use a socks proxy on port 8080 to route all web pages etc.

Of course you can add the -D and -L options together to do both functions via the one ssh session (note that the socks proxy will not intercept localhost requests). Also, if you Uni PC is running Windows then you need to configure the equivalent ssh commands above in PuTTY etc.

---

### Post by 8RDRrAR on 2013-10-18
Ok to clear things up here the goal is to have my server redirect all traffic coming in on a specific port to a machine behind a firewall. The idea I had was to use a reverse ssh connection and pass the traffic that way. The reason I have both local and remote listed is because when I tunnel my traffic to the server it does work as I would like it, this however does not quite fit my goal. 

Hope this helps:
This is the idea the cloud server passes all traffic on port 9091 to the Firewalled server (it is transmission for now, but that is only to see if it works. I have another more complex program in mind that uses a similar structure) 
Fire-walled server --Reverse SSH--> Cloud server <--Regular traffic-- Users connecting to my fire-walled sever

This is how it actually works 
Fire-walled server --Reverse SSH--> Cloud server <--ssh proxy-- me connecting to my fire-walled sever

---

### Post by papibe on 2013-10-19
I'm not sure if I'm getting 100% the right picture, but try this:

On the Firewallled-Server:
```
ssh -L 9091:localhost:9091 Cloud-Server
```
Then on the remote client machine:
```
ssh -L 9091:localhost:9091 firewallled-Server
```
Then, in the remote client machine, if you open your browser here:
```
localhost:9091
```
It should work.

What this does is to route transmission's webui from the Cloud-Server to the  firewallled-Server, and then to the remote client machine. Is that it?

Let us know if we are getting closer ;)
Regards.

---

