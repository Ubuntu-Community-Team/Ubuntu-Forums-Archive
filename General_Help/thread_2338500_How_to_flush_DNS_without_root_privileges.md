---
title: "How to flush DNS without root privileges"
date: 2016-09-28
forum: General Help
---

### Post by ineuw on 2016-09-28
Is it possible to flush the DNS without root privileges? Would like users of a community desktop to do so occasionally. Currently I am using sudo /etc/init.d/nscd but I am not always there.
OR would it be possible to run this on boot without user interference?

---

### Post by TheFu on 2016-09-29
You can setup sudo to allow specific commands to be run by specific users with specific options.  
I'm fairly certain that DNS caches are flushed at shutdown, but please check that.

I've never had DNS issues which required flushing that weren't fixed at the DNS server.

---

### Post by SeijiSensei on 2016-09-29
If you create a symbolic link to nscd in /etc/cron.hourly, it will be run every hour.

---

### Post by ineuw on 2016-09-29
Thanks for the clarification. It was just an idea, part of an overall upgrade. So far I had no problems, I was just concerned that a community desktop I look after, may require clearing the DNS cache when I am not around, and I am the only root user. The desktop is on for 16 hours and a lot of people use it to surf the web.

---

### Post by TheFu on 2016-09-29
> **ineuw said:**
> Thanks for the clarification. It was just an idea, part of an overall upgrade. So far I had no problems, I was just concerned that a community desktop I look after, may require clearing the DNS cache when I am not around, and I am the only root user. The desktop is on for 16 hours and a lot of people use it to surf the web.


BTW, if you want to automate it - I'd do what SeijiSensei says - perhaps every 4 hrs - just call the script every hour, but ignore it of not mod(4) on the current hour doesn't return 0.

Why would having lots of uses matter at all?  I've been on systems with thousands of concurrent users and never had to flush the DNS.  If DNS is a problem, fix that.

---

### Post by SeijiSensei on 2016-09-29
I agree.  I've only ever had to flush the DNS cache on Windows, and only then because I made changes to the domain's DNS records that Windows had cached.  I've never had the same problem with Linux.

---

### Post by ineuw on 2016-09-29
Thanks to you all for the help and advice. Realize by now that I was overzealous and it's not necessary to waste time on it. Will mark this as solved.

---

