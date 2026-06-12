---
title: "Amazon EC2 experiment"
date: 2013-02-06
forum: General Help
---

### Post by whiteso on 2013-02-06
Hi all, 

I am performing a cloud security analysis experiment for a project I am currently working on.

I have set up a virtual server using Amazon EC2 and Ubuntu 12.04 LTS.

The plan is to remote connect to this server using different operating systems, installing openVAS as a vulnerability scanner.

Perform some information security tests and analyse the results.

At this point I am slightly unsure how to approach and perform the tests, any help or guidance on this would be extremely appreciated.

Thanks.

Thanks.

---

### Post by Habitual on 2013-02-06
How do you connect to the instance currently?

EIP assigned?
Are you, or your IP in a Security Group assigned to the instance?

IF you can nmap the ec2 instance, no big deal as you are in the SecurityGroup, or at least your IP "should" be.

Doing so from various hosts that are NOT in the Security Group would not even reach the server _unless_ specific ports are open to the world. 
[EC2 Security Concepts.]("http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html#concepts-security")

[The Art of Port Scanning]("http://nmap.org/nmap_doc.html")

subscribed with interest...

---

### Post by whiteso on 2013-02-07
At the minute I am currently EIP assigned.
I have the default security group applied

I have been connecting to the instance through linux virtual machine and mac osX using ssh.

---

### Post by whiteso on 2013-02-07
I have now installed amazon EC2 API tools.
Set up security groups allowing SSH connection.
Not sure how to set allowed incoming traffic as I use the free tier and default security group.
Installed nmap.
Installed openVAS.

Any ideas on how I can further this experiment?

Regards.

---

### Post by Habitual on 2013-02-07
Installed OpenVAS *where* exactly?

Have you seen [http://www.openvas.org/setup-and-start.html](http://www.openvas.org/setup-and-start.html) ?

---

### Post by whiteso on 2013-02-07
Installed OpenVAS for Ubuntu via OBS...
[http://www.openvas.org/install-packages.html#openvas_ubuntu_obs](http://www.openvas.org/install-packages.html#openvas_ubuntu_obs)

---

### Post by whiteso on 2013-02-07
Im basically looking to set up a small testbed cluster using these tools to identify possible security threats and maybe try to compare with different virtual machine instances to differentiate.

This is not a large scale project and is intended for the analysis of results.

I am not an expert in this area so I am very grateful of your help.

---

### Post by whiteso on 2013-02-07
OpenVAS will be installed on the ubuntu server machine image provided by amazon EC2.

---

