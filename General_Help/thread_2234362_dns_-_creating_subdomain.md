---
title: "dns - creating subdomain"
date: 2014-07-14
forum: General Help
---

### Post by nos09 on 2014-07-14
Hi guys,

I have few cloud server to maintain. Many of them have public IPs. (soon moving some of them to VPC).

I have bought a domain say - example.com from godaddy.com. it points to my ec2 ubuntu instance.

now the scenario is I dont want to remember all the ips of all machines. I would rather like them to point like this - 

git.adweaver.com  --> digitalocen drophet (my git server).
client01.adweaver.com --> ec2 instance Amazon
client02.adweaver.com --> ec2 instance Amazon
....
....


I dont have much experiance with dns. can anybody suggest how to do it or point me where i can find solution ?! 

thank you very much.

---

### Post by dragonfly41 on 2014-07-14
If you have an Amazon account (you refer to EC2 instances) you can use Route53 to map domains.

Or you can use a service such as [www.zoneedit.com](www.zoneedit.com).

---

### Post by nos09 on 2014-07-14
Thank you for quick reply. 
I am currently using godaddy.com for dns. 
as i said i have already registered a domain name with them. 
I just dont know how to list/use subdomain.

I can use the domain to login via ssh. can i do the same for subdomains ?

---

### Post by dragonfly41 on 2014-07-14
Then try following godaddy support ...

[http://support.godaddy.com/help/article/4080/managing-a-domain-names-subdomains](http://support.godaddy.com/help/article/4080/managing-a-domain-names-subdomains)

---

### Post by nos09 on 2014-07-15
thank you. I'll mark the tread as solved.

---

