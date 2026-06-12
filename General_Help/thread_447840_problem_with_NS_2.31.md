---
title: "problem with NS 2.31"
date: 2007-05-18
forum: General Help
---

### Post by DEMM on 2007-05-18
hi, i followed the NS 2.31 installing page:

[http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04](http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04)

but on the step that i type 'ns' on console instead of appearing a %, this happens :

:~$ ns
Usage:      host [-v] [-a] [-t querytype] [options]  name  [server]
Listing:    host [-v] [-a] [-t querytype] [options]  -l zone  [server]
Hostcount:  host [-v] [options] -H [-D] [-E] [-G] zone
Check soa:  host [-v] [options] -C zone
Addrcheck:  host [-v] [options] -A host
Listing options: [-L level] [-S] [-A] [-p] [-P prefserver] [-N skipzone]
Common options:  [-d] [-f|-F file] [-I chars] [-i|-n] [-q] [-Q] [-T] [-Z]
Other options:   [-c class] [-e] [-m] [-o] [-r] [-R] [-s secs] [-u] [-w]
Special options: [-O srcaddr] [-j minport] [-J maxport]
Extended usage:  [-x [name ...]] [ -X server [name ...]]
:~$ 

can you tell me what is the problem here ?

or can you tell me how to uninstall ns, to follow the these steps again from the begining ?

thanks...

---

### Post by DEMM on 2007-05-20
:sad:

---

### Post by squared on 2007-05-22
I have the same problem with my installation.  I'm reinstalling UBUNTU and ns-2 again to see if it works on a clean install.  I think it may be due to some of the additional applications that are installed when you install ns-2.  If you notice, you get this same response when you type 'host', and man ns will give the same response as man host, so there's an assignment being made somewhere.  I thought it was an alias, but that's not it.  I reinstalled ubuntu on my machine, and when I type ns now, I get the following:

  The program 'ns' is currently not installed.  You can install it by typing:
  sudo apt-get install host
  Make sure you have the 'universe' component enabled
  bash: ns: command not found

  As you can see, the operating system is looking for an application called 'host', hence the issue with why ns doesn't work.  That's about all I know about it.

  Anyone else have any ideas?

---

### Post by squared on 2007-05-22
Demm,

     See the response to my other post titled  "Help third post no replys"

---

### Post by DEMM on 2007-05-23
> **squared said:**
> I have the same problem with my installation.  I'm reinstalling UBUNTU and ns-2 again to see if it works on a clean install.  I think it may be due to some of the additional applications that are installed when you install ns-2.  If you notice, you get this same response when you type 'host', and man ns will give the same response as man host, so there's an assignment being made somewhere.  I thought it was an alias, but that's not it.  I reinstalled ubuntu on my machine, and when I type ns now, I get the following:

  The program 'ns' is currently not installed.  You can install it by typing:
  sudo apt-get install host
  Make sure you have the 'universe' component enabled
  bash: ns: command not found

  As you can see, the operating system is looking for an application called 'host', hence the issue with why ns doesn't work.  That's about all I know about it.

  Anyone else have any ideas?

have you already fixed it ?

---

### Post by squared on 2007-05-23
Yes.  I did a reinstall of ubuntu and then followed the directions on the wikki page:

  [http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04](http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04)

  I'm the second author on there, it steps through how I got it to work.  Somehow ns was dynamically linked to host.  I got some replies to my post, but none that really told me why in detail.

  I'm planning on using it for my dissertation if I can get it running.  There's a visualization package called iNSpect developed by the Colorado institute of mines.  It looks better than nam.

---

