---
title: "LXD Help"
date: 2017-08-26
forum: General Help
---

### Post by chaos_efphect on 2017-08-26
I would like to first say sorry if this is the wrong second but didn't know where this would best fit. 

I have LXD running on a Ubuntu Server and having some issues with users with in the container. I am able to get a container to spin up and able to access it via root. My issue is how to create new users? I tired the normal adduser username and usermod -aG sudo username. All seems to go though with no issues until i change usernames. I for some reason am unable to get any sudo/root level commands to work with the error "sudo: no tty present and no askpass program specified'. I have seen people say to make changes to the visudo file, others say known bug. I want to know what is the offical way to create a user in an LXD container? I know with LXC you could do lxc-create -t ubuntu -n <CONTAINER_NAME> -- --user <USER_NAME> --password <USER_PASSWORD>. Is there an LXD version of this command ?

---

