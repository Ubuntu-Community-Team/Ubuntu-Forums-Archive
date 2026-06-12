---
title: "Can't login to NFL Network"
date: 2016-10-02
forum: General Help
---

### Post by valok2 on 2016-10-02
So I'm trying to login to NFL network to watch redzone and other games today.  When I go to the site, I'm prompted to enter my cable provider information.  I do this, hit enter, and am then redirected back to the login screen.  So essentially I'm stuck in an endless login loop cycle, can't figure out exactly why.  I'm able to watch on Windows, but I'd rather not have to reboot every time.  Any thoughts?

Edit - if it helps I'm running Ubuntu 16.04.  Same error happens in both firefox and chrome

---

### Post by Dennis N on 2016-10-02
In the United States, to login successfully to web content of cable channels you receive through your cable tv service, you need to install a package called hal-flash. This only works in Firefox. For currently-supported Ubuntu releases, it's available through a PPA:

[https://launchpad.net/~flexiondotorg/+archive/ubuntu/hal-flash](https://launchpad.net/~flexiondotorg/+archive/ubuntu/hal-flash)

---

### Post by valok2 on 2016-10-02
Thank you very much, this worked!!!

In case anyone else is having this same problem and interested in the solution.

```
sudo add-apt-repository ppa:flexiondotorg/hal-flash
sudo apt-get update
sudo apt-get install libhal1-flash
```

---

