---
title: "[Issue] Updated users/Groups from Active Directory Integration with Ubuntu 18.04 LTS"
date: 2020-05-29
forum: General Help
---

### Post by tkwok on 2020-05-29
Hi All,

I set up the AD Integration for my Ubuntu 18.04 LTS workstation through a Virtual Machine using these two links: 

[https://discourse.ubuntu.com/t/service-sssd/11579](https://discourse.ubuntu.com/t/service-sssd/11579)

[https://docs.microsoft.com/en-us/azure/active-directory-domain-services/join-ubuntu-linux-vm](https://docs.microsoft.com/en-us/azure/active-directory-domain-services/join-ubuntu-linux-vm)

And it seems to work fine as I am able to log in with my administrative account I used to join the machines. I am also able to search specific users on my Windows AD server although I have ran into some difficulties which am curious if anyone knows the answer to.

1. If I create a new user on AD, it doesn't seem to automatically transfer over to my Ubuntu. I can't search that user using id as it doesn't seem to exist.

2. If I create a new group and add my user to that group, it also doesn't transfer over...

Those are the main problems I have run into while setting up AD integration with Ubuntu. Am curious if there is something I am supposed to do on Ubuntu to "update" in the new users created on AD.

Edited: Basically is there a way to make sure from either  /etc/sssd/sssd.conf or somewhere else that AD user list will  automatically be updated onto my Ubuntu 18.04 instead of having to realm  join again.

---

