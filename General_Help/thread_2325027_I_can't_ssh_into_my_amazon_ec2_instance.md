---
title: "I can't ssh into my amazon ec2 instance"
date: 2016-05-18
forum: General Help
---

### Post by steve258 on 2016-05-18
ssh: connect to host ec2-52-38-217-247.us-west-2.compute.amazonaws.com port 22: Connection timed out

---

### Post by Habitual on 2016-05-18
```
ssh -i /path/to/key.pem ubuntu@ec2-52-38-217-247.us-west-2.compute.amazonaws.com
```
Where key.pem is your AWS IAM key.

See also [http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html)

---

### Post by steve258 on 2016-05-18
Yes I know how to ssh with my .pem file.. Only it times out. I'm trying to make a help post on amazon forums but it won't let me post.

---

### Post by Habitual on 2016-05-18
> **steve258 said:**
> Yes I know how to ssh with my .pem file.. Only it times out. I'm trying to make a help post on amazon forums but it won't let me post.

Login to your AWS console and check the Security Group for that host.
Verify that your IP/32 is in there on port 22.

This is local to your desktop system since you can neither reach the instance nor post to amazon forums.
If you have a router, you may wish to consider rebooting it and your system.

---

### Post by steve258 on 2016-05-18
> **Habitual said:**
> Login to your AWS console and check the Security Group for that host.
Verify that your IP/32 is in there on port 22.

This is local to your desktop system since you can neither reach the instance nor post to amazon forums.
If you have a router, you may wish to consider rebooting it and your system.



Just turned off the pc for a an hour or two and now it works.. This is so weird because it keeps happening and it fixes by just turning it off for a while.

---

### Post by Habitual on 2016-05-18
It happens.

---

