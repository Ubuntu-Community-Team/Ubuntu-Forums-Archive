---
title: "How do I allow remote whois requests?"
date: 2008-07-08
forum: General Help
---

### Post by dshuck on 2008-07-08
I am working on developing a simple whois web interface and have a question I am hoping someone could help out on.  Currently in testing, I am doing a java socket connection to whois.geektools.com on port 43 and passing my queries to it.  Obviously for production I don't want to leech off of someone else's server.  How can I accomplish the same type of setup on my Ubuntu box to allow clients to do queries against a port like that?  Thanks!

---

### Post by brian_p on 2008-07-08
> **dshuck said:**
> How can I accomplish the same type of setup on my Ubuntu box to allow clients to do queries against a port like that?  Thanks!

gwhois. Any use?

---

### Post by dshuck on 2008-07-09
Sweet!  Now I need to figure out how to config it. I bounced a few off of it 1 second apart and it seems to have blocked further incoming connections.  I have a suspicion that must be a security setting of some sort to keep from getting flooded.

---

### Post by danwood76 on 2008-07-09
You can use PHP or perl to create a simple script that will do a whois, I'm assuming that java is similar.

What you need to do is create (or find) a list of the whois servers instead of using the whois.geektools.com, and link this list to your script.
Each domain has its own whois server, like .co.uk is nominet and the whois server is whois.nic.uk

---

### Post by dshuck on 2008-07-09
Thanks danwood76, I actually have the code in place and working via web interface using ColdFusion/Java.  The only problem I am having is that I don't want to rely on an external whois server.  I am successfully using my code against various servers, but when I make too many requests in succession, I begin receiving: java.net.SocketException: Connection reset 

I set up gwhois based on brian_p's suggestion.  As I was running it in a loop querying random strings 1 second apart as a test, it successfully returned the first to results, but from then on gave me the Connection reset message.  I am assuming there is some type of flood protection built in, but I haven't yet found how to config that if so.  There is a dpkg-reconfigure for gwhois, but it doesn't deal with that.

---

### Post by danwood76 on 2008-07-09
You will have to rely on an external server otherwise how will your whois queries be correct?

I dont think you can flood the official whois servers with 1/ second, I'm sure plenty of sites do it far more than that.
If you are using a third party whois server you may have issues with flooding though.

Try doing repeated whois requests to an official server like the nominet one I just posted and see, maybe I am wrong in my assumptions.

It could be that your not closing the TCP socket properly or something and its causing issues on your end.

---

