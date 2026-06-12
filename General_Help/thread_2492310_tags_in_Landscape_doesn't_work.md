---
title: "tags in Landscape doesn't work"
date: 2023-11-07
forum: General Help
---

### Post by Jaxilian on 2023-11-07
Hi all
I couldn't find a category for Landscape so I hope this is ok place for now.

I have a Landscape server, just the free 10 client setup for now until some things get sorted. One thing is the tags that doesn't seem to work. I run the landscape-config command with some switches. Everything works, computer get added into Landscape and so on, but the tags don't get transferred from the /etc/landscape/client.conf to Landscape.
In the client.conf, the tags are just sitting there nicely, one space apart with no weird characters just letters. 

I tried looking of there are any bugs related to this, but I cannot find anything.

I hope someone with Landscape experience can help me here.

---

### Post by Jaxilian on 2023-11-07
solved it. I needed commas between the tags. After that it worked ok.

---

