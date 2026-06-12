---
title: "add-apt-repository always fails with ssl error - 12.04"
date: 2013-02-07
forum: General Help
---

### Post by anewbie on 2013-02-07
I have what was a clean desktop install of ubuntu 12.04. No matter what repository I try to add add-apt-repository always fails with ssl error - example:
add-apt-repository ppa:webupd8team/java
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 84, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (60, 'server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none')
---
ls -al /etc/ssl/certs/ca-certificates.crt 
-rw-r--r-- 1 root root 100356 Jan 24 16:41 /etc/ssl/certs/ca-certificates.crt
--
I have tried to reinstall/reconfiger ca-certificates but that does not seem to be the issue so I am lost :(
---

 dpkg-reconfigure ca-certificates
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
done.
done.

Any suggestions ?

---

### Post by anewbie on 2013-02-07
Is there an easy way to trace the command to see where it is trying to get the cert or is there a configuration file that might be pointing to the wrong certs ?

---

### Post by anewbie on 2013-02-08
Ok this is really annoying:
Here is what I dug out since then (still can't fix this):
--
curl  [https://launchpad.net](https://launchpad.net)
curl: (60) SSL certificate problem, verify that the CA cert is OK. Details:
error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
More details here: [http://curl.haxx.se/docs/sslcerts.html](http://curl.haxx.se/docs/sslcerts.html)

curl performs SSL certificate verification by default, using a "bundle"
 of Certificate Authority (CA) public keys (CA certs). If the default
 bundle file isn't adequate, you can specify an alternate file
 using the --cacert option.
If this HTTPS server uses a certificate signed by a CA represented in
 the bundle, the certificate verification probably failed due to a
 problem with the certificate (it might be expired, or the name might
 not match the domain name in the URL).
If you'd like to turn off curl's verification of the certificate, use
 the -k (or --insecure) option.
---
But the browser (firefox) works fine. I can look at the chain in the browser which includes:
Go_Daddy_Class_2_CA.pem
and
Go_Daddy_Root_Certificate_Authority_-_G2.pem
-
but both of these are found in:
ca-certificates.crt
-
So what I cannot figure out is why curl fails.

---

### Post by anewbie on 2013-02-10
Ok I found a fix for this problem and am posting it in case others have the same issue:

Note that 
apt-get --reinstall install ca-certificates
and
dpkg-reconfigure ca-certificates
by themselves did not fix the issue.

However:
rm -rf /usr/share/ca-certificates
followed by 
apt-get --reinstall install ca-certificates

does resolve the issue.
Since I blew away /usr/share/ca-certificates I cannot go back and figure out why reinstall did not resolve the issue but i have to guess maybe there was an old certificate that was causing an issue (not sure since /etc/ssl/certs/ca-certificates.crt was 1/2 the size it was prior to remove this directory and then reinstalling)

---

