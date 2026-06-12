---
title: "Update problem in Ubuntu 15.04"
date: 2015-10-11
forum: General Help
---

### Post by jerry58 on 2015-10-11
I installed Ubuntu 15.04 a few days ago and it will not update. When I run the Software Updater, it tries to download and then I get the following error message:



  Failed to download repository information. Check your internet connection.

This happens ever single time I run the updater. Any suggestions? BTW, there is nothing wrong with my internet connection.

UPDATE: I got desperate enough to do a re-install of 15.04. It didn't help. Ubuntu will not do updates.

---

### Post by howefield on 2015-10-11
Hello jerry58 and welcome to the forums, please use the paperclip icon to attach your image to your post rather than dragging into the browser window.

---

### Post by grahammechanical on 2015-10-11
I see that message every day but then I am running to development version of the next version of Ubuntu (15.10) and for most of the 26 week development period some of the repositories are not active. It does not stop me from updating the OS. I click OK and Update Manager goes away and does its stuff.

You should not be getting that message from a new install of 15.04. Have you added another software repository such as a PPA? If so, disable it in Software & Updates. Also we can run 2 commands that will identify what repositories are failing to download. This information is useful to help us identify what exactly is causing the problem. 

```
sudo apt-get update
sudo apt-get upgrade
```

In relation to this you might one day see an offer to do a partial upgrade. Resist the temptation to accept the offer. It will run a special apt-get command that will bring in upgrades and fix conflicts by removing software packages. I have know that to break the OS. These are the reasons for getting the offer of a partial upgrade

1) A previous upgrade which did not complete
2) Problems with some of the installed software
3) Unofficial softare packages not provided by Ubuntu
4) Normal changes of a pre-release version of Ubuntu

In my case item 4 is the reason whiy I get the partial upgrade offer. I always click continue and then the update is installed in the normal method.

Regards.

---

### Post by jerry58 on 2015-10-11
sudo apt-get update results were:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8c01::23 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by jerry58 on 2015-10-20
I solved the problem (by myself) with information from this page.  [http://askubuntu.com/questions/603058/failed-to-fetch-http-extras-ubuntu-com-ubuntu-dists-vivid](http://askubuntu.com/questions/603058/failed-to-fetch-http-extras-ubuntu-com-ubuntu-dists-vivid)

It seems that extras is not being continued, and canonical failed to delete the reference from the sources.list file. I merely commented out that line and it fixed the bug.

---

