---
title: "Getting Temporary Failure in name resolution in Ubuntu 18.04.1 LTS under AWS"
date: 2018-11-12
forum: General Help
---

### Post by aruneshdutta on 2018-11-12
Hello all

I am facing issue in one of the instances in Ubuntu 18.04.1 LTS under AWS,[IMG]https://postimg.cc/CRkCy14H[/IMG][IMG]https://ibb.co/mSguHq[/IMG] I am getting error Temporary failure in name resolution while making ping request and so none of applications running on instance are able to communicate with respective domain.The system was working perfectly fine earlier and all of a sudden the issue has been observed affecting my work.Kindly guide me how to fix same ..thx[IMG]https://postimg.cc/CRkCy14H[/IMG][IMG]https://postimg.cc/CRkCy14H[/IMG]

[IMG]https://image.ibb.co/c3QbVA/Untitled.png[/IMG]

---

### Post by hartman8227 on 2018-11-15
This might be a temporary problem with the  DNS server that you are using to resolve hostnames or might be something local. If your problem hasn't fixed itself (it happens), then we need some more information to help you. Could you please post the results of the following commands:

```


ip address

ip route

cat /etc/network/interfaces

cat /etc/resolv.conf

cat /etc/nsswitch.conf 

nslookup ubuntu.com

dig ubuntuforums.org
[COLOR=#000000][FONT=&amp]
ping 8.8.8.8[/FONT][/COLOR]
```

---

### Post by aruneshdutta on 2018-11-16
Thanks

---

