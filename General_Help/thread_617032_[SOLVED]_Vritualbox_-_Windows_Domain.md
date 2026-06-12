---
title: "[SOLVED] Vritualbox - Windows Domain"
date: 2007-11-18
forum: General Help
---

### Post by shanepardue on 2007-11-18
What is needed to join a virtualbox guest running XP to a windows domain? I want to switch to Virtualbox 
as my only virtualizing software because I think it runs better than the VMware free products, but it 
doesn't do bridged networking from the gui setup. I remember having it on a domain once by messing with
 the dns, but I don't want to have to change my dns stuff on every network I join.

Any help is greatly appreciated!

---

### Post by rechick on 2007-11-19
This was one of the reasons we use vmware in an AD (Domain) environment because it handles direct connection to the network. Trying to join a machine through a NAT (how Vbox works) is quite a project. If you only need access to the workgroup just change the settings in windows. If you really  need the group policies, etc., from Active Directory then your best bet is to read the Vbox instructions and set up proper bridged  networking.

---

