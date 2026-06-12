---
title: "Help connecting a mac on yosemite to ubuntu server"
date: 2016-02-02
forum: General Help
---

### Post by slimjim3k on 2016-02-02
Hello, im new to this forum and Linux in general and I need some help.

 I am in a small office with 3 people, one of whom is on a mac. I used this tutorial to set up a file server for our office. 
[http://ubuntuforums.org/showthread.php?t=1685718](http://ubuntuforums.org/showthread.php?t=1685718)
I did use a password, so when a windows machine tries to connect, the user will be prompted to input a user name and password.

After completing the instructions, I was able to easily connect 2 Windows10 laptops, but one of the laptops I need to connect is a Mac running Yosemite. I tried googling around with the search "Connecting a Mac to a Linux server" but no mater what tutorial I fallowed, I can't connect the mac to the server. The server shows shows up in the side pane of finder, but when I try to connect from there or the "Connect to Server" option, no login / credentials prompt comes up and the Mac attempts a connection. Each time I have tried this with a different tutorial, the results are the same.

I don't know the specifics of the Mac beyond the fact that it's running Yosemite. The server machine is running Ubuntu 14.04.3 on an old 32bit P4 machine. 
I will do my best to provide any other necessary information.

---

### Post by Vladlenin5000 on 2016-02-02
Hi and welcome.

For starters, your question has little to nothing to do with Ubuntu. -> Considering it works from Windows then a) the network share is correctly setup, b) it uses SMB (AKA Samba) which is pretty much a "Windows network share" for all intended purposes.

Try this [http://osxdaily.com/2013/10/30/connect-smb-nas-network-shares-os-x-mavericks/](http://osxdaily.com/2013/10/30/connect-smb-nas-network-shares-os-x-mavericks/) . It should be the same for Yosemite.

---

### Post by slimjim3k on 2016-02-02
Awesome! Thank you! I will be trying whats in that link! Will post back with results!

Ok I just tried what was in that tutorial several times. It didn't work, I tried other prefixes too.

---

