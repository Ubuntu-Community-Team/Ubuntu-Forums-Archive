---
title: "OpenVPN and Ubuntu in Amazon Web services"
date: 2017-09-11
forum: General Help
---

### Post by tc222 on 2017-09-11
Hi,
I have installed an OpenVPN Access Server on AWS and it works fine (runs on Ubuntu 16.04). 
However, I have difficulties installing CloudWatch Logs Agent  on the openVPN. I have followed all instruction but when I try to install the aws logs agent recieve the following error -message:
 
 openvpnas@openvpnas2:~$ sudo python ./awslogs-agent-setup.py --region eu-central-1
 Launching interactive setup of CloudWatch Logs agent ... 
 **ERROR: Failed to determine linux distribution. Exiting.**
 
Anyone that have an idea why it not recognizes the Ubuntu distribution and suggestion for a workaround?

Thanks in advance!
Thomas

---

