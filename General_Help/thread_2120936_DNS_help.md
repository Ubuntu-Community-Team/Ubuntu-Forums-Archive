---
title: "DNS help"
date: 2013-02-27
forum: General Help
---

### Post by opentoe on 2013-02-27
I'm running a VPS that has Ubuntu 12.04 on it. All command line here. I want to setup DNS. I have a domain pointing to the correct  DNS servers that I made to the same IP address of the VPS. Where do I setup the DNS fields/zones on here? Do I need to install BIND or anything? Right now I do have WEBMIN installed, but that hasn't help me much really. I want to be able to point my domain to my VPS. That's about it, pretty simple huh?

Also, I know if you have WHM/control panel installed you can multiple DNS zones sharing one IP address. Is there a way to admin this via command line? In case I want to setup multiple domains on this one VPS. Maybe someone can point me in the right direction. Thanks.

---

### Post by ali abry on 2013-02-28
if you want to setup your domain on your server you need bind.
and for setup zons check here :
[https://help.ubuntu.com/12.04/serverguide/dns.html](https://help.ubuntu.com/12.04/serverguide/dns.html)

---

### Post by derklempner on 2013-03-01
> **opentoe said:**
> I'm running a VPS that has Ubuntu 12.04 on it. All command line here. I want to setup DNS. I have a domain pointing to the correct  DNS servers that I made to the same IP address of the VPS. Where do I setup the DNS fields/zones on here? Do I need to install BIND or anything? Right now I do have WEBMIN installed, but that hasn't help me much really. I want to be able to point my domain to my VPS. That's about it, pretty simple huh?Just so we're on the same page here, am I correct in assuming that you just want to know how to direct a domain name/URL to your server (instead of just your public IP address), and **NOT** set up your machine as a DNS server?

There is a huge difference between the two things.  BIND is used for DNS queries, such as domain name resolving and reverse lookups; it is the cornerstone program that powers a DNS server using zone files.  If you're just looking for a way to direct your domain name to your server, then you're talking about configuring your registrar's DNS info to make sure your domain name is pointing to the correct IP address.

> **opentoe said:**
> Also, I know if you have WHM/control panel installed you can multiple DNS zones sharing one IP address. Is there a way to admin this via command line? In case I want to setup multiple domains on this one VPS. Maybe someone can point me in the right direction. Thanks.This is where usage of a DNS server comes into play.  If you are using multiple hostnames or domain names that all point to the same server, you shouldn't need BIND at all.  If you have multiple machines with multiple private IP addresses, and incoming queries are going to the same services (i.e., HTTP, FTP, SSH, etc.) on different machines, then that is when you would need BIND.

Running multiple web sites on the same server doesn't require BIND because all HTTP servers have configuration files that sort incoming queries to the correct directories in the file system.  As an example, Apache uses the **httpd.conf** file to figure out which directories are used for different domains; these configurations are known as *Virtual Servers* in the **httpd.conf** file.

---

