---
title: "Can't ssh: port 22: Connection timed out"
date: 2016-05-17
forum: General Help
---

### Post by steve258 on 2016-05-17
This happened to me yesterday and turned off the computer and later on once I was back on worked. Today same thing... What's going on?

**ssh: connect to host ec2-23-33-112-127.us-west-2.compute.amazonaws.com port 22: Connection timed out**

---

### Post by sailingboyLLB on 2016-05-17
i'm not sure what you're trying to do exactly, but....

that name "**ec2-23-33-112-127.us-west-2.compute.amazonaws.com"**, doesn't resolve to an ip address.  basically the internet isn't sure how to turn that name into an address it can use.

there is an ip in there which is human discernible and is 23.33.112.127. a backwards lookup resolves to a23-33-112-127.deploy.static.akamaitechnologies.com

so it looks like what ever you are trying to connect to got moved from amazon to akamai???

---

### Post by steve258 on 2016-05-17
Oh that's not my real amazon ip.. thought it would be better for security purposes. 

Anyhow here's the real one: **ec2-52-38-217-247.us-west-2.compute.amazonaws.com**

---

### Post by sailingboyLLB on 2016-05-27
well.  that one resolves correctly.  i don't think there's going to be an obvious answer here.  i tried pinging and ssh and got nothing.  make sure your firewall is setup correctly.

---

