---
title: "Automated Port Forwarding Through Several Servers"
date: 2008-01-14
forum: General Help
---

### Post by Ramorous on 2008-01-14
Here is the scenario.

- I have a client network that is to have LDAP. Lets call the client LDAP Master "CLD" (Client LDAP)
- I have a network that currently has its own LDAP Master. Lets call this one "LLD" (Local LDAP)
- The plan is to push the LLD to the CLD so the CLD can serve its own directory to its network and have information populated by the LLD.
- We've worked out the kinks on how to get that done. However, we want things to be a little more secure.
- What I would like to know if there is a service or script already in place that will allow automated SSH Tunnels from LLD to CLD.

* We have several hops to go through to get to the client network. We can accomplish this with password-less authentication.
* My main problem is how can I go about automating the SSH tunnels so that there are checks to see if the tunnel is up for that one port. 

Cheers.

---

