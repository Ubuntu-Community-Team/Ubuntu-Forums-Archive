---
title: "Migration from CentOS to ubuntu docker image"
date: 2021-10-05
forum: General Help
---

### Post by bharanitharan on 2021-10-05
We are planning to migrate from CentOS base docker image to ubuntu base docker image. We can chosen ubuntu:20.04. Have few clarifications around it.


[LIST=1]
[*]EOL is mentioned till early 2030. Is it applicable to community version users as well? OR Is it applicable only when we purchase enterprise version of ubuntu?
[*]What is the license for ubuntu base image 20.04?
[*]When docker image version for ubuntu 22.04 is planned?
[/LIST]

---

### Post by grahammechanical on 2021-10-05
I did not know that there was a Ubuntu Enterprise edition. As far as I know all Ubuntu versions are free to download, install, use and distribute. They are all published under an Open Source license. A commercial enterprise called Canonical develops and supports Ubuntu. I think that when Canonical describes Ubuntu as "enterprise" it is referring to the enterprise/business quality of the distribution and not to a special paid for version.

Canonical follows a different business model to RedHat. Canonical will provide paid for services of various kinds. You can read about at ubuntu.com.

[https://ubuntu.com/licensing](https://ubuntu.com/licensing)

A Ubuntu Long Term Support (LTS) version has five years support as standard. And it does not matter if the user is a home user or business user. Or, running one machine or many machines. Recently Canonical introduced Extended Service Maintenance (ESM). It provides an additional 5 years security support beyond the standard LTS five year support. We get the Extended Security Maintenance by signing up to Ubuntu Advantage. Which is free for up to 3 machines. Otherwise, it is a paid for service with additional benefits

[https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

[https://ubuntu.com/advantage](https://ubuntu.com/advantage)

This post on Ubuntu.com might help you.

[https://ubuntu.com/blog/migrating-to-ubuntu-lts-six-facts-for-centos-users](https://ubuntu.com/blog/migrating-to-ubuntu-lts-six-facts-for-centos-users)

As regards a Ubuntu 22.04 Docker image, then I suggest it will come at the same time or soon after Ubuntu 22.04 itself is released - 21 April 2022.

[https://ubunlog.com/en/ubuntu-22-04-lts-ya-tiene-fecha-de-lanzamiento/](https://ubunlog.com/en/ubuntu-22-04-lts-ya-tiene-fecha-de-lanzamiento/)

By the way, I am not a paid employee of Canonical and I do not receive commission for promoting Canonical services. Ubuntu forums is a user forum. We post as users and not as part of a paid support desk team.

Regards.

---

### Post by TheFu on 2021-10-05
> **bharanitharan said:**
> We are planning to migrate from CentOS base docker image to ubuntu base docker image. We can chosen ubuntu:20.04. Have few clarifications around it.


[LIST=1]
[*]EOL is mentioned till early 2030. Is it applicable to community version users as well? OR Is it applicable only when we purchase enterprise version of ubuntu?
[*]What is the license for ubuntu base image 20.04?
[*]When docker image version for ubuntu 22.04 is planned?
[/LIST]

There might be 2 people here who work for Canonical that I've seen. They don't tend to answer technical questions. Desktop LTS releases from Canonical "approved" desktops have either 3 or 5 yrs of standard support.  

ESM support is available for a few systems (I think it is 3) for free to anyone, but if you need more to be supported, then you'll either need to be a formal "Ubuntu Member" or pay for the support.  Ubuntu Server has 5 yrs of support as does the main Ubuntu Gnome3-based desktop.

Ubuntu releases are named after the year and month.  April == 04.  October == 10.  21.10 will be released in a few weeks. It is NOT an LTS release.  If you are doing this for a business, stick with 20.04 for now.  LTS releases happen in April of even years, always.  It is a good idea to wait about 6 months for the early bugs be addressed with any release.  So, when 22.04 is released in late April 2022, my company will pull the ISO to start playing with it, but we won't put it onto any planned production system until around August 2022, at the earliest.  New isn't better.

As for docker ... I think any docker image based on Ubuntu or CentOS is a mistake.  Docker containers should be extremely lite and should probably have something like alpine Docker as the basis.  It isn't like we should be putting more than just the single App we want running into any container.  That's the point of using containers and docker. They do 1 thing and only 1 thing. 

Linux containers should be treated like zombies. If any changes need to be made, shoot the container in the head and recreate it from all the updated/patched/current sources.  Containers aren't meant to be build-once solutions.  If any part of the container needs to be updated or any config needs to be changed - shoot it in the head and recreate the container, have it got through your automatic testing, and if it passes all those tests, deploy it to your 5 or 500 or 50,000 systems.

There are many best practice guides for using, building, deploying, linux containers.  If you are doing anything different that I've described, please reconsider.
At least Ubuntu's container image is lighter than CentOS, but neither are anywhere near as tight as Alpine - by a factor of at least 10x.  Lighter containers mean they run faster and can be much more dense on the same hardware.  That == money saved.

---

### Post by bharanitharan on 2021-10-06
Thanks for the response.

Got the information for EOL.

Regarding license, we are going to use only the ubuntu docker image ([https://hub.docker.com/_/ubuntu](https://hub.docker.com/_/ubuntu)). What is the license type for this?

---

### Post by bharanitharan on 2021-10-06
Could you provide the link to get the source code for ubuntu docker image?

---

### Post by bharanitharan on 2021-10-08
We are migrating from centOS docker image to Ubuntu docker image (20.04).

Wanted to understand what are the licenses applicable for Ubuntu docker image (20.04)?

there is a page for licensing - [https://ubuntu.com/licensing](https://ubuntu.com/licensing). But It doesn't specify the list of licenses used.

---

### Post by coffeecat on 2021-10-08
Threads merged. Please do not ask the same question in different threads. You can bump a thread if you don't get a reply after 12-24 hours or so.

---

### Post by bharanitharan on 2021-10-08
> **TheFu said:**
> There might be 2 people here who work for Canonical that I've seen. They don't tend to answer technical questions. Desktop LTS releases from Canonical "approved" desktops have either 3 or 5 yrs of standard support.  

ESM support is available for a few systems (I think it is 3) for free to anyone, but if you need more to be supported, then you'll either need to be a formal "Ubuntu Member" or pay for the support.  Ubuntu Server has 5 yrs of support as does the main Ubuntu Gnome3-based desktop.

Ubuntu releases are named after the year and month.  April == 04.  October == 10.  21.10 will be released in a few weeks. It is NOT an LTS release.  If you are doing this for a business, stick with 20.04 for now.  LTS releases happen in April of even years, always.  It is a good idea to wait about 6 months for the early bugs be addressed with any release.  So, when 22.04 is released in late April 2022, my company will pull the ISO to start playing with it, but we won't put it onto any planned production system until around August 2022, at the earliest.  New isn't better.

As for docker ... I think any docker image based on Ubuntu or CentOS is a mistake.  Docker containers should be extremely lite and should probably have something like alpine Docker as the basis.  It isn't like we should be putting more than just the single App we want running into any container.  That's the point of using containers and docker. They do 1 thing and only 1 thing. 

Linux containers should be treated like zombies. If any changes need to be made, shoot the container in the head and recreate it from all the updated/patched/current sources.  Containers aren't meant to be build-once solutions.  If any part of the container needs to be updated or any config needs to be changed - shoot it in the head and recreate the container, have it got through your automatic testing, and if it passes all those tests, deploy it to your 5 or 500 or 50,000 systems.

There are many best practice guides for using, building, deploying, linux containers.  If you are doing anything different that I've described, please reconsider.
At least Ubuntu's container image is lighter than CentOS, but neither are anywhere near as tight as Alpine - by a factor of at least 10x.  Lighter containers mean they run faster and can be much more dense on the same hardware.  That == money saved.


Thanks for your response. Alpine is definitely consideration. Alpine will be majorly used. But for cases where glibc is required will be using ubuntu (Alpine do not support glibc).

Could you please provide the link for the source code to build the ubuntu docker image?

---

### Post by TheFu on 2021-10-08
> **bharanitharan said:**
>  Could you please provide the link for the source code to build the ubuntu docker image?

I cannot. I don't use docker. Sorry.

---

