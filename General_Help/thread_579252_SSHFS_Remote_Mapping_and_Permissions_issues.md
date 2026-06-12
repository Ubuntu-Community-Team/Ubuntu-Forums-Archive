---
title: "SSHFS Remote Mapping and Permissions issues"
date: 2007-10-18
forum: General Help
---

### Post by k_smolka on 2007-10-18
Hi All,

I am currently working on some scripts to allow me to automatically deploy some applications to a server over a network. The scripts and tools I am using only allow local deployment so I am trying to get around the problem by using sshfs to map the remote machine to my local box.

I have been using sshfs to map the remote server locally which works perfectly, only problem I have is a permissions issue.

The scripts I am using require root privileges, but as I only have sudo -s access on the remote box I am unable to log in as root directly.

Is there anyway I can ssh into a remote box as a sudo -s user?

Is there a way I could fudge the permission on the server so my users has root privileges without having to issue any commands?

Any help would be most appreciated

Regards 

Karl

---

### Post by DagMan on 2007-10-18
what you can do is use just normal ssh with x forwarding and then open up two nautilus windows on your client machine, like this.

```
ssh user@server -X
```
then you're in your server and
```
sudo -s
nautilus . &
nautilus . &
```

My ubuntu server is set up default to allow X forwarding.  If it's a differant distro then you might have to enable this in a config file then restart the ssh deamon.

---

