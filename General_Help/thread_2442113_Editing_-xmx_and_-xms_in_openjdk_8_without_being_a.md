---
title: "Editing -xmx and -xms in openjdk 8 without being able to run Java"
date: 2020-04-29
forum: General Help
---

### Post by tylermatthew on 2020-04-29
Hi All! 

I'm running Ubuntu 16.04 in AWS to host a Unifi controller. due to god-knows-what upon the last startup java decided it would try to start with -xmx6144m and -xms6144m even though that instance has, and has only ever had 4GB of ram. So, Java can't start because not enough ram. I'm simply trying to figure out if/where these variables are stored in a configuration file or something I can edit to get it back working. I cant edit it with a java command, because java won't run. 

I'm also not entirely sure it's not unifi putting those variables there.. but I guess that's a question for a different forum. 

Any and all help greatly appreciated! 

-tylermatthew

EDIT: Also, brand new here! if this isn't in the right place, my sincere apologies! my initial exposure to Ubuntu was spinning up this controller 5 years ago, and I really just barely google my way through... but recently I decided to take the leap, and wiped a secondary work laptop to install 20.04 onto, and have been trying to get the basics under me!

EDIT 2: see reply, marked as solved

---

### Post by tylermatthew on 2020-04-29
For posterity in future google searches: the parameters regarding Java Heap size are located in the /var/lib/unifi/system.properties and can be edited there to require (in my case) Java to start while using LESS that the total amount of RAM in the system. 

Hooray!

---

