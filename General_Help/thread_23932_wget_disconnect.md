---
title: "wget disconnect"
date: 2005-04-04
forum: General Help
---

### Post by garfield on 2005-04-04
Hi,
At the beginning sorry for my bad english :(

I have problem with wget. When I try to download large file from http by my proxy ISP, I usually get disconnect after 5-10min. I dont know why because on windows I can download whole file without disconnect.
I'am using wget with parameters
```
wget -c -T 99999999 -t 9999999999 http://url_adres
``` 
-T should be a time of time out, but it didn't work.
When wget disconnect I see: 'Connection closed at byte xxxx' and he want try to connect once, after can't connect I see: Connection rejected.

I hope that someone know what I mean :)

sorry for bad english :(
bye.

---

### Post by Jad on 2005-04-08
**can't connect I see: Connection rejected.**
connection rejected means the server you are downloading from rejecting connecting from your side. 
try to contact them.

---

