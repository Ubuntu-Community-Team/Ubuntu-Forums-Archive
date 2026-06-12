---
title: "Double welcome post with SSH"
date: 2014-09-11
forum: General Help
---

### Post by stevecarter26 on 2014-09-11
Hello,

I'm struggling with how to sort this out;

When I SSH into my newly installed 14.04.1 server I get the below;

```
Welcome to Ubuntu 14.04.1 LTS (GNU/Linux 3.13.0-35-generic x86_64)


 * Documentation:  https://help.ubuntu.com/


  System information as of Thu Sep 11 11:46:36 BST 2014


  System load:    0.0              Users logged in:     0
  Usage of /home: 0.0% of 3.58TB   IP address for p1p1: 192.168.1.3
  Memory usage:   2%               IP address for em1:  10.10.0.23
  Swap usage:     0%               IP address for p1p2: 192.168.2.1
  Processes:      121


  Graph this data and manage this system at:
    https://landscape.canonical.com/




The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.


Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.




The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.


Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.


Last login: Thu Sep 11 11:46:36 2014 from 10.10.0.20



```

The bit that bothers me is I get 2 notifications the same 1 above the other;

```
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.


Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.




The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.


Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

```

I've done some reading and I think I need to change something in motd.d but I cannot for the life of me find where it needs to be changed....

Any help here please as I hate little niggly issues like this.

Thanks

---

