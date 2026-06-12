---
title: "Getting FTP (server) Installed and Running"
date: 2007-07-20
forum: General Help
---

### Post by trenog on 2007-07-20
Hello. The problem I am trying to solve is that my professor needs to send me large files from his server to my computer since the server doesn't have a CD burner. He told me that a solution was to set my computer up such that he can FTP upload the files to my computer.

My problem is that none of the instructions I've read have been good enough to solve my problem.

What my apparent need is for my (Ubuntu Dapper) home PC (behind a router which it connects to for Internet access) to be set up as an FTP server so that he can transfer the files over. My assumption is that he's running a Unix server so it's not like I'm asking about cross-platforming or anything.

What I need to know is the following:

How do I set up my computer for the FTP program so that I can have him transfer files to me?

How do I then tell him to gain access to my computer remotely?

Thanks

---

### Post by amac777 on 2007-07-20
There is lots of information about how to install stuff on the ubuntuguide site. Including how to install an ftp server:

FTP Server

    * How to install FTP Server for File Transfer service
    * How to configure FTP user to be "jailed" (chrooted) into their home directory
    * How to configure FTP Server to allow anonymous FTP user to read only
    * How to configure FTP Server to allow anonymous FTP user to read/write
    * How to map anonymous FTP user to folders outside /home/ftp/
    * How to change the default port number for FTP Server
    * How to ftp into remote Ubuntu machine via Windows machine
    * How to ftp into/from remote Windows machine via Ubuntu machine
    * How to configure your NAT/router/gateway/firewall for FTP server

Start here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server)

---

### Post by trenog on 2007-07-21
Well, I managed to set up a default FTP server but unfortunately it uses port 21 and my external ip for login.

Does anyone know how to get a DI-604 set up with proftpd to work such that I can use a different default port as well as different login address to protect my computer better?

Thanks

---

### Post by amac777 on 2007-07-24
What is a DI-604?

The above links also include instructions on how to change the default port.

As for using a different IP, I'm not sure of how you could do that. You probably need to address your computer with your IP address but you only need to give it to your prof so should be pretty secure. Let me know if I've misunderstood your question.

---

