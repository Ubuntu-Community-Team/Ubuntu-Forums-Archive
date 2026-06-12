---
title: "Setting up apache - server taking too long to respond"
date: 2007-11-17
forum: General Help
---

### Post by jarmenia on 2007-11-17
Hi all.  I am very new to Linux but I've be progressing nicely in my learning.  I am now trying to set up a web server using Apache with dynamic DNS being supplied by dyndns.com.

When I try and view my website from my local LAN, the address resolves (jarmenia.homelinux.com) and the page appears almost imediately.  However if I try and view it from a computer not on my local LAN, I get the message "The server at jarmenia.homelinux.com is taking too long to respond".  Port 80 is open on my router, and I know its not a DNS issue because the same thing happens if I use the IP address instead.  I can connect via SSH and SFTP with no problems from inside or outside my LAN.  

The only other two threads I've found with an issue like this was that one didn't have port 80 open (I've checked this multiple times) and the other didn't have an answer posted.

Thanks for any help.

John

---

### Post by wooster on 2007-11-17
It could be possible that possible that your ISP blocks port 80. I wonder if you use a different port like 8080 and see if it works. Of course you'll have to access your site at jarmenia.homelinux.com:8080 after you set it up the ports to be 8080 in your apache configuration.

---

### Post by jarmenia on 2007-11-17
That thought crossed my mind.  I'll give that a try.  Thanks.

John

---

### Post by tehet on 2007-11-17
nmap can only find an open ssh port and says the rest is filtered.

---

### Post by jarmenia on 2007-11-17
Looks like my ISP must be blocking port 80.  Swithing to 8080 seems to work fine.  


Thanks for the help guys.

John

---

