---
title: "File Download Restrictions"
date: 2008-05-12
forum: General Help
---

### Post by CollisionInc on 2008-05-12
I am currently installing two systems with Xubuntu.
They will be used purely for browsing the internet but I would like to know how to block/restrict the downloading of certain file types/sizes etc.

I would pretty much like to Lock Down the desktop so all the users have access to is Open Office and Firefox. I see there is Lockdown Editor on Ubuntu but this has limited options.

I have searched using various search terms:

file download restrictions etc but have not come up with an answer.

Any Advice??

---

### Post by Monicker on 2008-05-12
You can impose download restrictions by forcing users to go through a proxy, such as squid, and having the proxy enforce them with its acls.

---

### Post by CollisionInc on 2008-05-12
> **Monicker said:**
> You can impose download restrictions by forcing users to go through a proxy, such as squid, and having the proxy enforce them with its acls.

There are two other machines on the network that dont need to be restricted however they are all connected to the Broadband Router.
Is there a way round this other than an App that can be installed on the machines?

---

### Post by Monicker on 2008-05-12
The proxy server would be separate from the workstations, not installed on them.  Well, actually could install squid on each station and do it, but the purpose of a proxy server is to be a central point for cachine and controlling access to web sites.

As far as doing that just at the workstation level without a proxy, I don't know.

---

### Post by CollisionInc on 2008-05-12
> **Monicker said:**
> The proxy server would be separate from the workstations, not installed on them.  Well, actually could install squid on each station and do it, but the purpose of a proxy server is to be a central point for cachine and controlling access to web sites.

As far as doing that just at the workstation level without a proxy, I don't know.

Well since the machines will have one purpose I suppose i can install Squid on each one then. Sounds like overkill but then again if it works thats fine by me.

Thanks Muchly for the Advice

---

