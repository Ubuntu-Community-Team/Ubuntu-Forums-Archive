---
title: "Listen and print to terminal what ever comes in on port 80, how?"
date: 2019-01-18
forum: General Help
---

### Post by adrian-h on 2019-01-18
I have a simple internal server running running apache2 I am trying to debug, and print out on the terminal screen anything that comes in on port 80 as a string of characters.
I thought I could use 

sudo  nc -l 80

But it reports port 80 is already in use and this will be apache2.

If i try to use another free port, say 8080 and send the url to 192.168.1.100:8080 as there is no server there the connection does not get made.

In logs all I see is a HTTP request and 404 as there is not page for what I am typing.

I am trying this to debug some script that I can not get correct, but think I have got the wrong understanding of netcat.

Can someone point me in the correct direction please?

I should have included ubuntu 16.04 server install

Adrian

---

### Post by The Cog on 2019-01-18
sudo tcpdump -A tcp port 80

---

### Post by adrian-h on 2019-01-18
Thank you, there is a load if dots and bits of messages and some understandable stuff but I will have a look at the man pages and have a read.

I appreciate your quick answer.

Adrian

---

### Post by The Cog on 2019-01-18
You can use -X instead of -A for a dump in both hex and ascii. It's better for non-text stuff but the text is harder to read.

---

