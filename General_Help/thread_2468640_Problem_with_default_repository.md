---
title: "Problem with default repository"
date: 2021-11-06
forum: General Help
---

### Post by jjoxford20072 on 2021-11-06
I had Ubuntu 20.04.2 Server installed on a separate PC so I could run a Minecraft server off of it, and it's been running fine up until today. For some reason it started throwing me "Can't authenticate user" errors. So I decided to try and uninstall/reinstall java. I couldn't reinstall java. So next I tried to do sudo apt-get update, and for the DEFAULT repository it said
E: The repository 'http://us.archive.ubuntu.com/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.

It said the same thing for updates, backports, and security. So I decided I'll just try to reinstall ubuntu, which of course had a version higher, being 20.04.3. Now in trying to make my user name and such for the new install, it fails while I'm typing, so I open up the report, scroll down a ton, and I see the same repository error in the log. Is something going on with my internet or is it on the repository end? It's pretty frustrating considering I can surf the web, watch videos, etc. on my main pc which is how I'm even able to post this. Right now I'm kind of just at a point where I have no idea what steps to take to progress with anything.

---

### Post by dragonfly41 on 2021-11-06
Google brings up this ..

[https://itsfoss.com/repository-does-not-have-release-file-error-ubuntu/](https://itsfoss.com/repository-does-not-have-release-file-error-ubuntu/)


P.S. I remember that I have a useful tool Y PPA Manager installed from repo which might help troubleshooting PPA.
And Synaptic Package Manager of course.

---

### Post by grahammechanical on 2021-11-06
Did you succeed in installing Ubuntu 20.04.3 server? If you did then the problem with Ubuntu 20.04.2 server is no longer an issue. If you cannot finish installing 20.04.3 then it is a separate problem. Can you still load Ubuntu 20.04.2 server?

The Ubuntu repositories sometimes go offline for maintenance reasons. There are mirror repositories in different places. We can wait a few hours before trying to update. Or, we could change repositories to another mirror site.

Regards

---

### Post by ajgreeny on 2021-11-06
Try removing the ***us.*** prefix to the repository line and just use [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal Release in its place.

As grahammechanical says above, perhaps the US archive is temporarily offline; it will probably come back again if it hasn't already done so, but the main archive may still be available even if the US archive is not.

---

### Post by jjoxford20072 on 2021-11-06
Not quite sure what I did, but I have successfully got 20.04.3 up, and running by disabling networking during install, and then painstakingly re-enabling it after installation. However, I am now very confused. When looking at attached devices in my routers settings it shows my server TWICE with 2 different internal IP addresses. One shows the device name as its correct name that i entered during installation, the other has the name desktop followed by numbers. When I edit the netstat and set the IP to that of the incorrect one nothing works network-wise. But when it's set to the correct one everything obviously works. I just don't know why the 2nd one is there to begin with.

---

### Post by ajgreeny on 2021-11-07
What are the numbers you see of the one that doesn't work; does it look like an IP or perhaps the UUID of the partition?
Show us what you see if possible by copying the text, not as a screenshot.

---

