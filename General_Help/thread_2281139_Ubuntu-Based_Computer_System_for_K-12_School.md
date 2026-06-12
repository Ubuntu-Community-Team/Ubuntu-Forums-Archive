---
title: "Ubuntu-Based Computer System for K-12 School"
date: 2015-06-04
forum: General Help
---

### Post by Ethen_Crowl on 2015-06-04
Hello all, I have recently been tasked with designing and managing my school's entire computer system. I am going to have every computer in the school run Ubuntu, as it is the easiest to use for complete beginners. My school is a charter school, so the students can choose to do their work on-campus, or at home. This is an extremely important feature of the system, the ability for the students to login the the school and complete work from home.

The desired features of this system would be:

[LIST]
[*]Scalability (I would like to add more computers down the road)
[*]Portability (Full access to the system/network and their network drives wherever they have internet)
[*]Ease of use (the principle has a basic knowledge of computer systems, not advanced. though, I would like to have full control of every aspect of the system)
[*]Persistence (Some students have full-access computers at home, so we would just give them, a 64GB live USB pre-configured with the system.)
[*]The ability to update software and repositories on all machines remotely
[/LIST]

Any ideas you have that would make this more user-friendly without losing functionality would be greatly appreciated. Also, any other features you might see as necessary for a system of this size, but don't see above, feel free to speak up.

---

### Post by sandyd on 2015-06-04
> **Ethen_Crowl said:**
> Hello all, I have recently been tasked with designing and managing my school's entire computer system. I am going to have every computer in the school run Ubuntu, as it is the easiest to use for complete beginners. My school is a charter school, so the students can choose to do their work on-campus, or at home. This is an extremely important feature of the system, the ability for the students to login the the school and complete work from home.

The desired features of this system would be:

[LIST]
[*]Scalability (I would like to add more computers down the road)
[*]Portability (Full access to the system/network and their network drives wherever they have internet)
[*]Ease of use (the principle has a basic knowledge of computer systems, not advanced. though, I would like to have full control of every aspect of the system)
[*]Persistence (Some students have full-access computers at home, so we would just give them, a 64GB live USB pre-configured with the system.)
[*]The ability to update software and repositories on all machines remotely
[/LIST]

Any ideas you have that would make this more user-friendly without losing functionality would be greatly appreciated. Also, any other features you might see as necessary for a system of this size, but don't see above, feel free to speak up.

1. Use OpenLDAP for auth, this should allow users to login using their credentials on any computer
2. Setup home folders as NFS/etc shares (Side note, depending on the level of students, for security reasons I highly reccomend you use this with kerberos unless you want someone to become able to snoop on NFS traffic). Use autofs to mount folders only when necessary
3. Use x2go/NX Server so that users can connect at home. With this method, users can be authed with the school network.
4. Depending on the number of computers, you may want to install something like saltstack on each computer. Now, you can execute commands on all the computers at once, and create customized configurations that you can instantly apply to any computer to add new software/etc. If your bored, you can probably set up computers as thin clients with nx/x2go sessions, but that will use up some network capacity.
5. You shouldn't need much CPU power to run OpenLDAP, you can probably just use two servers, one as the primary and one as the backup. Storage can either be on the OpenLDAP servers, or seperately mounted through NFS/etc

Now about scalability...
I highly recommend using docker with OpenLDAP via the ubuntu docker image for scalability reasons. You can install coreOS on all of the servers except the storage servers. This creates a easy to setup failover setup that you can increase capacity in easily. [Using fleetctl with CoreOS]("https://coreos.com/using-coreos/clustering/") allows you to have easy-to-setup high-avaliability services that will allow you to have failed servers or servers taken offline for maintenance while keeping required services running. See [here]("https://coreos.com/docs/cluster-management/scaling/etcd-optimal-cluster-size/") for setting up additional fault tollerance.

---

### Post by SeijiSensei on 2015-06-04
I'll just ask the impertinent question.  What happens if you leave or get run over by a truck?  Will there be anyone else there who can administer an all-Linux network?

---

### Post by Ethen_Crowl on 2015-06-04
> **SeijiSensei said:**
> I'll just ask the impertinent question.  What happens if you leave or get run over by a truck?  Will there be anyone else there who can administer an all-Linux network?
Yes, the school district has a large IT department, so at least one of them knows Linux. I am getting high-school credits and pay for this project, so, how could I refuse?

---

### Post by Ethen_Crowl on 2015-06-04
> [COLOR=#000000]1. Use OpenLDAP for auth, this should allow users to login using their credentials on any computer[/COLOR]
[COLOR=#000000]2. Setup home folders as NFS/etc shares (Side note, depending on the level of students, for security reasons I highly reccomend you use this with kerberos unless you want someone to become able to snoop on NFS traffic). Use autofs to mount folders only when necessary[/COLOR]
[COLOR=#000000]3. Use x2go/NX Server so that users can connect at home. With this method, users can be authed with the school network.[/COLOR]
[COLOR=#000000]4. Depending on the number of computers, you may want to install something like saltstack on each computer. Now, you can execute commands on all the computers at once, and create customized configurations that you can instantly apply to any computer to add new software/etc. If your bored, you can probably set up computers as thin clients with nx/x2go sessions, but that will use up some network capacity.[/COLOR]
[COLOR=#000000]5. You shouldn't need much CPU power to run OpenLDAP, you can probably just use two servers, one as the primary and one as the backup. Storage can either be on the OpenLDAP servers, or seperately mounted through NFS/etc[/COLOR]

[COLOR=#000000]Now about scalability...[/COLOR]
[COLOR=#000000]I highly recommend using docker with OpenLDAP via the ubuntu docker image for scalability reasons. You can install coreOS on all of the servers except the storage servers. This creates a easy to setup failover setup that you can increase capacity in easily.[/COLOR][Using fleetctl with CoreOS]("https://coreos.com/using-coreos/clustering/")[COLOR=#000000] allows you to have easy-to-setup high-avaliability services that will allow you to have failed servers or servers taken offline for maintenance while keeping required services running. See [/COLOR][here]("https://coreos.com/docs/cluster-management/scaling/etcd-optimal-cluster-size/")[COLOR=#000000] for setting up additional fault tollerance.[/COLOR]
What about landscape? would that be viable for a network of this type? or is it just overkill?

---

### Post by sandyd on 2015-06-04
Landscape is pricey, everything on the above list is free and just requires a bit of tinkering and posting at mailing lists.

I *think* the only thing it comes with is [Ubuntu Advantage]("http://www.ubuntu.com/cloud/plans-and-pricing"). Not sure if you could get it seperately.

---

