---
title: "'101: Network is unreachable' error when I ran sudo apt-get update on Ubuntu 16.04"
date: 2017-01-05
forum: General Help
---

### Post by ayotunde on 2017-01-05
I launched an EC2 Ubuntu 16.04 server. It is contained in a VPC which is connected to a private VPN. To SSH into the server, you have to connect to that VPN which is also on AWS before having access to the server. After setting everything up and started configuring the server I discovered that sudo apt-get update did not install any update and I got the error below:


> ubuntu@private-ip:~$ sudo apt-get update
Err:1 [http://eu-west-1.ec2.archive.ubuntu.com/ubuntu](http://eu-west-1.ec2.archive.ubuntu.com/ubuntu) xenial InRelease
Could not connect to eu-west-1.ec2.archive.ubuntu.com:80 (IP), connection timed out [IP]
Err:2 [http://eu-west-1.ec2.archive.ubuntu.com/ubuntu](http://eu-west-1.ec2.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Unable to connect to eu-west-1.ec2.archive.ubuntu.com:http: [IP]
Err:3 [http://eu-west-1.ec2.archive.ubuntu.com/ubuntu](http://eu-west-1.ec2.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Unable to connect to eu-west-1.ec2.archive.ubuntu.com:http: [IP]
Err:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Cannot initiate the connection to security.ubuntu.com:80 (). - connect (101: Network is unreachable) [IP]
Reading package lists... Done
W: Failed to fetch [http://eu-west-1.ec2.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://eu-west-1.ec2.archive.ubuntu.com/ubuntu/dists/xenial/InRelease) Could not connect to eu-west-1.ec2.archive.ubuntu.com:80 (IP), connection timed out [IP]
W: Failed to fetch [http://eu-west-1.ec2.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://eu-west-1.ec2.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease) Unable to connect to eu-west-1.ec2.archive.ubuntu.com:http: [IP]
W: Failed to fetch [http://eu-west-1.ec2.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://eu-west-1.ec2.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease) Unable to connect to eu-west-1.ec2.archive.ubuntu.com:http: [IP]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease) Cannot initiate the connection to security.ubuntu.com:80 (). - connect (101: Network is unreachable) [IP]
W: Some index files failed to download. They have been ignored, or old ones used instead.


I tried to install apache too but got a similar error. Please what could be wrong?

---

### Post by adrihomb on 2017-02-15
Hi,
I am facing the same issue. did you find a solution.
thanks

---

