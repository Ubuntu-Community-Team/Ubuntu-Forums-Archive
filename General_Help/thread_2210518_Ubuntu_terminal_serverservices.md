---
title: "Ubuntu terminal server/services"
date: 2014-03-11
forum: General Help
---

### Post by Bauro on 2014-03-11
Hello

I am getting tired of Windows Server 2012 Terminal Services, and was wondering if something similar would be possible with a Ubuntu-Server.
The only required software for the terminal server is "Internet Explorer", so I was thinking of a setup consisting of:
- Ubuntu Server with GUI.
- Create a user for each employee who needs to logon (maybe you could join a windows-domain and create per-user desktop from AD-credentials).
- Use xrdp to connect to Ubuntu-desktop from a Windows 7 x64 client.
- Use Wine to emulate Internet Explorer 10 (+ Java).

Do you think this would be possible?

Regards,
Soren

---

### Post by ian-weisser on 2014-03-11
Nothing you list is unimplemented, as far as I can tell.
You seem to overestimate the difference between Ubuntu Server and Ubuntu Desktop. Desktop is a perfectly fine server, too.
You seem to want to use Windows services (AD, xrdp, etc) exclusively. Why bother with Ubuntu at all if you simply want a Windows server?
I don't really see the point of emulating IE, but feel free to do so.

Do be aware that Ubuntu is not trying to be a free clone of Windows. Design, operation and admin is not similar.

---

### Post by Bauro on 2014-03-12
Hello again

I dont see anything wrong with intergrating the two OS' - this does'nt have to be a black/white thing.
Since this server is going to be implemented in a Windows Environment (with about 500+/- users) I think it would be easier for our users to only have to relate to one set of credentials (hence the AD-intergration).

We have a critical Java-webapp which requires Java 6.x, but since we also use critical services such as net-access to our bank (which requires the newest Java), I was thinking of creating this terminal server to only have Java 6.x + IE.
I cant seem to find my way around creating a Windows Server 2012 standalone terminal server and was thinking of this Ubuntu-solution instead (which would also be more resource efficient).

I tried installing a Ubuntu Desktop with Wine, but had problems installing IE10 - do anyone have experience with this?

---

### Post by matt_fussell2 on 2014-04-25
> **Bauro said:**
> Hello again

I dont see anything wrong with intergrating the two OS' - this does'nt have to be a black/white thing.
Since this server is going to be implemented in a Windows Environment (with about 500+/- users) I think it would be easier for our users to only have to relate to one set of credentials (hence the AD-intergration).

We have a critical Java-webapp which requires Java 6.x, but since we also use critical services such as net-access to our bank (which requires the newest Java), I was thinking of creating this terminal server to only have Java 6.x + IE.
I cant seem to find my way around creating a Windows Server 2012 standalone terminal server and was thinking of this Ubuntu-solution instead (which would also be more resource efficient).

I tried installing a Ubuntu Desktop with Wine, but had problems installing IE10 - do anyone have experience with this?

I agree - there's nothing wrong with integrating Ubuntu and Windows server; unfortunately, the AD implementation in Linux hasn't caught up to Server 2012 quite yet. It is possible to join the AD domain and tie your logins and services on the Ubuntu server to the AD domain, but it takes a great deal of manipulation to make sure your policies get pushed properly. If you're looking for a solution to cut your implementation time, take a look at the following:

PowerBroker: [http://www.beyondtrust.com/Products/PowerBrokerIdentityServicesADBridge/](http://www.beyondtrust.com/Products/PowerBrokerIdentityServicesADBridge/)
Centrify: [http://www.centrify.com/resources/centrify-suite-resources.asp](http://www.centrify.com/resources/centrify-suite-resources.asp) 

As far as running IE 10 in Wine, I haven't had a reason to give that a go at this point.

---

### Post by matt_fussell2 on 2014-04-25
I forgot to subscribe to the thread - fixing that now...

---

