---
title: "Problem while adding repository"
date: 2013-08-31
forum: General Help
---

### Post by vicke4 on 2013-08-31
Hi,whenever I try to add repositories I get the following error.How to fix this error???

```
vicky@Vicky-HP-ProBook-4520s:~$ sudo add-apt-repository ppa:kazam-team/stable-series
[sudo] password for vicky: 
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 84, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (7, "couldn't connect to host")

```

---

### Post by SeijiSensei on 2013-08-31
```
couldn't connect to host
```

Says it all.  You machine cannot see the server where the PPA is located, or perhaps the PPA has been discontinued.

---

### Post by vicke4 on 2013-08-31
> **SeijiSensei said:**
> ```
couldn't connect to host
```

Says it all.  You machine cannot see the server where the PPA is located, or perhaps the PPA has been discontinued.

It occurs for all repos....
And I have the working connection.How can I fix this problem???

---

