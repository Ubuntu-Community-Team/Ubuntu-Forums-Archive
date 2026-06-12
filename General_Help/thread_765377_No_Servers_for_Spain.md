---
title: "No Servers for Spain??"
date: 2008-04-24
forum: General Help
---

### Post by nachomaster on 2008-04-24
I had to download Ubuntu 8.04 from a Germany server because both of Spain's disappeared... now I installed it and it wont let me update anything or install anything because it says Spain servers are down.

For example: 

"Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://es.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg) "

Any ideas on how to fix this or when will the servers be back up?

---

### Post by retrow on 2008-04-24
In terminal, type:
```
sudo gedit /etc/apt/sources.list
```
Replace 'http://es.' with 'http://nl.' (Go with replace all - this will replace Spain servers by Netherlands servers. Remember to do it along with the dots, else things might get a little messed up).

Then run:
```
sudo apt-get update
```
Once thats done, you can search and install whichever application you want.

NOTE: I am assuming that the servers in Netherlands won't go down by the time you read this.

---

