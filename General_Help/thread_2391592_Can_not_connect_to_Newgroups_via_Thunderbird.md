---
title: "Can not connect to Newgroups via Thunderbird"
date: 2018-05-11
forum: General Help
---

### Post by ordak on 2018-05-11
Hi,

Since yesterday I can not connect to any Newsgroups via Thunderbird. I use [https://www.eternal-september.org/](https://www.eternal-september.org/) to connect to NGs. 

Ubuntu 16.04

---

### Post by oldos2er on 2018-05-11
Did you have a question?

---

### Post by walts48 on 2018-05-11
What changed in your Thunderbird yesterday? What version of Thunderbird?

If nothing, it is probably the news server, not Thunderbird. The server looks up today.

[https://www.eternal-september.org/serverstatus.php?language=en](https://www.eternal-september.org/serverstatus.php?language=en)

---

### Post by ordak on 2018-05-11
> **walts48 said:**
> What changed in your Thunderbird yesterday? What version of Thunderbird?

If nothing, it is probably the news server, not Thunderbird. The server looks up today.

[https://www.eternal-september.org/serverstatus.php?language=en](https://www.eternal-september.org/serverstatus.php?language=en)

I suspect nothing special happened for Thunderbird yesterday. I am using Thunderbird 52.7.0 (64-bit). When I try to connect to a newsgroup, in the status bar it is written:"Connected to news.eternal-september.org ..." . But after some waiting the connection is timed out.

---

### Post by SeijiSensei on 2018-05-11
A direct test with telnet gets a "connection refused:"

```
$ telnet www.eternal-september.org 119
Trying 81.169.215.164...
telnet: connect to address 81.169.215.164: Connection refused

```

119 is the port number for the NNTP service.

---

### Post by walts48 on 2018-05-12
Try```
$ telnet news.eternal-september.org 119
Trying 2a01:238:42d4:5600:d1f0:29db:ccda:edee...
Connected to reader02.eternal-september.org.
Escape character is '^]'.
200 reader02.eternal-september.org InterNetNews NNRP server INN 2.7.0 (20170923 snapshot) ready (posting ok)


```

---

### Post by SeijiSensei on 2018-05-12
Just to make things clear, the OP should be using "news.eternal-steptember.org" not "www.eternal-september.org".

---

### Post by ordak on 2018-05-13
> **SeijiSensei said:**
> Just to make things clear, the OP should be using "news.eternal-steptember.org" not "www.eternal-september.org".

Yes, I am using this suggestion. Today I was able to read a few posts, but again I could not get rest of messages.

---

### Post by walts48 on 2018-05-13
> **ordak said:**
> Yes, I am using this suggestion. Today I was able to read a few posts, but again I could not get rest of messages.

Do you get any error messages?

You can also check the Error Console for problems Tools > Developer Tools > Error Console (Ctrl+Shift+J).

---

### Post by ordak on 2018-05-14
> **walts48 said:**
> Do you get any error messages?

You can also check the Error Console for problems Tools > Developer Tools > Error Console (Ctrl+Shift+J).

After some wait, I get a timeout message.

Error console gives:
```

Could not read chrome manifest 'file:///usr/lib/thunderbird/chrome.manifest'.


```

---

### Post by walts48 on 2018-05-14
Sounds like a server or network problem to me.

The chrome.manifest file isn't related.

---

