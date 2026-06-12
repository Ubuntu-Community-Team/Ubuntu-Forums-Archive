---
title: "Ubuntu Server --&gt; Web-filter w/ login."
date: 2008-05-03
forum: General Help
---

### Post by eaglestrike7339 on 2008-05-03
Hello to my fellow Ubuntu users, and congrats to the devs of Hardy Haron. 

I am looking for a free way to set up a transparent proxy server with web filter. The goal is to have all traffic of a Medium-sized Non-profit filtered. There are 2 segments: employees, and also students. No students are allowed to view outside material, and employees are not either. 

However, students have many necessary programs online, and every so often an employee needs to access an  outside site within the range of their job.
Is there a way for there to be a log-in sequence to access pages that are not directly associated with the class lessons (student) or from visiting social networking sites or online stores (both employees and student)? 

I was looking into it, and the closest that I came up with was using Ubuntu Server, Squid proxy, and Dansguardian. Is there some sort of program out there that can do what I need?

Also, what sort of requirements would this take? Would it be better to have a small cluster set up of these squid servers? I've never done this before, but it looks very interesting. 

Note: This project is not yet started, but I am looking for an alternate solution of spending 6K a year on per-pc filtering software

Thanks to all, 
eagle

---

### Post by Monicker on 2008-05-03
Why wouldn't Squid work for what you want? You can configure squid and dansguardian acls which will allow/disallow traffic to sites based on their login.

---

### Post by eaglestrike7339 on 2008-05-03
I was looking into Dansguardian, but I am a little confused. 
Do I need both squid and dansguadian? or just dansguardian? Dansguardian acts as a layer on top of the proxy, but is the proxy itself included?

---

### Post by Monicker on 2008-05-03
> **eaglestrike7339 said:**
> I was looking into Dansguardian, but I am a little confused. 
Do I need both squid and dansguadian? or just dansguardian? Dansguardian acts as a layer on top of the proxy, but is the proxy itself included?


There is some overlap in functionality, but basically dansguardian is a content filter used in conjunction with a proxy server.  Dansguardian does not include Squid, but works to filter the content which squid is retrieving on behalf of the user.

---

