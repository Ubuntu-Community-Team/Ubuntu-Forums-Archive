---
title: "Suggestions: lightweight distros with native SMBv1?"
date: 2021-05-15
forum: General Help
---

### Post by username2758 on 2021-05-15
Hey,

I have kind of an old PC and been thinking about installing a lightweight Linux distribution with native SMBv1 protocol.
 
I know Ubuntu releases prior to version 18.xx all came with the SMBv1 protocol, so version 16.04.7 (Xenial) works fine as a simple file-server with the old machine.

So my question is, if I install any other Linux distribution based on Debian released around that year (2015~2016) they all have the same SMBv1 protocol too like Ubuntu 16.04? How about support and updates?

Thanks in advance!

---

### Post by ActionParsnip on 2021-05-15
Smb ver 1 was from around the Windows 2000 years. Why do you want specifically version 1 please? What are you trying to achieve?

---

### Post by username2758 on 2021-05-15
It's because I can't get SMBv2 to work properly on my simple home network, I am not an expert so.

I tried adding the "***server min protocol = NT1***", "***client lanman auth = yes***" and "***ntlm auth = yes***" to smb.conf and while it partially solves the problem, some clients are not able to connect. 

I don't know what else to try, and as a last resource I am thinking about installing two different Linux distros on the same old machine: one main distro for general use (SMBv2) and another distro for file-server purposes where devices fail to connect (SMBv1).

I am open to ideas and suggestions though.

---

### Post by HermanAB on 2021-05-15
If you are only using Linux machines, then rather use NFS.  It is much simpler than SMB. (Windows also has NFS drivers for free download from MS).

---

### Post by mikewhatever on 2021-05-16
There is Ubuntu 14.04 or older. They are obsolete and unsupported, same as SMBv1, but if that is what you want to use, best of luck.

---

### Post by username2758 on 2021-05-16
> **HermanAB said:**
> If you are only using Linux machines, then rather use NFS.  It is much simpler than SMB. (Windows also has NFS drivers for free download from MS).
I have never used NFS before, is it superior to Samba?

The clients or devices I have at home include smartphones (Android), smart tv's (Android), media players such as WDTV Live Streaming etc, and other computers using Linux.

Is it still a good idea to switch over to NFS? Like can I set up SMBv2 and NFS together on the same operating system?

Also as an alternative, would it be possible to set up SMBv1 via a virtual machine on top of the SMBv2? Like having Ubuntu 20.04 running SMBv2 and Ubuntu 16.04 running SMBv1 as a virtual machine?

---

### Post by Morbius1 on 2021-05-16
SMB1 is not removed from the version of samba in Ubuntu20. It is disabled.

You can enable it with what you already did: [highlight]server min protocol = NT1[/highlight]

The other thing that has changed over time is the security mode - which you already accounted for: [highlight]ntlm auth = Yes[/highlight]

That translates into [highlight]ntlm auth = ntlmv1-permitted[/highlight] in Samba which does not preclude going beyond it to more modern standards.

> some clients are not able to connect. 
What exactly does that mean?

You might want to post the output of the following so folks can see how you are set up:
```
testparm -s
```
And if you created shares in your file manager the output of this one:
```
net usershare info --long
```

And sure, you can run Ubuntu 16.04 in a VBox client on top of Ubuntu 20.

---

### Post by Morbius1 on 2021-05-16
Packing up for the day but I thought I'd install and test things out to see what's what.

I installed x-plore on android.

Then I went to a Ubuntu20 server ( vubsrv2004 ) adding the same 2 lines you did - just to see if it interfered with >= SMB2 operation:
> server min protocol = NT1
ntlm auth = Yes

X-Plore found the server and all of it's shares fast enough but what it cannot do is access any share that requires a user name and password from the client. It can do guest shares fine but it doesn't know how to prompt the user for credentials.

 But you can can do an Add Server:
[ATTACH=CONFIG]288485[/ATTACH]

Then I can see the "added" server and the saved credentials allow me access and I was allowed to add a test.txt file:
[ATTACH=CONFIG]288484[/ATTACH]

---

### Post by username2758 on 2021-05-17
> **Morbius1 said:**
> Packing up for the day but I thought I'd install and test things out to see what's what.

I installed x-plore on android.

Then I went to a Ubuntu20 server ( vubsrv2004 ) adding the same 2 lines you did - just to see if it interfered with >= SMB2 operation:


X-Plore found the server and all of it's shares fast enough but what it cannot do is access any share that requires a user name and password from the client. It can do guest shares fine but it doesn't know how to prompt the user for credentials.

 But you can can do an Add Server:
[ATTACH=CONFIG]288485[/ATTACH]

Then I can see the "added" server and the saved credentials allow me access and I was allowed to add a test.txt file:
[ATTACH=CONFIG]288484[/ATTACH]

Hey there! Thanks, adding the server credentials in X-Plore app solved the problem!

Exactly! It's been kind of a strange experience with SMBv2 as some shares are accessible from the client while others are not, plus a myriad of other little issues like duplicate server name etc. You said some shares aren't accessible because it doesn't know how to prompt the user for credentials. But why is that exactly? Does it have anything to do with file permissions?

I am also trying to set up DLNA which looks to be a much simpler way to share media but unfortunately WDTV Live Streaming doesn't recognize the shares via DLNA. :(

---

### Post by Morbius1 on 2021-05-18
> **username2758 said:**
> Hey there! Thanks, adding the server credentials in X-Plore app solved the problem!

Exactly! It's been kind of a strange experience with SMBv2 as some shares are accessible from the client while others are not, plus a myriad of other little issues like duplicate server name etc. You said some shares aren't accessible because it doesn't know how to prompt the user for credentials. But why is that exactly? Does it have anything to do with file permissions?:(

When I said this:
>  ... but it doesn't know how to prompt the user for credentials
I meant X-Plore on the android end not on the samba server end. The server is sending a request for credentials to the android client but that request is never presented to the android user. Have the same issue with other file managers on android so maybe it's an android thing. Not familiar with the internal plumbing on android so I don't know.

---

