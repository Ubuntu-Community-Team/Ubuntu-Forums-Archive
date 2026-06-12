---
title: "Problems with rtorrent"
date: 2005-09-06
forum: General Help
---

### Post by Lapse on 2005-09-06
Hello

I'm about to install rtorrent when I get this error when typing ./configure

```

checking for curl >= 7.12.0... FAILED
configure: error: curl-config was not found

``` 

Well, I have curl installed, I guess. 

```

lapse@linux:~$ curl -V

curl 7.12.3 (i386-pc-linux-gnu) libcurl/7.12.3 OpenSSL/0.9.7e zlib/1.2.2 libidn/0.5.2
Protocols: ftp gopher telnet dict ldap http file https ftps
Features: IDN IPv6 Largefile NTLM SSL libz
```

Well, what is the problem and should I do? How do I make a curl-config?
Read something about choosing config (curl -K parameter), but what config in that case? :p

Thanks.

---

### Post by arnieboy on 2005-09-06
[QUOTE=Lapse]Hello

I'm about to install rtorrent when I get this error when typing ./configure

```

checking for curl >= 7.12.0... FAILED
configure: error: curl-config was not found

``` 

Well, I have curl installed, I guess. 

```

lapse@linux:~$ curl -V

curl 7.12.3 (i386-pc-linux-gnu) libcurl/7.12.3 OpenSSL/0.9.7e zlib/1.2.2 libidn/0.5.2
Protocols: ftp gopher telnet dict ldap http file https ftps
Features: IDN IPv6 Largefile NTLM SSL libz
```

Well, what is the problem and should I do? How do I make a curl-config?
Read something about choosing config (curl -K parameter), but what config in that case? :p

Thanks.[/QUOTE]

do the following and try running configure again:
```
sudo apt-get install libcurl3-dev libwww-curl-perl python2.4-pycurl

```

---

### Post by Lapse on 2005-09-06
Thank you, it worked.

Now when I try to runt rtorrent I get 
```
rtorrent: error while loading shared libraries: libtorrent.so.4: cannot open shared object file: No such file or directory
``` 
I'm pretty sure I installed some libtorrent stuff before I began with the rtorrent.

---

### Post by born_confused on 2005-09-06
[QUOTE=Lapse]Thank you, it worked.

Now when I try to runt rtorrent I get 
```
rtorrent: error while loading shared libraries: libtorrent.so.4: cannot open shared object file: No such file or directory
``` 
I'm pretty sure I installed some libtorrent stuff before I began with the rtorrent.[/QUOTE]

Im not sure but you could try

sudo apt-get install bittorrent

---

### Post by arnieboy on 2005-09-06
[QUOTE=born_confused]Im not sure but you could try

sudo apt-get install bittorrent[/QUOTE]
nopes, that wont work. what he needs is the package "libtorrent" which somehow has been removed from the debian repos. I am not too sure why. even sourceforge is not hosting the libtorrent release files. maybe some fatal bug or something.

---

### Post by Lapse on 2005-09-06
[QUOTE=born_confused]Im not sure but you could try

sudo apt-get install bittorrent[/QUOTE]
nope, already the latest version.

Well, I found the libtorrent4_0.7.2-2_i386.deb and tried to install it.
But I got a message that said:

```
 libtorrent4 depends on libc6 (>= 2.3.5-1), but:
  Version of libc6 in the system is 2.3.2.ds1-20ubuntu14.
 libtorrent4 depends on libgcc1 (>= 1:4.0.1), but:
  Version of libgcc1 in the system is 1:4.0.0-7ubuntu6~5.04ubp1.
 libtorrent4 depends on libsigc++-2.0-0c2 (>= 2.0.2), but:
  Package libsigc++-2.0-0c2 is not installed.

```
:(

And when I try to apt-get install those, they say they're up to date.

---

### Post by arnieboy on 2005-09-06
[QUOTE=Lapse]nope, already the latest version.

Well, I found the libtorrent4_0.7.2-2_i386.deb and tried to install it.
But I got a message that said:

```
 libtorrent4 depends on libc6 (>= 2.3.5-1), but:
  Version of libc6 in the system is 2.3.2.ds1-20ubuntu14.
 libtorrent4 depends on libgcc1 (>= 1:4.0.1), but:
  Version of libgcc1 in the system is 1:4.0.0-7ubuntu6~5.04ubp1.
 libtorrent4 depends on libsigc++-2.0-0c2 (>= 2.0.2), but:
  Package libsigc++-2.0-0c2 is not installed.

```
:(

And when I try to apt-get install those, they say they're up to date.[/QUOTE]
thats because the hoary repositories are not up to date and the version that u see installed is the one that they have on the repos. forget abt rtorrent for the time being. because if u try to install all the dependencies for libtorrent (which is required for rtorrent) and u are not too experienced a linux user, there is a very high chance that u will break your system. heed my advice on this.

---

### Post by Lapse on 2005-09-06
Alright, I guess I'll stick to bittornado or something then. :(

Thanks.

---

