---
title: "VSFTPD - Unique passive ftp issue?"
date: 2014-05-22
forum: General Help
---

### Post by dozy on 2014-05-22
Hello Everyone,

I'm just looking for an explanation from someone that understands these things better than I do.

My ftp server *is working properly* and *can be* accessed externally using passive-mode ***without ***specifying pasv_address, and I don't know why.

**_My Setup_**
**[**Internet**]** -> **[**Cable Modem**]** -> **[**Normal Home Router (with non-standard-ftp ports forwarded to non DMZ machine )**]** -> **[**Machine running vsftpd**]**

Even though I am using passive mode *without *pasv_address, I am able to connect passively from external sources (my buddy's house) without issue.

Even though the ftp client (Filezilla) shows that my vsftpd server is returning the *internal *address of my server (eg. 192.168.1.10), as the passive address to connect to, it **is **working, and connection succeeds. But this makes no sense to me because there are so many threads where people describe this very thing as being the reason they *cannot *connect (and rightfully so) - which is the problem I too face when I swap out my normal router for a machine running pfsense or ipcop. 
But somehow, when using a normal router, the external client is being told to make passive connection to 192.168.1.10 and it is working.

As I mentioned, if I swap out my normal router for a machine running pfsense or ipcop, and set up port forwarding properly (of course), external access will not work until I specify pasv_address, just like everyone else says. As soon as I use pasv_address, all is well.

Does anyone know what 'magic' may be taking place that is allowing an external client to passively-connect to my ftp server even though vsftpd is sending them the internal address?

I have ruled out the client software (filezilla) because it's settings remain constant, and I get the same results with other ftp clients, it's my hardware that's changing.

To summarize...
1. I don't need to specify pasv_address (in vsftpd) to connect to my internal server from an external source when I'm using my normal home router (+port forwarding). It works even though vsftpd is telling the client to passively connect to my internal 192.168.x.x address.
2. Without changing anything else, if i swap out my router and replace it with a machine running pfsense or ipcop, it causes passive connections to fail until I specify my external IP in pasv_address.


Anyone?

Thanks for taking the time to read.

---

