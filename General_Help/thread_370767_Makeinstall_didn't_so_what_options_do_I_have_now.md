---
title: "Makeinstall didn't so what options do I have now?"
date: 2007-02-26
forum: General Help
---

### Post by andytof47 on 2007-02-26
Ok trying to make a .deb out of squid 2.6 stable 9 because the one in the repos has a bug - it's already documented so I want to update....

I went searching an found a thread about using make install to make .debs from the source however even though I succesfully made the .deb it had a lot of errors in the process

paths not existing etc etc


so I'm wondering if anyone has a guide on how to build this package into a deb or if anyone has the deb file already to go

either way I would really appreciate some HEEEEEELLLLLPPPPP

It's driving me nuts


PS I just tried the same setting with fedora core 6 and all went well - but I want to do it on Ubuntu it's just not an option going to another distro

I hope you'll all be kind because of this:)

---

### Post by Rui Pais on 2007-02-26
To make a deb it's easier to use something like checkinstall

see this [thread here]("http://ubuntuforums.org/showthread.php?p=2138545") for some tips.

---

### Post by andytof47 on 2007-02-26
ooooops I messed up,

I actually tried to make a deb of squid 2.6 stable9 from the method described there already....However It didn't work


Any ideas how one might go about making a deb out of it ?????

---

### Post by Rui Pais on 2007-02-26
> **andytof47 said:**
> ooooops I messed up,

I actually tried to make a deb of squid 2.6 stable9 from the method described there already....However It didn't work


Any ideas how one might go about making a deb out of it ?????

Do you mean that you used checkinstall?
(So you finished make without errors, correct?)

What was the output of: 
```
sudo checkinstall -D
```
? 
Can you post it here?


Anyway, you can always do it in the hard way (:(). [Here is an How-to]("http://doc.gwos.org/index.php/Deb_Guide").

---

### Post by andytof47 on 2007-02-28
ok here 'tis

```
rors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_FTP_FORBIDDEN': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_FTP_NOT_FOUND /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_FTP_NOT_FOUND': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_FTP_PUT_CREATED /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_FTP_PUT_CREATED': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_FTP_PUT_ERROR /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_FTP_PUT_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_FTP_PUT_MODIFIED /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_FTP_PUT_MODIFIED': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_FTP_UNAVAILABLE /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_FTP_UNAVAILABLE': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_INVALID_REQ /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_INVALID_REQ': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_INVALID_RESP /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_INVALID_RESP': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_INVALID_URL /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_INVALID_URL': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_LIFETIME_EXP /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_LIFETIME_EXP': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_NO_RELAY /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_NO_RELAY': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_ONLY_IF_CACHED_MISS /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_ONLY_IF_CACHED_MISS': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_READ_ERROR /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_READ_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_READ_TIMEOUT /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_READ_TIMEOUT': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_SHUTTING_DOWN /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_SHUTTING_DOWN': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_SOCKET_FAILURE /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_SOCKET_FAILURE': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_TOO_BIG /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_TOO_BIG': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_UNSUP_REQ /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_UNSUP_REQ': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_URN_RESOLVE /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_URN_RESOLVE': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_WRITE_ERROR /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_WRITE_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_ZERO_SIZE_OBJECT /usr/local/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Swedish/ERR_ZERO_SIZE_OBJECT': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_ACCESS_DENIED /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_ACCESS_DENIED': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_CACHE_ACCESS_DENIED /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_CACHE_ACCESS_DENIED': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_CACHE_MGR_ACCESS_DENIED /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_CACHE_MGR_ACCESS_DENIED': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_CANNOT_FORWARD /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_CANNOT_FORWARD': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_CONNECT_FAIL /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_CONNECT_FAIL': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_DNS_FAIL /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_DNS_FAIL': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FORWARDING_DENIED /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_FORWARDING_DENIED': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FTP_DISABLED /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_FTP_DISABLED': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FTP_FAILURE /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_FTP_FAILURE': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FTP_FORBIDDEN /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_FTP_FORBIDDEN': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FTP_NOT_FOUND /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_FTP_NOT_FOUND': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FTP_PUT_CREATED /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_FTP_PUT_CREATED': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FTP_PUT_ERROR /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_FTP_PUT_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FTP_PUT_MODIFIED /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_FTP_PUT_MODIFIED': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FTP_UNAVAILABLE /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_FTP_UNAVAILABLE': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_INVALID_REQ /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_INVALID_REQ': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_INVALID_RESP /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_INVALID_RESP': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_INVALID_URL /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_INVALID_URL': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_LIFETIME_EXP /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_LIFETIME_EXP': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_NO_RELAY /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_NO_RELAY': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_ONLY_IF_CACHED_MISS /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_ONLY_IF_CACHED_MISS': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_READ_ERROR /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_READ_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_READ_TIMEOUT /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_READ_TIMEOUT': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_SHUTTING_DOWN /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_SHUTTING_DOWN': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_SOCKET_FAILURE /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_SOCKET_FAILURE': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_TOO_BIG /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_TOO_BIG': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_UNSUP_REQ /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_UNSUP_REQ': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_URN_RESOLVE /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_URN_RESOLVE': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_WRITE_ERROR /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_WRITE_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_ZERO_SIZE_OBJECT /usr/local/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Traditional_Chinese/ERR_ZERO_SIZE_OBJECT': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_ACCESS_DENIED /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_ACCESS_DENIED': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_CACHE_ACCESS_DENIED /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_CACHE_ACCESS_DENIED': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_CACHE_MGR_ACCESS_DENIED /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_CACHE_MGR_ACCESS_DENIED': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_CANNOT_FORWARD /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_CANNOT_FORWARD': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_CONNECT_FAIL /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_CONNECT_FAIL': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_DNS_FAIL /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_DNS_FAIL': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FORWARDING_DENIED /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_FORWARDING_DENIED': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FTP_DISABLED /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_FTP_DISABLED': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FTP_FAILURE /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_FTP_FAILURE': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FTP_FORBIDDEN /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_FTP_FORBIDDEN': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FTP_NOT_FOUND /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_FTP_NOT_FOUND': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FTP_PUT_CREATED /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_FTP_PUT_CREATED': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FTP_PUT_ERROR /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_FTP_PUT_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FTP_PUT_MODIFIED /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_FTP_PUT_MODIFIED': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FTP_UNAVAILABLE /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_FTP_UNAVAILABLE': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_INVALID_REQ /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_INVALID_REQ': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_INVALID_RESP /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_INVALID_RESP': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_INVALID_URL /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_INVALID_URL': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_LIFETIME_EXP /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_LIFETIME_EXP': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_NO_RELAY /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_NO_RELAY': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_ONLY_IF_CACHED_MISS /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_ONLY_IF_CACHED_MISS': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_READ_ERROR /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_READ_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_READ_TIMEOUT /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_READ_TIMEOUT': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_SHUTTING_DOWN /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_SHUTTING_DOWN': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_SOCKET_FAILURE /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_SOCKET_FAILURE': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_TOO_BIG /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_TOO_BIG': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_UNSUP_REQ /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_UNSUP_REQ': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_URN_RESOLVE /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_URN_RESOLVE': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_WRITE_ERROR /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_WRITE_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_ZERO_SIZE_OBJECT /usr/local/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/local/squid/share/errors/Turkish/ERR_ZERO_SIZE_OBJECT': No such file or directory
make[2]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/errors'
make[1]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/errors'
Making install in doc
make[1]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/doc'
make[2]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/squid/man/man8" || mkdir -p -- "/usr/local/squid/man/man8"
 /usr/bin/install -c -m 644 './squid.8' '/usr/local/squid/man/man8/squid.8'
/usr/bin/install: setting permissions for `/usr/local/squid/man/man8/squid.8': No such file or directory
 /usr/bin/install -c -m 644 './cachemgr.cgi.8' '/usr/local/squid/man/man8/cachemgr.cgi.8'
/usr/bin/install: setting permissions for `/usr/local/squid/man/man8/cachemgr.cgi.8': No such file or directory
make[2]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/doc'
make[1]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/doc'
Making install in helpers
make[1]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers'
Making install in basic_auth
make[2]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/basic_auth'
make[3]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/basic_auth'
make[4]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/basic_auth'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/basic_auth'
make[3]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/basic_auth'
make[2]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/basic_auth'
Making install in ntlm_auth
make[2]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/ntlm_auth'
make[3]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/ntlm_auth'
make[4]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/ntlm_auth'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/ntlm_auth'
make[3]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/ntlm_auth'
make[2]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/ntlm_auth'
Making install in negotiate_auth
make[2]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/negotiate_auth'
make[3]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/negotiate_auth'
make[4]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/negotiate_auth'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/negotiate_auth'
make[3]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/negotiate_auth'
make[2]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/negotiate_auth'
Making install in digest_auth
make[2]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/digest_auth'
make[3]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/digest_auth'
make[4]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/digest_auth'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/digest_auth'
make[3]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/digest_auth'
make[2]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/digest_auth'
Making install in external_acl
make[2]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/external_acl'
make[3]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/external_acl'
make[4]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/external_acl'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/external_acl'
make[3]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/external_acl'
make[2]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers/external_acl'
make[2]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers'
make[3]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers'
make[2]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers'
make[1]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/helpers'
Making install in tools
make[1]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/tools'
make[2]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/tools'
make[3]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/tools'
test -z "/usr/local/squid/bin" || mkdir -p -- "/usr/local/squid/bin"
  /usr/bin/install -c 'squidclient' '/usr/local/squid/bin/squidclient'
/usr/bin/install: setting permissions for `/usr/local/squid/bin/squidclient': No such file or directory
test -z "/usr/local/squid/libexec" || mkdir -p -- "/usr/local/squid/libexec"
  /usr/bin/install -c 'cachemgr.cgi' '/usr/local/squid/libexec/cachemgr.cgi'
/usr/bin/install: setting permissions for `/usr/local/squid/libexec/cachemgr.cgi': No such file or directory
/usr/bin/install -c -m 644 ./cachemgr.conf /usr/local/squid/etc/cachemgr.conf
/usr/bin/install: setting permissions for `/usr/local/squid/etc/cachemgr.conf': No such file or directory
make[3]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/tools'
make[2]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/tools'
make[1]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9/tools'
make[1]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9'
make[2]: Entering directory `/root/Desktop/squiddeb/squid-2.6.STABLE9'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9'
make[1]: Leaving directory `/root/Desktop/squiddeb/squid-2.6.STABLE9'

======================== Installation successful ==========================

Copying documentation directory...
./
./COPYING
./COPYRIGHT
./CREDITS
./ChangeLog
./CONTRIBUTORS
./INSTALL
./README
./RELEASENOTES.html
./doc/
./doc/Makefile.am
./doc/Makefile.in
./doc/squid.8.in
./doc/cachemgr.cgi.8.in
./doc/debug-sections.txt
./doc/Makefile
./doc/squid.8
./doc/cachemgr.cgi.8

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /root/Desktop/squiddeb/squid-2.6.STABLE9/squid_2.6.STABLE9-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r squid

**********************************************************************

```

It's there but the files aren't in the same places as the squid from the repos which makes it a little dificult to work with.


Is there a way to create the deb so it will install the same as the repo version using checkinstall?

thanks for the link

---

### Post by Rui Pais on 2007-03-01
hi,
well according to the output of checkinstall you managed to create a deb and it was installed.

I don't know a thing about squid, but if you think your errors are just location problem you need then to compile for the dir you want. 

First IMPORTANT step is uninstall. sudo apt-get remove squid
(don't redo over an installed one since versions can collide.)

Then redo all from the begin but instead of plain ./configure use:
```
./configure --prefix=/usr/lib/squid
```
Thats the path of the official ubuntu squid.

Read, too, the file INSTALL on the code dir. It says to do instead of plain make:
```
make all
``` 

After that it's just:
```
sudo checkinstall -D
```

hth

---

### Post by andytof47 on 2007-03-01
Cheers Thanks for the input:)

---

### Post by andytof47 on 2007-03-02
Hey just a heads up on the Squid install

It seems to be doing the same things????

But i thought I would try running Squid however when I ran the command

```
/etc/init.d/squid start
```
I got nothing back? When I run squid on fedora core or evven squid stable 1 it tells me all is ok and that it is restarting or starting or stopping soooooo......


Any other suggestions?

```
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Swedish/ERR_NO_RELAY': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_ONLY_IF_CACHED_MISS /usr/lib/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Swedish/ERR_ONLY_IF_CACHED_MISS': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_READ_ERROR /usr/lib/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Swedish/ERR_READ_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_READ_TIMEOUT /usr/lib/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Swedish/ERR_READ_TIMEOUT': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_SHUTTING_DOWN /usr/lib/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Swedish/ERR_SHUTTING_DOWN': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_SOCKET_FAILURE /usr/lib/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Swedish/ERR_SOCKET_FAILURE': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_TOO_BIG /usr/lib/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Swedish/ERR_TOO_BIG': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_UNSUP_REQ /usr/lib/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Swedish/ERR_UNSUP_REQ': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_URN_RESOLVE /usr/lib/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Swedish/ERR_URN_RESOLVE': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_WRITE_ERROR /usr/lib/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Swedish/ERR_WRITE_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Swedish/ERR_ZERO_SIZE_OBJECT /usr/lib/squid/share/errors/Swedish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Swedish/ERR_ZERO_SIZE_OBJECT': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_ACCESS_DENIED /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_ACCESS_DENIED': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_CACHE_ACCESS_DENIED /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_CACHE_ACCESS_DENIED': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_CACHE_MGR_ACCESS_DENIED /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_CACHE_MGR_ACCESS_DENIED': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_CANNOT_FORWARD /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_CANNOT_FORWARD': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_CONNECT_FAIL /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_CONNECT_FAIL': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_DNS_FAIL /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_DNS_FAIL': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FORWARDING_DENIED /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_FORWARDING_DENIED': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FTP_DISABLED /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_FTP_DISABLED': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FTP_FAILURE /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_FTP_FAILURE': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FTP_FORBIDDEN /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_FTP_FORBIDDEN': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FTP_NOT_FOUND /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_FTP_NOT_FOUND': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FTP_PUT_CREATED /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_FTP_PUT_CREATED': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FTP_PUT_ERROR /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_FTP_PUT_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FTP_PUT_MODIFIED /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_FTP_PUT_MODIFIED': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_FTP_UNAVAILABLE /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_FTP_UNAVAILABLE': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_INVALID_REQ /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_INVALID_REQ': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_INVALID_RESP /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_INVALID_RESP': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_INVALID_URL /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_INVALID_URL': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_LIFETIME_EXP /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_LIFETIME_EXP': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_NO_RELAY /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_NO_RELAY': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_ONLY_IF_CACHED_MISS /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_ONLY_IF_CACHED_MISS': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_READ_ERROR /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_READ_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_READ_TIMEOUT /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_READ_TIMEOUT': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_SHUTTING_DOWN /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_SHUTTING_DOWN': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_SOCKET_FAILURE /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_SOCKET_FAILURE': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_TOO_BIG /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_TOO_BIG': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_UNSUP_REQ /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_UNSUP_REQ': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_URN_RESOLVE /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_URN_RESOLVE': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_WRITE_ERROR /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_WRITE_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Traditional_Chinese/ERR_ZERO_SIZE_OBJECT /usr/lib/squid/share/errors/Traditional_Chinese
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Traditional_Chinese/ERR_ZERO_SIZE_OBJECT': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_ACCESS_DENIED /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_ACCESS_DENIED': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_CACHE_ACCESS_DENIED /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_CACHE_ACCESS_DENIED': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_CACHE_MGR_ACCESS_DENIED /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_CACHE_MGR_ACCESS_DENIED': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_CANNOT_FORWARD /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_CANNOT_FORWARD': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_CONNECT_FAIL /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_CONNECT_FAIL': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_DNS_FAIL /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_DNS_FAIL': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FORWARDING_DENIED /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_FORWARDING_DENIED': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FTP_DISABLED /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_FTP_DISABLED': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FTP_FAILURE /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_FTP_FAILURE': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FTP_FORBIDDEN /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_FTP_FORBIDDEN': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FTP_NOT_FOUND /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_FTP_NOT_FOUND': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FTP_PUT_CREATED /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_FTP_PUT_CREATED': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FTP_PUT_ERROR /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_FTP_PUT_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FTP_PUT_MODIFIED /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_FTP_PUT_MODIFIED': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_FTP_UNAVAILABLE /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_FTP_UNAVAILABLE': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_INVALID_REQ /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_INVALID_REQ': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_INVALID_RESP /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_INVALID_RESP': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_INVALID_URL /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_INVALID_URL': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_LIFETIME_EXP /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_LIFETIME_EXP': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_NO_RELAY /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_NO_RELAY': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_ONLY_IF_CACHED_MISS /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_ONLY_IF_CACHED_MISS': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_READ_ERROR /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_READ_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_READ_TIMEOUT /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_READ_TIMEOUT': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_SHUTTING_DOWN /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_SHUTTING_DOWN': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_SOCKET_FAILURE /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_SOCKET_FAILURE': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_TOO_BIG /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_TOO_BIG': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_UNSUP_REQ /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_UNSUP_REQ': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_URN_RESOLVE /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_URN_RESOLVE': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_WRITE_ERROR /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_WRITE_ERROR': No such file or directory
/usr/bin/install -c -m 644 ./Turkish/ERR_ZERO_SIZE_OBJECT /usr/lib/squid/share/errors/Turkish
/usr/bin/install: setting permissions for `/usr/lib/squid/share/errors/Turkish/ERR_ZERO_SIZE_OBJECT': No such file or directory
make[2]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/errors'
make[1]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/errors'
Making install in doc
make[1]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/doc'
make[2]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/squid/man/man8" || mkdir -p -- "/usr/lib/squid/man/man8"
 /usr/bin/install -c -m 644 './squid.8' '/usr/lib/squid/man/man8/squid.8'
/usr/bin/install: setting permissions for `/usr/lib/squid/man/man8/squid.8': No such file or directory
 /usr/bin/install -c -m 644 './cachemgr.cgi.8' '/usr/lib/squid/man/man8/cachemgr.cgi.8'
/usr/bin/install: setting permissions for `/usr/lib/squid/man/man8/cachemgr.cgi.8': No such file or directory
make[2]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/doc'
make[1]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/doc'
Making install in helpers
make[1]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers'
Making install in basic_auth
make[2]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/basic_auth'
make[3]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/basic_auth'
make[4]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/basic_auth'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/basic_auth'
make[3]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/basic_auth'
make[2]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/basic_auth'
Making install in ntlm_auth
make[2]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/ntlm_auth'
make[3]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/ntlm_auth'
make[4]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/ntlm_auth'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/ntlm_auth'
make[3]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/ntlm_auth'
make[2]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/ntlm_auth'
Making install in negotiate_auth
make[2]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/negotiate_auth'
make[3]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/negotiate_auth'
make[4]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/negotiate_auth'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/negotiate_auth'
make[3]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/negotiate_auth'
make[2]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/negotiate_auth'
Making install in digest_auth
make[2]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/digest_auth'
make[3]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/digest_auth'
make[4]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/digest_auth'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/digest_auth'
make[3]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/digest_auth'
make[2]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/digest_auth'
Making install in external_acl
make[2]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/external_acl'
make[3]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/external_acl'
make[4]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/external_acl'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/external_acl'
make[3]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/external_acl'
make[2]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers/external_acl'
make[2]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers'
make[3]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers'
make[2]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers'
make[1]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/helpers'
Making install in tools
make[1]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/tools'
make[2]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/tools'
make[3]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9/tools'
test -z "/usr/lib/squid/bin" || mkdir -p -- "/usr/lib/squid/bin"
  /usr/bin/install -c 'squidclient' '/usr/lib/squid/bin/squidclient'
/usr/bin/install: setting permissions for `/usr/lib/squid/bin/squidclient': No such file or directory
test -z "/usr/lib/squid/libexec" || mkdir -p -- "/usr/lib/squid/libexec"
  /usr/bin/install -c 'cachemgr.cgi' '/usr/lib/squid/libexec/cachemgr.cgi'
/usr/bin/install: setting permissions for `/usr/lib/squid/libexec/cachemgr.cgi': No such file or directory
/usr/bin/install -c -m 644 ./cachemgr.conf /usr/lib/squid/etc/cachemgr.conf
/usr/bin/install: setting permissions for `/usr/lib/squid/etc/cachemgr.conf': No such file or directory
make[3]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/tools'
make[2]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/tools'
make[1]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9/tools'
make[1]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9'
make[2]: Entering directory `/home/andy1/Desktop/squid-2.6.STABLE9'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9'
make[1]: Leaving directory `/home/andy1/Desktop/squid-2.6.STABLE9'

======================== Installation successful ==========================

Copying documentation directory...
./
./COPYING
./COPYRIGHT
./CREDITS
./ChangeLog
./CONTRIBUTORS
./INSTALL
./README
./RELEASENOTES.html
./doc/
./doc/Makefile.am
./doc/Makefile.in
./doc/squid.8.in
./doc/cachemgr.cgi.8.in
./doc/debug-sections.txt
./doc/Makefile
./doc/squid.8
./doc/cachemgr.cgi.8

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/andy1/Desktop/squid-2.6.STABLE9/squid_2.6.STABLE9-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r squid

```

thanks in advance:confused:

---

### Post by Rui Pais on 2007-03-04
sorry that didn't work...

there are apps that didn't go well with checkinstall.

Have you tried to do a simple make install?

---

### Post by andytof47 on 2007-03-04
well I have and I get an install that isn't quite working ....

But finally A few days ago I found an updated squid package that works beautifully....

I'll still need to learn how to make debs it's just not as critical now


cheers for the help

---

### Post by Rui Pais on 2007-03-04
Hi,

glad you managed to get a working updated version (maybe post a link would help others who wish to try a newer version:))

checkinstall it's a nice script to make easy what other way is very boring and hard... if it fails one have to do it all by hand... 
Here is a nice How-TO:
[http://doc.gwos.org/index.php/Deb_Guide](http://doc.gwos.org/index.php/Deb_Guide)

Have fun.

---

### Post by andytof47 on 2007-03-05
here is the link to the howto relating to the new files

[http://www.ubuntuforums.org/showthread.php?t=370563](http://www.ubuntuforums.org/showthread.php?t=370563)

and thanks for the guide

:popcorn:

---

